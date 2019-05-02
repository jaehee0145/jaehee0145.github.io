---
title: "[Spring] Dependency Injection"
layout: single
categories:
  - Spring
  - Java

---

Learn about Spring :)  
    &nbsp;&nbsp;  

## 1. Object Dependencies (객체 의존성)  
- 코드에서 두 모듈 간의 연결  
- 객체지향언어에서는 두 클래스 간의 관계라고도 말함  
- 일반적으로 둘 중 하나가 다른 하나를 어떤 용도를 위해 사용함  

```java
public class Programmer{
    private Computer computer;

    public Programmer() {
        this.computer = new Macbook();
    }
}
```
- Programmer 객체는 Computer객체(Macbook)에 의존한다.  
  - Programmer 생성자에서 new Macbook();을 통해 Macbook에 의존성을 가진다  


## 2. Dependency가 위험한 이유  
- 하나의 모듈이 바뀌면 의존한 다른 모듈까지 변경이 이루어지기 때문  
  - Computer 객체를 변경하면 Programmer 객체도 변경된다.  
- 유닛테스트 작성의 어려움  
  - Programmer 클래스 테스트가 실패하면 Programmer 클래스의 문제인지, Macbook 클래스의 문제인지 알 수 없다.

## 3. Dependency Injection (의존성 주입)  
- 객체 자체가 아니라 **Framework에 의해** 객체의 의존성이 주입되는 설계 패턴  
- 'new'를 사용해 모듈 내에서 다른 모듈을 초기화 하지 않고 외부에서 객체를 생성해, 생성된 객체를 참조시킴  

![](http://www.einnovator.org/store/docs/tutorials/spring/beans/dimg/injection.png)
  - 예> XML Config의 설정대로 Bean Container가 Bean A, Bean B를 생성하고 종속성을 주입한다  

- 의존성 주입은 'Inversion of Control' 개념을 바탕으로 한다  
  - 개발자가 설정(xml, annotation 등)을 하면 Container가 코드 전체에 대한 제어를 담당한다  

## 4. Dependency Injection 방법  
1. Constructor Injection 생성자 삽입   
2. Field Injection 멤버 변수 삽입   
3. Method Injection 메소드 매개 변수 삽입  

## 5. Dependency Injection의 이점  
- 클래스를 재사용 용이  
- 독립적인 테스트 가능  
- 코드 단순화로 가독성 증가  

## 6. DI Container의 종류  
1. Spring Container  
   - IoC/DI가 자바의 표준 프로그래밍 모델로 발전해오며 다양한 종류의 프레임워크가 등장했지만 Spring이 독보적이다.  강력한 기능을 갖고 있고 다양하게 컨테이너를 사용할 수 있기 때문  
   - Spring IoC Container가 관리하는 객체를 bean이라고 부른다. 이러한 bean을 관리한다는 의미로 컨테이너를 Bean Factory라고 부른다.  
   -  Spring은 단순한 DI작업보다 더 많은 일을 한다. 엔터프라이즈 애플리케이션을 개발하는 데 필요한 컨테이너 기능을 추가하여 Application Context라고 부른다.  
2. Pico Container  
    - DI 자체에 집중한 작은 프레임워크  
    - xml, annotation이 필요 없는 단순한 구성이며, 복잡한 대형 프로젝트에 적합하지 않다  
3. Guice  
    - 구글이 발표한 DI 프레임워크  
    - annotation을 사용하여 자바 객체를 구성하도록 DI를 구현  
    - 사용이 편리하고 에러메시지가 확실하며 속도가 빠르다는 것이 장점이다  







*** 

##### 참고
[[Design Pattern] DI란 (Dependency Injection)](https://gmlwjd9405.github.io/2018/11/09/dependency-injection.html)  
[DI 첫 번째, Dependency Injection에 관하여](https://poqw.github.io/di_1/)  
[DI(Dependency Injection) 와 Dagger2 (1)](https://cmcmcmcm.blog/2017/07/27/didependency-injection-%EC%99%80-dagger2/)  
[[DI] Dependency Injection 이란?](https://medium.com/@jang.wangsu/di-dependency-injection-%EC%9D%B4%EB%9E%80-1b12fdefec4f)  
[DI (Dependency Injection)가 뭘까?](https://siyoon210.tistory.com/122?category=839542)   
[Dependency Injection 이해하기](https://imcreator.tistory.com/106)  
[세 가지 DI 컨테이너로 향하는 저녁 산책](http://www.nextree.co.kr/p11247/)  