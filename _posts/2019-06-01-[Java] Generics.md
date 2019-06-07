---
title: "[Java] Generics"
layout: single
categories:
  - Java
Tags:
  - Java

---
How to master Java

### 1. Overview  
> Java Generics were introduced in JDK 5.0 with the aim of reducing bugs and adding an extra layer of abstraction over types.  -by baeldung  

### 2. 제네릭이란?  
클래스와 인터페이스, 메소드를 정의할 때 타입을 파라미터로 사용할 수 있도록 한다.  

* 컴파일 시 강한 타입 체크를 할 수 있다.  
  * 런타임이 아닌 컴파일 시 에러를 체크해서 방지한다.  

* 타입 변환(casting)을 제거한다.  
  * 비제네릭 코드는 불필요한 타입 변환이 필요해서 프로그램 성능에 악영향을 준다.  

```java
  List list = new ArrayList();
  list.add("test");
  String s = (String)list.get(0); //타입 변환이 필요 
```
  * List에 문자열을 저장했는데 다시 꺼내올때 String으로 타입 변환을 해야 한다.  

```java
  List<String> list = new ArrayList<String>();
  list.add("hello");
  String s = list.get(0); // 타입 변환이 필요하지 않음
```
  
---
참고  

[제네릭스(Generics) - 1. 제네릭 사용 방법](https://siyoon210.tistory.com/14)  
[The Basics of Java Generics](https://www.baeldung.com/java-generics)  
[TCP school](http://tcpschool.com/java/java_generic_concept)
  