---
title: CodeIgniter4 AutoLoad
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### CodeIgniter4 AutoLoad

Application 작동을 위해, 여러 Library 등을 사용할 때 매번 file 위치를 requires()로 처리하지 않기 위해 AutoLoad 사용
AutoLoad 는 framework 실행 초기에 등록되어 항상 활성화
```
    spl_autoload_register()
```
초기 설정 : /app/Config/Autoload.php

<br>
<br>
###### #Reference
{: .text-right }
[파일 오토로드(autoload)](http://ci4doc.cikorea.net/concepts/autoloader.html)
{: .text-right }


