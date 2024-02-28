---
title: Spring Boot Junit
layout: post
categories: [SpringBootFramework]
tags: [SPRING BOOT]
---

### Junit

- [참고1](https://junit.org/junit5/docs/current/user-guide/)
- [참고2](https://junit.org/junit5/docs/current/user-guide/#running-tests-ide-intellij-idea)

  - Swagger UI 접속 설정
    ```
    # build.gradle 의존성 추가
    testImplementation 'org.junit.platform:junit-platform-launcher'
    testImplementation 'org.junit.jupiter:junit-jupiter-api'
    testImplementation 'org.junit.jupiter:junit-jupiter-engine'
    testImplementation 'org.junit.jupiter:junit-jupiter-params'
    ```
    ```
    # 필수 추가
    test {
      useJUnitPlatform()
    }
    ```

###### #Reference
<br>
<br>
{: .text-right }
[참고](https://blog.naver.com/ssuyastory/221644575256)
{: .text-right }
