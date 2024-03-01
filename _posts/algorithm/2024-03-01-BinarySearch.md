---
title: 이진 탐색(Binary Search)
layout: post
categories: [Algorithm]
tags: [ALGORITHM]
---

## 이진 탐색 = 이분 탐색
> **정렬**돼 있는 데이터에서 특정한 값을 찾아내는 알고리즘<br/>
> **정렬**된 구조에서만 사용할 수 있기 때문에 정렬된 배열, 리스트나 트리에서 사용이 가능<br/>
> 중간점 탐색방식<br/>
> 탐색 범위를 반으로 나누어 찾는 값을 포함하는 범위를 좁혀가는 방식으로 동작<br/>
> 이진탐색의 시간 복잡도는 O(log n)으로, 배열의 크기에 비례하여 실행 시간이 빨라진다.<br/>
> 대용량 데이터에서 특정 값의 위치를 찾는 방법에 용이

### 예제

```java
public int binarySearch(int[] array, int target){
  int leftIndex = 0;
  int rightIndex = array.length-1;

  while (leftIndex <= rightIndex){
    int middleIndex = (leftIndex + rightIndex) / 2;

    if(array[middleIndex] == target){
      return middleIndex;
    }
    else if(array[middleIndex] < target){
      leftIndex = middleIndex+1;
    }
    else{
      rightIndex = rightIndex-1;
    }
  }
  return -1;
}

```

<br/>
<br/>

###### #Reference
[참고](https://velog.io/@kwontae1313/%EC%9D%B4%EC%A7%84-%ED%83%90%EC%83%89Binary-Search-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B0%9C%EB%85%90)
