---
title: Parallels 에서 MAC Local Server 접속 
layout: post
categories: [Codeigniter4]
tags: [PHP, CODEIGNITER4, MAC, PARALLELS]
---

**Parallels Windows > Mac에서 실행한 웹서버 접속**  

### Local 서버 실행  
어디서든 접속 가능하도록 서버를 띄운다.  

```
    php spark serve -port 8000 -host 0.0.0.0       
``` 

### Parallels 네트워크 설정  
장치 > 네트워크 > 공유네트워크 사용  

### MAC 사설 IP 확인  
```
    ifconfig | grep inet       
```  
혹은 Parallels의 게이트웨이 확인 
```
    ipconfig  
```  

### Parallels 에서 접속  
![parallels1](/assets/img/etc/parallels1.png)  
  

- hosts를 바꿔서 접속    
![parallels2](/assets/img/etc/parallels2.png)

