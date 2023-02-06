---
title: Spring Annotation
layout: post
categories: [SpringFramework]
tags: [SPRING]
---

### Annotation
사전적 의미는 "주석" 이지만, JAVA에서는 코드 사이에 주석 처럼 쓰이며 특별한 의미나 기능을 수행하는 기술이다.
즉, 프로그램에게 추가적인 정보를 제공하는 메타데이터라고 볼 수 있다.

#### 용도
1. 컴파일러에게 코드 작성 문법 에러 체크하도록 정보 제공
2. 빌드나 배치 코드를 자동으로 생성할 수 있도록 정보 제공
3. 실행 시 특정 기능을 실행하도록 정보 제공

### 그 동안 사용했던 것

@SuppressWarnings
- Java의 경고를 제외할 때 사용
- 하나만 적용 : @SuppressWarnings("rawtypes")
- 두 개 이상 적용 : @SuppressWarnings({"rawtypes", "unchecked"})

all : 모든 경고
cast : 캐스트 연산자 관련 경고
dep-ann : 사용하지 말아야 할 주석 관련 경고
deprecation : 사용하지 말아야 할 메서드 관련 경고
fallthrough : switch문에서 break 누락 관련 경고
finally : 반환하지 않는 finally 블럭 관련 경고
null : null 분석 관련 경고
rawtypes : 제너릭을 사용하는 클래스 매개 변수가 불특정일 때의 경고
unchecked : 검증되지 않은 연산자 관련 경고
unused : 사용하지 않는 코드 관련 경고
