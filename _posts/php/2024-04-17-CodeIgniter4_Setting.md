---
title: Codeigniter4 Local 서버 실행
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4]
---

### Local 서버 실행

- 기본 Local 8080 port  
```  
    php spark serve       
``` 

- port change  
```  
    php spark serve -port 8000       
``` 

- allow anywhere  
```
    php spark serve -host 0.0.0.0         
``` 

- allow anywhere & port change
```
    php spark serve -port 8000 -host 0.0.0.0       
``` 


###### #Reference  
[CI4](https://blog.naver.com/pareko/221862055929)
