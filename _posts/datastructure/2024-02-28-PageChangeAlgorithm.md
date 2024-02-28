---
title: 페이지 교체 알고리즘
layout: post
categories: [Data-Structure]
tags: [DATA STRUCTURE]
---

## 페이지 교체 알고리즘
> OS는 CPU보다 큰 용량의 프로그램을 실행하기 위해 프로그램의 일부만 CPU에 적재해 사용한다. = 가상 메모리 기법<Br/>
> 페이징 기법으로 메모리를 관리하는 OS에서, 필요한 페이지가 CPU에 적재되지 않았을 때(페이지 부재) 어떤 페이지 프레임을 선택하여 교체할 것인지 결정하는 방법 = 페이지 교체 알고리즘

### 페이지 교체 알고리즘 종류
- OPT - Optimal : 앞으로 가장 오랫동안 사용되지 않을 페이지 교체
- FIFO - First In First Out
- LRU - Least Recently Used : 가장 오랫동안 사용되지 않은 페이지 교체
- LFU - Least Frequently Used : 참조 횟수가 가장 작은 페이지 교체
- MFU - Most Frequently used : 참조 횟수가 가장 많은 페이지 교체
- NUR - Not Used Recently : 최근에 사용하지 않은 페이지 교체


<br>
<br>
{: .text-right }
###### #Reference
<br>
[참고](https://doh-an.tistory.com/28)
{: .text-right }
