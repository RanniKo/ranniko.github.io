---
title: Codeigniter4 개발환경 구축
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### Windows10 / Apache / PHP 개발환경 구축 2가지 방법
    개발환경은 Local 에 *.php 소스를 디버깅 하는 단계까지 구현

개발 Tool은 Visual Studio Code를 이용했다.
[Visual Studio Code 다운로드](https://code.visualstudio.com/download)

요새 PC에 이것저것 설치하다 보니, 이미 tomcat이 설치되어 있었다.
늘 JSP OR Spring / Boot를 공부하던 내가 PHP를 공부하기 위해서는 동작 방식 부터 이해할 필요가 있었다.

Local 개발 환경은 크게 2가지로 구분해 구성할 수 있다.

1. Apache 설치 후 해당 웹디렉토리에 php 소스를 배포해 확인하는 방법
- 설치할 내용이 많긴 하지만, php 소스 배포에 대한 이해를 위해 1번 방법도 추천

2. Composer를 이용한 구축 방법
- 간단하게 Local 환경 구성 가능

우선 Local에 이미 Spring을 사용하기 위한 tomcat이 존재했기 때문에, Apache 부터 설치를 진행했다.
그리고 java 구성은 그대로 이용하기 위해 Local에 다중 호스트(Virtual host) 설정도 진행했다. 

#### Apache 설치 후 해당 웹디렉토리에 php 소스를 배포해 확인하는 방법
* PHP8 / APACHE2.4

1. PHP 다운로드 [다운로드](https://windows.php.net/download/)
    
Thread Safe(TS)로 다운로드 후 압축 해제 ( 이 때, php8apache2_4.dll 파일 존재해야함 )
![php00](/assets/img/php_00.png)
    
2. Apache 다운로드 [다운로드](https://www.apachelounge.com/download/)
    
다운로드 후 특정 Directory에 압축 해제
![apache24](/assets/img/apache24.png)

3. Local 환경설정

-  apache httpd conf 설정
![apache24setting](/assets/img/apache24_setting01.png)
    
- 명령프롬프트(cmd) 관리자권한 실행 > httpd.exe install 진행
```
    E:\Apache24\bin\httpd.exe -k install       
``` 
  
- services.msc or 서비스 실행 후 Apache2.4 구동 여부 확인 > 서비스 시작(실행) 
![apache24setting](/assets/img/php_apache00.png)

- 1)번에서 설치한 php directory 진입 > php.ini.development 파일 복사해 php.ini 파일 생성
![apache24setting](/assets/img/php_05.png)
    
- php.ini 파일 오픈 > php 위치 지정
![apache24setting](/assets/img/php_06.png)
    
- apache httpd conf 수정 ( php Load Module )

httpd 에서 사용할 Apache 위치 정의

![apache24setting](/assets/img/php_07.png)

php Dir 지정 및 모듈 Load  

**(주의사항!! php 버전에 따라 php Dir 지정 외에 LoadModule, *.dll 등 입력 정보 다름)**
![apache24setting](/assets/img/php_08.png)

- 기타 - Apache 다중 Host 설정

[Apache 다중Host 설정](https://jimnong.tistory.com/658)


**개발환경 실행**

1) ..\Apache24\htdocs 해당 위치를 workspace로 잡고 작업하는 방법

2) 다른 위치에서 개발소스 수정 후 관련 리소스를 ..\Apache24\htdocs 에 옮겨 확인하는 방법

위 1),2) 모두 github 에 존재하는 codeigniter4 framework의 기본 소스를 다운받아 작업 필요! 

#### Composer를 이용한 구축 방법
* PHP8
1. <Apache 설치 후 해당 웹디렉토리에 php 소스를 배포해 확인하는 방법> 의 1번, php.ini까지 완료 후 진행

2. Composer 설치 [다운로드](https://getcomposer.org/download/)
    
![php02](/assets/img/php_02.png)
    
![php03](/assets/img/php_03.png)
    
    설치 시 proxy 는 따로 설정하지 않고, php.exe 위치만 잘 지정해준다!

3. Codeigniter framework을 이용해 개발 소스 만들 위치 이동 및 명령어 실행 ( VS Code Terminal )
     
![php01](/assets/img/php_01.png)

```
    // 아래와 같이 composer 명령어 입력
    composer 프로젝트명 codeigniter4/appstarter project-root
```

CodeIgniter4는 PHP의 내장 웹 서버를 활용하여 CodeIgniter 라우팅이 동작하는 로컬 개발 서버와 함께 제공하기 때문에, 1~2 구성완료 후 몇 가지 Config 파일만 수정하면 서버를 띄울 수 있다.

텍스트 편집기로 app/Config/App.php 파일을 열고 기본(base) URL을 설정 ( .env 에서도 설정 가능 )

데이터베이스를 사용하려면 app/Config/Database.php 파일에 데이터베이스 정보를 설정 ( .env 에서도 설정 가능 )

개발환경 실행 전 소스 root 폴더로 이동 후 php spark serve 명령어 실행!

4. 개발환경 실행
```
    //터미널에서 실행 (기본 8080 포트)
    php spark serve
    
    //option host name 변경한 상태로 실행 / port 변경한 상태로 실행
    php spark serve --host local.ranniko.com  --port 3000
```

**자잘한 설정**

1) xdebug php.ini 부분 제거

2) create project error

오류메시지
```
    Problem 1
    - codeigniter4/framework[4.0.0, ..., v4.1.4] require ext-intl * -> it is missing from your system. Install or enable PHP's intl extension.
    - Root composer.json requires codeigniter4/framework ^4 -> satisfiable by codeigniter4/framework[4.0.0, ..., v4.1.4].
    To enable extensions, verify that they are enabled in your .ini files:
    - E:\php\php.ini
```

해결방법       
- php.ini 파일에서 ;extension=intl and remove the ;
![composer_setting_error01](/assets/img/composer_setting_error01.png)
    
3) mysql 연동을 위해서 php.ini 에서 아래 내용 제거필요
```
    CodeIgniter\Database\Exceptions\DatabaseException #8 Unable to connect to the database
    ;extension=mysqli just remove ; like this extension=mysqli
```

#### Debugging 환경 구성
1) var_dump(); exit 명령어를 통해 간단한 변수 데이터 확인 등으로 처리
```
    var_dump();
    exit; 
```       

2) VSCode Xdebug 로 Line 별 정보 확인

3) Codeigniter4 Debug 지원 toolbar 통해 확인
    
.env 파일에 2가지 주석해제 및 입력 필수
```
    CI_ENVIRONMENT = development
    app.baseURL = 'http://local.ranniko.com:3000'
```    
이 경우, 아래 이미지와 같이 local에 띄운 서버 접속 > 브라우저 하단에 변수나 View 등을 확인할 수 있는 toolbar가 노출된다.

![php04](/assets/img/php_04.png)

<br>
<br>
###### #Reference
{: .text-right }
[윈도우 10에서 PHP 최신 개발환경 구축하기](https://blog.naver.com/PostView.nhn?blogId=ndb796&logNo=221395476384)
{: .text-right }
[Codeigniter4 Composer](http://ci4doc.cikorea.net/installation/installing_composer.html)
{: .text-right }
