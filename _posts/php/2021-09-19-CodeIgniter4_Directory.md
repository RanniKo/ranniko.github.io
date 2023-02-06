---
title: CodeIgniter4 구조
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### CodeIgniter4

framework 설치 이후 생성되는 Directory 는 총 6개

**/app**
<br>
app Direatory는 이미 namespace 이기 때문에, application 요구사항에 맞게 구조를 자유롭게 변경 가능
<br>
- /Config >> 구성파일저장
- /Controllers >> Controllers
- /Database >> DB MIG 및 seed file 저장
- /Filters >> Controller 전/후에 실행할 수 있는 Filter Class
- /Helpers >> 독립형 함수(Helper) 저장
- /Language >> 다국어 지원을 위한 언어 파일
- /Libraries >> 카테고리에 포함되지 않는 유용한 Class
- /Models >> Models
- /ThirdParty >> App에서 사용할 수 있는 타사 Library
- /Views >> Html View
<br><br>

**/system**
<br>
- Framework 구성 파일 / 수정 X
<br><br>

**/public**
<br>
- 브라우저로 Access 할 수 있는 Web Application 일부 보관 / .htaccess file, index.php / css / js or img 등 / web Root를 의미    
<br><br>

**/writable**
<br>
- Application 동작하는 동안 보관하는 정보 / 캐시 / 로그 및 사용자가 업로드한 데이터를 저장하기 위한 Directory
<br><br>

**/tests**
<br>
- Test files
<br><br>

**/docs**
<br>
- Guide
<br>


<br>
<br>
###### #Reference
{: .text-right }
[어플리케이션 구조](http://ci4doc.cikorea.net/concepts/structure.html)
{: .text-right }


