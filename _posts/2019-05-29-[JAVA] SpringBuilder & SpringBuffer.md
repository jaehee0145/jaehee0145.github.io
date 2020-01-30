---
title: "[Java] SpringBuilder & SpringBuffer"
layout: single
categories:
  - Java
Tags:
  - Java

---
How to master Java

## 1. Overview  
Java에서는 문자열을 처리하기 위해 String 클래스를 제공한다. `+`를 이용해서 문자열을 연산할 수 있다는 것은 아주 처음에 배우는 부분이다. 하지만 `+`는 좋은 방법이 아니라고 한다.  
문자열 처리를 위해 제공하는 String, StringBuilder, StringBuffer에 대해 알아보고 어떤 경우에 어떤 클래스를 쓰는 것이 좋을지 알아보자.  

## 2. String  
###  String은 immutable하다.    
String이 다른 클래스(StringBuilder, StringBuffer)와 다른 점은 immutable(불변)하다는 것이다.  

String 객체는 한 번 생성되면 변하지 않는다. `+` 연산자나 concat 메서드를 이용해서 기존에 생성된 String 객체에 연산을 하면 기존 객체에 새로운 문자열이 더해지는 것이 아니라 새로운 String 객체를 생성해서 문자열 연산한 결과를 저장한다.  

String 연산을 반복하면 각 String 객체의 주소값이 stack에 쌓이고 객체들은 Garbage Collector가 동작하기 전까지 heap 메모리 영역에 추가된다.  

String 객체는 immutable하기 때문에 동기화를 고려하지 않아도 된다.(Thread safe)  

## 3. StringBuilder vs StringBuffer  
### StringBuilder와 StringBuffer는 모두 mutable(변경 가능)하다. 
객체는 한번만 생성하고 연산할 때 문자열을 변경한다.  

### StringBuffer는 멀티스레드 환경에서 동기화를 보장하고 StringBuilder는 동기화를 보장하지 않는다.  
Java5부터 StringBuffer를 대체해서 StringBuilder를 사용하도록 제공하고 있다. (동일한 메서드를 사용할 수 있음)  
StringBuilder는 동기화를 고려하지 않기 때문에 StringBuffer에 비해 연산 속도가 빠르고 싱글스레드 환경에서 유리하다.  

## 4. Conclusions  
* String: 문자열 연산이 필요없는 싱글스레드 환경에서 유리  
* StringBuilder: 문자열 연산이 필요한 싱글스레드 환경에서 유리  
* StringBuffer: 문자열 연산이 필요한 멀티스레드 환경에서 유리    

> In single-threaded programs, we can take of the StringBuilder. Yet, **the performance gain of StringBuilder over StringBuffer may be too small to justify replacing it everywhere.** It's always a good idea to profile the application and understand its runtime performance characteristics before doing any kind of work to replace one implementation with another.  -From Baeldung  

* StringBuffer 대신 StringBuilder를 사용해서 얻는 효과가 미비하다면 의미가 없다. application과 runtime 환경을 이해하고 적절히 사용하는 것이 중요하다.  

---
참고  

[StringBuilder and StringBuffer in Java](https://www.baeldung.com/java-string-builder-string-buffer)  
[JAVA String, StringBuffer, StringBuilder 차이점](https://jeong-pro.tistory.com/85)  
[Java에서 String, StringBuilder, StringBuffer의 차이](https://novemberde.github.io/2017/04/15/String_0.html)    
[Class StringBuilder API](https://docs.oracle.com/javase/7/docs/api/java/lang/StringBuilder.html)






  