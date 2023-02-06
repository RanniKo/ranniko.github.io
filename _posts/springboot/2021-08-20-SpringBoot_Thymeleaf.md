---
title: Spring Boot Template Thymeleaf
layout: post
categories: [SpringBootFramework]
tags: [SPRING BOOT]
---

### Spring Boot Template Thymeleaf

- ${XX} 형식
- 변수식 안에 작성하는 것 = OGNL(Object-Graph Navigation Language)식
- OGNL은 자바의 값에 접근하기 위한 식

#### 유틸리티 객체(Utility Object)
- java class 중 template에서 사용빈도가 높은 것을 controller에서 class 변수로 준비하는 것이 아닌, template에서 자주 사용하는 class 이름을 상후로 정의해 직접 작성 가능
- "#이름" 으로 정의

```
//이렇게 instance를 객체화 할 수 있다
<p th:text="${new java.util.Date().toString()}"/>
```

```
//#strings String클래스의 상수
<p th:text="${#strings.toUpperCase('Welcome to Spring.')}"/>
//#numbers Number 클래스의 상수
<p th:text="${#numbers.formatInteger(1234,7)}"/>
#bools Boolean 클래스의 상수
//#dates Date클래스의 상수
<p th:text="${#dates.format(new java.util.Date(), 'dd/MM/yyyy')}"/>
#objects Object 클래스의 상후
#arrays Array 클래스의 상후
#lists List 클래스의 상수
#sets Set 클래스의 상수
#maps Map 클래스의 상수
```

#### 문법
- th:text
- th:utext
타임리프 변수식으로 텍스트를 출력하는 경우 html 태그를 모두 이스케이프 처리하지 않고 출력하는 속성
- th:if="조건"
- th:unless="조건"
- th:switch="조건" / th:case="조건식"
- th:each="변수 : ${컬렉션}"
- th:inline="text" / th:inline="javascript"  
직접 html 태그 안에 값을 기술
```
<script th:inline="javascript">
	function action(){
		var val = document.getElementById("text1").value;
		var res = parseInt(val * ((100 + /*[[$(tax)]]*/) /100));
	}
</script>
```
- th:fragment="프래그먼트명"
footer / menu 같은 별도 파일을 조합해 페이지를 구성할 때, 특정 파일 안에 다른 템플릿을 삽입하는 기술
- th:include="템플릿명::프래그먼트명"
