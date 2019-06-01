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

* Overloading과 Overriding은 객체 지향 프로그래밍의 특징 중 하나인 다형성을 구현하는 방법   
* 두 개념은 이름이 비슷하고 헷갈리기 쉽다. 개념을 확실히 이해하고 차이점을 알아보자.  

### 2. Overloading  
#### 매개 변수의 개수나 타입이 다른 메서드를 같은 이름으로 정의하는 것  
* 메서드에 사용되는 이름을 절약할 수 있다.  
* 메서드를 호출할 때 매개 변수에 크게 신경쓰지 않고 호출할 수 있다.  


#### Overloading의 대표적인 예) println()  
전달받는 매개 변수에 따라 적절한 메서드를 호출한다.  
> println()  
> println(boolean x)  
> println(char x)  
> println(int x)  
> println(Object x)  
> println(String x)  등등  

### 3. Overriding  
#### 부모 클래스에서 정의된 메소드를 자식 클래스에서 다시 정의하는 것  

#### 조건  
* 메서드 선언부(리턴 타입, 메서드 이름, 매개 변수)는 변경할 수 없다.  
* 부모 클래스의 메서드보다 접근 제어자를 좁게 변경할 수 없다.  
* 부모 클래스의 메서드보다 더 큰 범위의 예외를 선언할 수 없다.  


---
참고  

[Method Overloading and Overriding in Java](https://www.baeldung.com/java-method-overload-override)  
[[Java] 오버로딩과 오버라이딩의 차이(Overloading VS Overriding)](https://gmlwjd9405.github.io/2018/08/09/java-overloading-vs-overriding.html)  
[TCP School](http://tcpschool.com/java/java_inheritance_overriding)
  