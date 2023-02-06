---
title: Spring Boot Annotation
layout: post
categories: [SpringBootFramework]
tags: [SPRING BOOT]
---

### Spring Boot Annotation

@RestController
- REST(REpresentative State Transfer) 분산시스템을 위한 아키텍처 / RESTFul
- 네트워크를 경유해 외부 서버에 접속하거나 필요한 정보를 불러오기 위한 구조

@RequestMapping
- 서버의 URL과 특정 처리를 연동시키는(매핑) 구조
- value만 있는 경우, value를 생략하고 값을 지정할 수 있지만, 인수가 여러개인 경우 모두 지정 필요
- ex
-- @RequestMapping("/{num}")
   @RequestMapping(value="/", method=RequestMethod.POST)
   

@PathVariable
- 매개변수
- URL의 쿼리 스트링에 지정한 값을 추출

@Controller
- 일반 웹 페이지를 사용하는 경우 Controller 클래스 앞에 붙인다

@RequestParam
- 폼에서 전송한 값을 지정하기 위한 Annotation
- 폼에 있는 name 데이터 이용
- @RequestParam(value="check1",required=false)boolean check1
: required=false 값이 전달되지 않는 경우 null 처리 / 데이터가 없어도 처리 계속 진행됨

@Entity
- JPA를 이용하는 경우, DB의 데이터에 해당하는 부분을 Entity로 지칭

@Table
- name으로 테이블명 설정
- 생략 가능

@Id
- PK 지정 ( 엔티티 클래스 정의 시 필수 )

@GeneratedValue( strategy = GenerationType.AUTO )
- PK 자동 생성 타입

@Column
- 컬럼 명 지정
- 생략인 경우 필드명 = 컬럼명
- 인수 ( name / length / nullable )

@Repository
- SpringBoot JPA 에서 설명

@Autowired
- Application에 있는 Bean 객체와 연동하기 위한 것

@ModelAttribute
- Entity 클래스의 인스턴스를 자동으로 적용할 때 사용(new 클래스)
- 인수에 인스턴스 Name 지정

@Transactional(readOnly=false)
- 트랜잭션 기능을 위함
- 해당 애너테이션을 사용하는 메서드 내에서 실행되는 DB 처리가 일괄적으로 실행
- 데이터 일관성 문제 방지
- readOnly = 변경불가

    ```
    	@RequestMapping(value = "/", method = RequestMethod.POST)
    	@Transactional(readOnly=false)
    	public ModelAndView form(
    			@ModelAttribute("formModel") MyData mydata, 
    			ModelAndView mav) {
    		repository.saveAndFlush(mydata);
    		return new ModelAndView("redirect:/");
    	}
    ```


그 외
- redirect:XX
- forward:XX
