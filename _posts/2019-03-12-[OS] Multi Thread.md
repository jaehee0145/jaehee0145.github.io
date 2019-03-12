---
title: "[OS] Multi-Thread"
layout: single
categories:
  - OS
Tags:
  - OS, JAVA

---
Multi-Thread

## 스레드와 프로세스의 개념  

프로세스란(process)란?  
> 프로그램이 운영체제에 의해 메모리 공간을 할당받아 실행 중인 것을 말한다.  

스레드(thread)란?
> 프로세스 내에서 실제로 작업을 수행하는 주체  
모든 프로세스에는 한 개 이상의 스레드가 존재하여 작업을 수행  

멀티 스레드(multi thread)  
> 하나의 프로세스 내에서 둘 이상의 스레드가 동시에 작업을 수행하는 것  
각 스레드가 자신이 속한 프로세스의 메모리를 공유 

멀티 프로세스 (multi process)  
> 여러 개의 CPU를 사용하여 여러 프로세스를 동시에 수행하는 것  
각 프로세스가 독립적인 메모리를 가지고 별도로 실행  


## 멀티스레드의 장점과 단점  
### 장점  
1. 응답성 증가 
   일부 스레드가 중단되거나 긴 작업을 수행하더라도 다른 스레드에 의해 프로그램이 계속 수행된다.  
2. 자원 공유  
   각 스레드가 속한 프로세스의 메모리와 자원을 공유한다.  
3. 경제성  
    프로세스를 생성할 때 메모리와 자원을 할당하는 것은 비용이 많이 든다.  
    스레드는 속한 프로세스의 메모리와 자원을 공유하기 때문에,  
    스레드르 생성하고 문맥교환을 하는 것이 경제적이다.  
4. 멀티 프로세서 활용  
    멀티프로세서 구조에서는 각각의 스레드가 다른 프로세서에서 병렬로 수행될 수 있다.  

### 단점  
1. 공유 자원  
   - 스레드는 프로세스 내의 데이터와 힙 영역을 공유하기 때문에  
      다른 스레드가 사용중인 변수나 자료구조에 접근해서 잘못된 값을 가져올 수 있다.  
   - 이를 방지하기 위해 동기화 작업이 필요하다.   
   


---
참고
[멀티 쓰레드(Multi Thread)란 무엇인가?](https://goodgid.github.io/What-is-Multi-Thread/) [스레드의 개념](http://tcpschool.com/java/java_thread_concept)  
 