---
title: Spring Boot Template JPA
layout: post
categories: [SpringBootFramework]
tags: [SPRING BOOT]
---

### JPA

- 데이터베이스 관련 기능을 구현하기 위해 사용하는 것
- Java EE의 데이터 지속성( 객체 등의 데이터를 저장해 항상 사용할 수 있게 하는 것 )
- Controller -> Model|JPA -> DB
- JPA를 사용하기 위한 Library 및 Framework
- Spring Boot Starter Data JPA 라는 Library를 이용해 통합적으로 사용 가능 ( HSQLDB 제외 )

- pom.xml
   ```
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>org.hsqldb</groupId>
			<artifactId>hsqldb</artifactId>
			<scope>runtime</scope>
		</dependency>
    ```

    1) HSQLDB ( Hyper SQL Database )
        
        Java로 만들어진 오픈 소스 DB Library
        Application 자체에 DB까지 내장할 수 있는 장점
        같은 방식의 Lib = Java DB( Apache Derby 등 존재 )
        HSQLDB는 용량이 매우 적고, 사용이 쉬운 장점
        파일에 저장하는 것은 물론 메모리에 DB를 저장할 수 있어, 개발 or Test DB로 적합
        메모리에 데이터를 캐시하고 있으므로, 종료화 함께 데이터는 없어진다.
        
    2) JTA ( Java Transaction API )
    
        Java EE에서 트랜잭션 처리를 제공한다.
        JPA와 JTA를 조합해 지속적 처리를 구현한다
        
    3) Spring ORM ( Object-Relational Mapping )
    
        Spring에 존재하는 ORM Framework
        ORM = 객체와 DB Table을 매핑해서 임피던스 불일치( Impedance mismatch ) 문제 해결 = RDB와 Java Object 설계 구조의 차이로 발생하는 문제
        
    4) Spring Aspects / Spring AOP
    
        Spring Framework 내부에 Framework
        기능 직접 호출해 사용 x / DB를 자유롭게 사용할 수 있게 Background에서 동작하는 구조
     
### Entity

- 하나하나의 레코드를 자바 객체로 저정한 것
- Annotation @Entity
- 매우 단순한 구조
- = 일반적인 POJO ( Plain Old Java Object, 아무 상속 관계나 의존 관계가 없는 단순 자바 객체 ) 라고 한다
```
@Entity
public class 클래스명{
    private 필드 정의;
    ... 필요한 만큼 필드 정의 ...
}
``` 

### Repository

- DB 접속 설정 중 하나
- 데이터베이스 접속을 위한 기본 수단 제공
- Class를 구현 or Implement 하지 않고 별도 처리도 작성하지 않는다.
- @Repository 사용

### Bean이 등록되기 까지 흐름

- Application 실행 시 @Repository가 붙은 인터페이스를 검색 > 자동으로 클래스를 생성 > 해당 객체를 Application Bean으로 등록
- Controller 등의 클래스가 Load 될 때 @Autowired 가 설정된 필드가 있으면, 등록 완료된 Bean에서 동일 클래스를 검색해 자동으로 해당 필드에 할당






