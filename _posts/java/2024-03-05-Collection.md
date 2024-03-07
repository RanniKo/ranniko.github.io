---
title: Java Collection Framework
layout: post
categories: [Java]
tags: [JAVA]
---

### Collection Framework Hierarchy in Java
![Collection Framework](/assets/img/java/collection_frmwk.jpeg)  

[참고](https://techvidvan.com/tutorials/java-collection-framework/)  

#### 1. Collection(List)  
> 순서를 갖고, 원소의 중복 허용  

#### 1-1. ArrayList  
> a. 배열을 이용하여 만든 리스트  
> b. (배열의 특징) 조회 빠르고, 삽입/삭제 느림  
```
  List<Integer> list = new ArrayList<>();
  list.add(1);
  list.get(1); // index 이용
```  

#### 1-2. LinkedList  
> a. Node와 Pointer 를 이용해 만든 리스트  
> b. next / prev 로 양방향 포인터를 갖는다.  
> c. 삽입/삭제 빠름 / 특정 원소를 조회하기 위해서는 첫 노드부터 순회 조회속도 ArrayList에 비해 느림    
```
  List<Integer> list = new LinkedList<>();
  list.add(1);
  list.get(1); // index 이용
  list.size();
```  

#### 1-3. Vector  
> a. 배열을 이용하여 만든 리스트  
> b. Thread-Safe 동기화 지원 / 한 번에 하나의 Thread만 접근 가능, Multi-Thread 환경에서 사용하기 좋음  
> c. get / put 모두에 synchronized 존재 / Thread 마다 Lock이 걸리게 되기 때문에 ArrayList보다 성능이 안좋은 단점이 있다.    
```
  List<Integer> vector = new Vector<>();
  vector.add(1);
  vector.get(1); // index 이용
  vector.size();
```  
* 비동기 형태 매핑
```
List<T> synchronizedList(List<T> list) → 동기화된 List 반환  
Map<K,V> synchronizedMap(Map<K,V> map) → 동기화된 Map 반환  
Set<T> synchronizedSet(Set<T> set) → 동기화된 Set 반환  
```  

#### 1-4. Stack  
> a. LIFO  
> b. push / pop  
> c. Stack은 Vector를 implements  
```
  List<Integer> stack = new Stack<>();
  vector.push(1);
  vector.pop(); // index 이용
  vector.size();
```  

#### 2. Collection(Set)  
> 집합, 순서가 없고 원소의 중복을 허용하지 않는 특징  

#### 2-1. HashSet  
> a. 대표적인 Set 자료 구조  
> b. 순서 없음  

```
  Set<Integer> hashSet = new HashSet<>();
  hashSet.add(1);
  hashSet.add(2);
  hashSet.add(2);//중복 무시
  
  // add 순서 무관 출력
  Iterator iter = hashSet.iterator();
  while (iter.hasNext()){
      System.out.println("iter.next() = " + iter.next());
  }
```  

#### 2-2. LinkedHashSet  
> a. 중복 허용 안함  
> b. 순서 있음  

```
  Set<Integer> hashSet = new LinkedHashSet<>();
  hashSet.add(1);
  hashSet.add(2);
  hashSet.add(2);//중복 무시
  
  // add 순서대로 출력됨
  Iterator iter = hashSet.iterator();
  while (iter.hasNext()){
      System.out.println("iter.next() = " + iter.next());
  }
```  

#### 2-3. TreeSet  
> a. 중복 허용 안함  
> b. 순서 없음  
> c. 데이터 정렬 후 저장하는 특징  

```
  Set<Integer> treeSet = new TreeSet<>();//오름차순
  //Set<Integer> treeSet = new TreeSet<>(Collections.reverseOrder());//내림차순
  treeSet.add(3);
  treeSet.add(7);
  treeSet.add(1);
  
  Iterator<Integer> iter = treeSet.iterator();
  while (iter.hasNext()){
      System.out.println("iter.next() = " + iter.next());
  }
```  

#### 3. Collection(Queue)
> a. FIFO  
> b. enqueue / dequeue  

#### 3-1. PriorityQueue  
> a. 이진 트리 구조  
> b. 원소에 우선순위를 부여하여 높은 순으로 먼저 반환  

```
  //오름차순
  Queue<Integer> queue = new PriorityQueue<>();
  queue.add(3);
  queue.add(331);
  queue.add(1);

  while (!queue.isEmpty()){
      System.out.println("queue.poll() = " + queue.poll());
  }
  //result : 1 > 3 > 331

  //내림차순
  queue = new PriorityQueue<>(Collections.reverseOrder());
  queue.add(3);
  queue.add(331);
  queue.add(1);

  while (!queue.isEmpty()){
      System.out.println("queue.poll() = " + queue.poll());
  }
  //result : 331 > 3 > 1
```  
 
#### 3-2. ArrayDeque  
> a. 양쪽에 넣고 빼는게 가능한 구조  

![deque](/assets/img/java/deque.png)  

```
  Deque<Integer> deque = new ArrayDeque<>();
  deque.offerLast(100); // 100
  deque.offerFirst(1); // 1 > 100
  deque.offer(2); // 1 > 100 > 2
  deque.offerFirst(3); // 3 > 1 > 100 > 2de
  deque.offerLast(119); // 3 > 1 > 100 > 2 > 119

  System.out.println("deque.poll() = " + deque.poll()); // 3
  System.out.println("deque.pollFirst() = " + deque.pollFirst()); // 1
  System.out.println("deque.pollLast() = " + deque.pollLast()); // 119
  System.out.println("deque.pop() = " + deque.pop()); // 100
```  

#### 4. Map  
> a. key-value 형태  
> b. 순서 없음  
> c. key 는 중복 불가  

#### 4-1. HashMap  
> 대표적인 Map 자료 구조  

```
  Map<Integer, String> map = new HashMap<>();
  map.put(2, "test1");
  map.put(1, "test2");
  map.put(5, "test3");

  Iterator<Integer> iter = map.keySet().iterator();
  while (iter.hasNext()){
      int key = iter.next();
      String value = map.get(key);
  }

  Set<Integer> keySet = map.keySet();
  for(Integer key : keySet){
      String value = map.get(key);
  }
```  

#### 4-2. Hashtable  
> a. HashMap과 동일한 특징  
> b. Thread-Safe  

```
  Map<Integer, String> map = new Hashtable<>();
  map.put(2, "test1");
  map.put(1, "test2");
  map.put(5, "test3");

  Iterator<Integer> iter = map.keySet().iterator();
  while (iter.hasNext()){
      int key = iter.next();
      String value = map.get(key);
  }
```  

#### 4-3. LinkedHashMap  
> put 한 순서대로 순서를 갖는다.  

```
  Map<Integer, String> map = new LinkedHashMap<>();
  map.put(2, "test1");
  map.put(1, "test2");
  map.put(5, "test3");

  Iterator<Integer> iter = map.keySet().iterator();
  while (iter.hasNext()){
      int key = iter.next();
      String value = map.get(key);
      System.out.println("key = "+key+" , value = " + value);
  }
  //result
  /*
    key = 2 , value = test1
    key = 1 , value = test2
    key = 5 , value = test3
  */
```  

#### 4-4. TreeMap  
> a. 이진 트리로 구성, TreeSet과 동일하게 정렬하여 데이터 저장  
> b. 데이터 저장 시 정렬하기 때문에, 시간이 다른 자료구조에 비해 오래걸림  

```
  //Map<Integer, String> map = new TreeMap<>();//오름차순
  Map<Integer, String> map = new TreeMap<>(Collections.reverseOrder());//내림차순
  map.put(2, "test1");
  map.put(1, "test2");
  map.put(5, "test3");

  Iterator<Integer> iter = map.keySet().iterator();
  while (iter.hasNext()){
      int key = iter.next();
      String value = map.get(key);
      System.out.println("key = "+key+" , value = " + value);
  }
  //result
  /*
    key = 5 , value = test3
    key = 2 , value = test1
    key = 1 , value = test2
  */
```  



<br/>
<br/>
###### #Reference

[참고](https://memostack.tistory.com/234)

