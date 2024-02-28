---
title: Spring Boot Swagger
layout: post
categories: [SpringBootFramework]
tags: [SPRING BOOT]
---

### Swagger

- FO와 BO의 협업에 사용되는 툴
- API 시각화 지원(명세)

  - Swagger UI 접속 설정
    ```
    # build.gradle 파일에서 spring boot 버전 확인
    plugins {
      id 'java'
      id 'org.springframework.boot' version '3.2.3'
      id 'io.spring.dependency-management' version '1.1.4'
    }
    ```
    ```
    # Swagger API Test URL
    2.x.x 버전: localhost:8080/swagger-ui.html
    3.x.x 버전: localhost:8080/swagger-ui/index.html
    ```
  - Spring 기반의 Swagger Springfox vs Springdoc
    ```
    # build.gradle 파일에서 의존성 추가
    implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.2.0'
    ```
  - SwaggerConfig 작성
    ```
    # JWT 사용 X
    import io.swagger.v3.oas.models.Components;
    import io.swagger.v3.oas.models.OpenAPI;
    import io.swagger.v3.oas.models.info.Info;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;
    
    @Configuration
    public class SwaggerConfig {
    
      @Bean
      public OpenAPI openAPI() {
        return new OpenAPI()
        .components(new Components())
        .info(apiInfo());
      }
    
      private Info apiInfo() {
         return new Info()
         .title("API Test") // API의 제목
         .description("Let's practice Swagger UI") // API에 대한 설명
         .version("1.0.0"); // API의 버전
      }
    }
    ```
    ```
    # JWT 사용 O
    @Configuration
    public class SwaggerConfig {
    
      @Bean
      public OpenAPI openAPI() {
         String jwt = "JWT";
         SecurityRequirement securityRequirement = new SecurityRequirement().addList(jwt);
         Components components = new Components().addSecuritySchemes(jwt, new SecurityScheme()
         .name(jwt).type(SecurityScheme.Type.HTTP).scheme("bearer").bearerFormat("JWT"));
    
         return new OpenAPI().components(new Components()).info(apiInfo()).addSecurityItem(securityRequirement).components(components);
      }
    
      private Info apiInfo() {
         return new Info()
         .title("API Test") // API의 제목
         .description("Let's practice Swagger UI") // API에 대한 설명
         .version("1.0.0"); // API의 버전
      }
    }
    ```
  - API Annotation
     ```
    # 태그명을 지정하지 않으면, Controller의 이름을 Kebab Case(ex: AuthController → auth-controller)로 변환하여 API를 그룹화
    # API의 도메인을 태그명으로 사용하여 그룹화
    @Tag(name = "Response Estimate", description = "Response Estimate API")
    
    # API에 대한 설명을 추가
    @Operation(summary = "업체 회원가입", description = "업체 측에서 회원가입 할 때 사용하는 API")
    
    # 응답 정보에 대한 내용
    @ApiResponse(responseCode = "1000", description = "요청에 성공하였습니다.", content = @Content(mediaType = "application/json"))
    @ApiResponses(value = {
        @ApiResponse(responseCode = "1000", description = "요청에 성공하였습니다.", content = @Content(mediaType = "application/json")),
        @ApiResponse(responseCode = "2002", description = "이미 가입된 계정입니다.", content = @Content(mediaType = "application/json")),
        @ApiResponse(responseCode = "4000", description = "데이터베이스 연결에 실패하였습니다.", content = @Content(mediaType = "application/json")),
        @ApiResponse(responseCode = "4011", description = "비밀번호 암호화에 실패하였습니다.", content = @Content(mediaType = "application/json"))})
    
    # 파라미터에 대한 정보
    @Parameters({
        @Parameter(name = "email", description = "이메일", example = "chrome123@naver.com"),
        @Parameter(name = "password", description = "6자~12자 이내", example = "abcd1234"),
        @Parameter(name = "companyName", description = "업체명", example = "코리아 시스템"),
        @Parameter(name = "companyNumber", description = "업체 번호", example = "112233"),
        @Parameter(name = "companyAddress", description = "업체 주소", example = "인천시 미추홀구 용현동")})
    
    # MultiPart File
    # @PostMapping(또는 @PatchMapping) 어노테이션 안에 consumes, produces 속성을 추가
    @PatchMapping(value = "/image", consumes = MediaType.MULTIPART_FORM_DATA_VALUE, produces = MediaType.APPLICATION_JSON_VALUE)
     ```

###### #Reference
<br>
<br>
{: .text-right }
[참고](https://velog.io/@gmlstjq123/SpringBoot-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-Swagger-UI-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)
{: .text-right }
