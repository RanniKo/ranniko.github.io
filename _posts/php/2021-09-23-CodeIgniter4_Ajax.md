---
title: CodeIgniter4 AJAX
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### Codeigniter4 AJAX

- XHR 임을 식별하기 위해 Header에 수동으로 정의해서 호출 필요
XHR(Xml Http Request) = AJAX 요청을 생성하는 JavaScript API / XHR의 Method 이용해 Browser와 서버 간 N/W 요청 전송

    ```
    fetch(url, {
        method: "get",
        headers: {
            "Content-Type": "application/json",
            "X-Requested-With": "XMLHttpRequest"
        }
    });
    ```
  
<br>
<br>
###### #Reference
{: .text-right }
[CodeIgniter AJAX](http://ci4doc.cikorea.net/general/ajax.html)
{: .text-right }

