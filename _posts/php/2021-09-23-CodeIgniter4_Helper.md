---
title: CodeIgniter4 Helper
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### Codeigniter4 Helper
- 특정 범주의 함수(function) 모음
- URL헬퍼/Form헬퍼/Text헬퍼/Cookie헬퍼/File헬퍼 등
- 다른 기능에 의존하지 않고 하나의 특정 작업을 수행
- 사용하기 위해 헬퍼 파일 로드 필요 ( CodeIgniter는 기본적으로 헬퍼 파일을 로드(load)하지 않음 )
- system/Helpers 또는 app/Helpers 디렉토리에 저장 [ 찾는 순위 : app/Helpers > system/Helpers ]
- URL 헬퍼는 항상 로드되므로 직접 로드 할 필요는 없음
    ```
    //helper load
    helper('helper name');
    //cookie helper load (= cookie_helper.php )
    helper('cookie');
    // 2개 이상 helper load = 이름 배열로 전달
    helper(['cookie', 'date']);
    // ex. Click Here 링크
    <?= anchor('blog/comments', 'Click Here');?>
    ```


<br>
<br>
###### #Reference
{: .text-right }
[CodeIgniter Helper](http://ci4doc.cikorea.net/general/helpers.html)
{: .text-right }

