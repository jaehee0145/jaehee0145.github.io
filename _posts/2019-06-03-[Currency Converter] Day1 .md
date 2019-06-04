---
title: "[Currency Converter] Day 1"
layout: single
categories:
  - Currency Converter
Tags:
  - Currency Converter

---
개발 일지  

### 1. 스프링 부트 프로젝트 생성  
- 인텔리제이에서 스프링부트 생성, Dependencies 추가

### 2. IndexController 생성  
- "/"로 접근하면 index.html을 보여주도록 설정  
- @Controller @GetMapping 사용  

### 3. 프로젝트와 Git 연동  
- 인텔리제이에서 연동  
- 참고: [intelliJ Github 연결 후 저장소 생성 및 푸쉬(push) - 403 에러](https://wings2pc.tistory.com/entry/intelliJ-Github-%EC%97%B0%EA%B2%B0-%ED%9B%84-%EC%A0%80%EC%9E%A5%EC%86%8C-%EC%83%9D%EC%84%B1-%EB%B0%8F-%ED%91%B8%EC%89%ACpush-403-%EC%97%90%EB%9F%AC)  
- Commit message Convention을 지켜보고자 함  
  - 형식  
    > chore (commit type): 프로젝트 생성 (commit 내용 한글로 작성)  
  - Commit Type  
    - feat: a new feature  
    - fix: a bug fix
    - docs: changes to documentation
    - style: formatting, missing semi colons, etc; no code change
    - refactor: refactoring production code
    - test: adding tests, refactoring test; no production code change
    - chore: updating build tasks, package manager configs, etc; no production code change
  - 참고: [Udacity Git Commit Message Style Guide](https://udacity.github.io/git-styleguide/)  

### 4. 기능 정리  
1. 수취 국가에 따라 환율을 보여준다. -> api 요청  
2. 수취 국가, 송금액에 따라 수취 금액을 보여준다. -> 기존 데이터를 이용해 연산  
    * free plan은 일 단위로 업데이트 되기 때문에 불필요한 api 요청을 줄이는 것이 좋을 것으로 판단  
    * TODO 언제 업데이트 되는지 시점을 확인해서 활용하면 좋을 것 같다. 
      (요청 후 24시간 경과 시점인지, 매일 0시 기준인지)  

### 5. 기본 구조 설계  
* Dto
  * RequestDto
    수취국가
    송금액

  * CurrencyDto
    환율
* Controller
  * IndexController
  * CurrencyApiController
      public CurrencyDto 환율가져오기 (RequestDto)

* Service
  * CurrencyService
      public CurrencyDto 환율가져오기 
  * 다른 API를 사용하게 되는 경우를 고려해서 Interface를 만들고 구현하도록 함


### Today's Error 1. 톰캣 포트 충돌
- 문제: 톰캣 기본 포트 8080를 다른 프로세스가 사용하고 있어서 충돌 발생
- 해결: 해당 프로세스를 종료 
```java
org.apache.catalina.LifecycleException: Protocol handler start failed
    at org.apache.catalina.connector.Connector.startInternal(Connector.java:1008) ~[tomcat-embed-core-9.0.19.jar:9.0.19]
    at org.apache.catalina.util.LifecycleBase.start(LifecycleBase.java:183) ~[tomcat-embed-core-9.0.19.jar:9.0.19]
    at org.apache.catalina.core.StandardService.addConnector(StandardService.java:226) [tomcat-embed-core-9.0.19.jar:9.0.19]
    at org.springframework.boot.web.embedded.tomcat.TomcatWebServer.addPreviouslyRemovedConnectors(TomcatWebServer.java:259) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.boot.web.embedded.tomcat.TomcatWebServer.start(TomcatWebServer.java:197) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.startWebServer(ServletWebServerApplicationContext.java:311) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.finishRefresh(ServletWebServerApplicationContext.java:164) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:552) [spring-context-5.1.7.RELEASE.jar:5.1.7.RELEASE]
    at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:142) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:775) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:397) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:316) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:1260) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:1248) [spring-boot-2.1.5.RELEASE.jar:2.1.5.RELEASE]
    at com.jaehee.currencycalculator.CurrencyCalculatorApplication.main(CurrencyCalculatorApplication.java:10) [classes/:na]
Caused by: java.net.BindException: Address already in use: bind
    at sun.nio.ch.Net.bind0(Native Method) ~[na:1.8.0_191]
    at sun.nio.ch.Net.bind(Net.java:433) ~[na:1.8.0_191]
    at sun.nio.ch.Net.bind(Net.java:425) ~[na:1.8.0_191]
    at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:223) ~[na:1.8.0_191]
    at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:74) ~[na:1.8.0_191]
    at org.apache.tomcat.util.net.NioEndpoint.initServerSocket(NioEndpoint.java:239) ~[tomcat-embed-core-9.0.19.jar:9.0.19]
    at org.apache.tomcat.util.net.NioEndpoint.bind(NioEndpoint.java:213) ~[tomcat-embed-core-9.0.19.jar:9.0.19]
    at org.apache.tomcat.util.net.AbstractEndpoint.bindWithCleanup(AbstractEndpoint.java:1116) ~[tomcat-embed-core-9.0.19.jar:9.0.19]
    at org.apache.tomcat.util.net.AbstractEndpoint.start(AbstractEndpoint.java:1202) ~[tomcat-embed-core-9.0.19.jar:9.0.19]
    at org.apache.coyote.AbstractProtocol.start(AbstractProtocol.java:568) ~[tomcat-embed-core-9.0.19.jar:9.0.19]
    at org.apache.catalina.connector.Connector.startInternal(Connector.java:1005) ~[tomcat-embed-core-9.0.19.jar:9.0.19]
    ... 14 common frames omitted
    ```
- 참고: [[TOMCAT] 톰캣 시작시 포트 충돌 에러](https://dololak.tistory.com/152)


