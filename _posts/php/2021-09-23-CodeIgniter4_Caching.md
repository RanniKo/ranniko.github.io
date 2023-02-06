---
title: CodeIgniter4 Caching
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### Codeigniter4 Caching

#### CodeIgniter Caching
- 캐싱은 페이지별로 활성화할 수 있으며 페이지를 캐시 상태를 유지해야 하는 시간 설정 가능
- 페이지가 처음 로드되면 현재 구성된 캐시 엔진을 사용하여 파일로 캐시( 그 이후 페이지 로드시, 캐시 파일이 검색되어 요청하는 사용자의 브라우저로 전송 )
- 캐시가 만료된 경우 브라우저로 전송되기 전에 삭제되고 새로 고침 됨
- 벤치 마크 태그는 캐시되지 않음( 활성화 된 경우 페이지 로드 속도 확인 가능 )
- 캐시 파일을 작성하기 전에 app/Config/Cache.php 파일의 캐시 엔진을 설정 필요
- 출력(output)에 영향을 줄 수 있는 구성 옵션을 변경하면 캐시 파일을 수동으로 삭제해야함
- 캐시 코드 제거해도, 파일 만료될 때 까지 캐시 파일 갱신 X
    ```
    //Controller method에 추가
    // $n = 캐시 상태로 유지하려는 시간(초)
    $this->cachePage($n);
    ```
  

<br>
<br>
###### #Reference
{: .text-right }
[CodeIgniter Caching](http://ci4doc.cikorea.net/general/caching.html)
{: .text-right }


