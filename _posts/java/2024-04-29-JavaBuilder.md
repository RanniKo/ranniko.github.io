---
title: Java Builder
layout: post
categories: [Java]
tags: [JAVA]
---

## Apache Ant  
> 제일 처음 출시한 빌드 도구  
  
#### 특징  
1. 유연성 : 코딩 규칙, 프로젝트 구조를 강조하지 않는다.  
2. Xml 기반 스크립트로 작성 ( build.xml )  
3. Ant 하위 프로젝트인 Apache lvy 통해 의존성 관리 가능  
  
#### 단점  
1. 개발자가 모든 명령을 스스로 작성, lvy 등장 전까지 종속성 관리가 어려워 개발자가 파악해야했다.  
2. build 파일 이해 시간 소요  
3. 유지 보수하기 어려운 xml 파일  
  
  
## Apache Maven  
> 종속성 관리 + 빌드 도구, Ant 대안으로 출시  
  
#### 특징  
1. 규칙성 : 규칙에 의존, 사전에 정의된 목표 제공  
2. Xml 기반 스크립트 작성 ( pom.xml )  
3. 정해진 라이프사이클에 의해 작성 수행, 전반적인 프로젝트 관리 기능을 포함  
4. 종속성 관리 가능 ( library 를 pom.xml 파일에 작성하면, 자동으로 N/W 통해 다운, 특정 library 에 종속된 libraries 까지 다운 )
  
#### 단점  
1. 엄격한 프로젝트 구조 규정, Ant 에 비해 유연성이 떨어진다.  
2. Maven 에서 지원하지 않는 빌드 과정을 추가해야하는 경우, 복잡도 상승  
3. 정적인 데이터를 저장하는 xml 파일이기 때문에 동적인 정의가 어렵다.  
  
[Pom.xml](https://ranniko.github.io/posts/MavenPom/)
  
  
## Gradle  
> Gradle(그래들)  
> Maven 의 장황한 설정 파일과 에러가 쉽게 나는 문제를 해결하기 위해 만들어졌다.  
> 종속성 관리 + 빌드 도구  
  
#### 특징  
1. Java, Groovy, Kotlin 등 지원  
2. Groovy 기반의 빌드 도구 ( DSL 로 작성된 빌드 도구 ) **Domain-Specific Language  
3. 언어가 특정 도메인 문제를 해결하도록 설계, 구성 파일의 크기가 작아졌다. ( build.gradle )  
4. Groovy 언어를 기반으로 동적 정의 가능, 공통 설정 조건을 특정 프로젝트에 주입 가능  
  
  


<br/>
<br/>
###### #Reference  

[참고](https://doosicee.tistory.com/entry/JAVA%EC%9D%98-%EB%B9%8C%EB%93%9C%ED%88%B4%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)

