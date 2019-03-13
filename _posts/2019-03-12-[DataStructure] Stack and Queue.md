---
title: "[DataStructure] Stack and Queue"
layout: single
categories:
  - DataStructure
Tags:
  - DataStructure, Stack, Queue, CollectionFramework,

---
Stack and Queue

## Stack

선형 자료 구조의 일종으로 `Last In First Out (LIFO)`  
한 쪽 끝에서만 요소를 넣거나 뺄 수 있는 구조라 나중에 넣은 요소가 먼저 나온다.  

### 용도  
- 웹 브라우저 방문 기록 (뒤로 가기)  
- 실행 취소  
- 역순 문자열 만들기  
- 후위표기법 계산 

### method
- pop() : 제일 위에 있는 요소를 꺼내서 반환한다.  
- push(item) : 요소를 추가한다.  
- peek() : 제일 위에 있는 요소를 확인한다.  
- boolean empty() : 현재 스택이 비어있는지를 확인한다. 
- int search(Object o) : o의 위치를 반환한다. (제일 위에 있는 요소부터 1)

---
  
## Queue  

선형 자료 구조의 일정으로 `First In First Out (FIFO)`   
먼저 넣은 요소가 먼저 나온다.  

### 용도  
- 너비 우선 탐색(BFS) 구현  
- 선입선출이 필요한 대기열 (티켓 카운터)  
- 프린터의 출력 처리  
- 프로세스 관리  


### method  
- add(item) : 요소를 추가한다.  
- remove() : 제일 먼저 넣은 요소를 제거한다.  
- peek() : 제일 먼저 넣은 요소를 확인한다.
- isEmpty() : 현재 큐가 비어있는지 확인한다.  

---
참고
[위키백과, 우리 모두의 백과사전](https://ko.wikipedia.org/wiki/%ED%81%90_(%EC%9E%90%EB%A3%8C_%EA%B5%AC%EC%A1%B0))  
[자바의 스택(Stack)](http://alecture.blogspot.com/2012/10/stack.html)  
[[자료구조] 큐(Queue)란](https://gmlwjd9405.github.io/2018/08/02/data-structure-queue.html)  
[59) Stack과 Queue](http://tcpschool.com/java/java_collectionFramework_stackQueue)
