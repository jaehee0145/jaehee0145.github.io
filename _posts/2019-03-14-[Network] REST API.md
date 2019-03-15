---
title: "[Network] REST API"
layout: single
categories:
  - Network
Tags:
  - Network, REST API,

---
REST API

## REST란?  
> REST(REpresentational State Transfer)는 WWW과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 아키텍처의 한 형식이다. - 위키백과     


* REST는 네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나이다.  
* REST는 기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다.  
* API 설계의 중심에 자원(Resource)이 있고 HTTP Method를 통해 자원을 처리하도록 설계하는 것이다.  

## REST가 필요한 이유  
* 애플리케이션 분리와 통합을 쉽게 하기 위해서  
* 다양한 클라이언트(브라우저, 모바일 디바이스)를 처리하기 위해서  



## REST 구성 요소  
1. 자원(Resource): URI  
  * 모든 자원에 고유한 ID가 존재하고, 이 자원은 Server에 존재한다.  
  * 자원을 구별하는 ID는 '/groups/:group_id'와 같은 HTTP URI다.
  * Client는 URI를 이용해서 자원을 지정하고 해당 자원의 상태에 대한 조작을 Server에 요청한다.  
2. 행위(Verb): HTTP Method  
  * HTTP 프로토콜의 Method를 사용한다.  
  * HTTP 프로토콜은 GET,POST, PUT, DELETE와 같은 메서드를 제공한다.  
3. 표현(Representation of Resource)  
  * Client가 자원의 상태에 대한 조작을 요청하면 Server는 이에 적절한 응답(Representation)을 보낸다.  
  * REST에서 하나의 자원은 JSON, XML, RSS 등 여러 형태의 Representation으로 나타낼 수 있다.  
  * JSON 혹은 XML을 통해 데이터를 주고 받는 것이 일반적이다.  


## REST 6가지 원칙  
1. Uniform Interface(인터페이스 일관성)    
  * URI로 지정한 Resource에 대한 조작을 통일되고 한정된 인터페이스로 수행한다.  
  * HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.  
    - 특정 언어나 기술에 종속되지 않는다.  
2. Server-Client 
  * 자원이 있는 쪽이 Server, 자원을 요청하는 쪽이 Client가 된다.  
    * REST Server: API를 제공하고 비즈니스 로직 처리 및 저장을 담당  
    * Client: 사용자 인증이나 context(세션, 로그인 정보) 등을 직접 관리  
  * 서로 간 의존성이 줄어든다.  
3. Stateless(무상태)
  * HTTP 프로토콜과 마찬가지로 무상태성이 특징이다.  
  * Client의 Context를 Server에 저장하지 않는다.  
    - 즉, 세션과 쿠키와 같은 context 정보를 신경쓰지 않아도 되므로 구현이 단순해진다.  
  * Server는 각각의 요청을 완전히 별개의 것으로 인식하고 처리한다.  
    - 각 API 서버는 Client의 요청만을 단순 처리한다.  
    - 즉, 이전 요청이 다음 요청의 처리에 연관되어서는 안된다.  
    - 물론 이전 요청이 DB를 수정하여 DB에 의해 바뀌는 것은 허용한다.  
    - Server의 처리 방식에 일관성을 부여하고 부담이 줄어들며, 서비스의 자유도가 높아진다.  
4. Cacheable(캐시 처리 기능)
  * 웹 표준 HTTP 프로토콜을 그대로 사용하므로 웹에서 사용하는 기존의 인프라를 그대로 활용할 수 있다.  
    - 즉, HTTP가 가진 가장 강력한 특징 중 하나인 캐싱 기능을 적용할 수 있다.  
    - HTTP 프로토콜 표준에서 사용하는 Last-Modified 태그나 E-Tag를 이요하면 캐싱 구현이 가능하다.  
  * 대량의 요청을 효율적으로 처리하기 위해 캐시가 요구된다.  
  * 캐시 사용을 통해 응답시간이 빨라지고 REST Server 트랜잭션이 발생하지 않기 때문에 전체 응답시간, 성능, 서버의 자원 이용률을 향상시킬 수 있다. 
5. Layered System(계층화)
  * Client는 REST API Server만 호출한다.  
  * REST Server는 다중 계층으로 구성될 수 있다.  
    - API Server는 순수 비즈니스 로직을 수행하고 그 앞단에 보안, 로드밸런싱, 암호화, 사용자 인증 등을 추가하여 구조상의 유연성을 줄 수 있다.  
    - 또한 로드밸런싱, 공유 캐시 등을 통해 확장성과 보안성을 향상시킬 수 있다. 
    - PROXY, 게이트웨이 같은 네트워크 기반의 중간 매체를 사용할 수 있다.  
6. Code-On-Demand(optional)  
  * Server로부터 스크립트를 받아서 Client에서 실행한다.  
  * 반드시 충족할 필요는 없다.  

## REST API란?  
* API(Application Programming Interface)  
  - 데이터와 기능의 집합을 제공하여 컴퓨터 프로그램간 상호작용을 촉진하며, 서로 정보를 교환 가능하도록 하는 것  
* REST API  
  - REST 기반으로 서비스 API를 구현한 것  
  - 최근 OpenAPI, 마이크로서비스(하나의 큰 애플리케이션을 여러 개의 작은 애플리케이션으로 쪼개어 변경, 조합이 가능하도록 만든 아키텍처) 등을 제공하는 업체 대부분은 REST API를 제공한다.  

## REST API 특징  
* 사내 시스템도 REST기반으로 시스템을 분산해 확장성과 재사용성을 높여 유지보수 및 운용을 편리하게 할 수 있다.  
* REST는 HTTP 표준을 기반을로 구현하므로, HTTP를 지원하는 프로그램 언어로 클라이언트, 서버를 구현할 수 있다.  
* 즉, REST API를 제작하면 델파이 클라이언트 뿐 아니라 자바, C#, 웹 등을 이용해 클라이언트를 제작할 수 있다.  



---
참고  
[[Network] REST란? REST API란? RESTful이란?](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html)  
[REST API 제대로 알고 사용하기](https://meetup.toast.com/posts/92)   

 
