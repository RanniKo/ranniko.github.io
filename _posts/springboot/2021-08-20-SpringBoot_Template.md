---
title: Spring Boot Template
layout: post
categories: [SpringBootFramework]
tags: [SPRING BOOT]
---

### Spring Boot Template

#Model
- 템플릿에서 사용할 데이터들을 일괄해서 관리한다. 데이터 관리가 전부로 뷰 관련 정보는 갖고 있지 않다.
- Model을 반환값을 사용할 수 없다( MVC )

#ModelAndView
- 템플릿에서 사용할 데이터들과 뷰 관련 정보를 일괄해서 관리한다. 뷰 관련 정보를 갖고 있어 ModelAndView를 그대로 반환값으로 사용할 수 있다.

## 타임리프(Thymeleaf)
~~~
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>

<html xmlns:th="http://www,thymeleaf.org">
~~~
th:XX 형식으로 속성을 html 태그에 추가해서 값이나 처리 등을 페이지에 심는다
	
## JSP(JavaServer Pages)
- 스프링 부트에선 app을 자바 서버와 함께 jar 파일로 묶어서 배포하는 경우가 많지만, 이 방법으론 jsp가 동작하지 않는다.
- 자바 서버가 실행된 환경에서 war 파일을 업로드 하는 경우에 동작
- 스크립틀릿(scriptlet)라는 기능으로 자바 코드를 직접 태그 안에 작성
- View와 Code가 섞여 로직 분리가 어려움
~~~
<dependency>
    <groupId>org.apache.tomcat.embed</groupId>
    <artifactId>tomcat-embed-jasper</artifactId>
</dependency>
~~~
	
##프리마커(FreeMarker)
- ${XX} 형식으로 값을 채워 나가는 템플릿
- 제어를 위해서 <#XX> 형식의 태그를 사용하기 때문에 html 편집기 등에선 html 구조에 영향을 줄 수 있다.

##그루비(Groovy)
- JVM에서 동작하는 스크립트 언어
~~~
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-groovy-templates</artifactId>
</dependency>
~~~
##벨로시티(Velocity)
- Apache Software Foundation에서 개발중인 템플릿 엔진
- $ / # 같은 특수한 문자를 사용해 변수 등을 html 코드 내에 작성
- 프리마커와 비슷하지만, 태그 없이 바로 작성 할 수 있어서, 비주얼 편집기 등에선 영향이 적다

##머스타시(Mustache)
- java, php, ruby, python, javascript 등에 사용할 수 있어서 자바 이외의 언어를 사용하고 싶은 사람에게 좋은 대안이 될 수 있다.
- "\{\{\}\}" 기호를 이용
