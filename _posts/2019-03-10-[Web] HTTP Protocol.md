---
title: "[Web] HTTP Protocol"
layout: single
categories:
  - Web
Tags:
  - Web, Http Protocol,

---
HTTP Protocol  

## HTTP 프로토콜이란?  
- 웹 상에서 정보를 주고 받을 수 있는 프로토콜  
- 주로 HTML 문서를 주고 받을 때 사용  

- 클라이언트와 서버 사이에서 이루어진 요청/응답(Request/Response) 프로토콜  
  - 웹 브라우저(클라이언트)가 HTTP를 통해 서버로부터 웹 페이지나 그림 정보를 요청  
  - 웹 서버는 해당 요청에 응답하여 필요한 정보를 사용자에게 전달  


## HTTP 프로토콜의 역사  
- Hyper Text라는 용어는 1965년 제너두 프로젝트에서 테드 넬슨이 만들었다.  
- 팀 버너스 리와 그의 팀은 CERN에서 HTML뿐 아니라 웹 브라우저 및 텍스트 기반 웹 브라우저 관련 기술과 HTTP를 발명  
- 1989년 버너스 리는 "World Wide Web" 프로젝트를 제안  
- 문서화된 최초의 HTTP 버전은 HTTP V0.9 (1991년)   

## Message Fromat  
### 1. 요청 메세지
   클라이언트가 서버에게 보내는 메세지  
   ```
   GET / HTTP/1.1  
   Host: developer.mozilla.ort  
   Accept- Language: fr  
   ```  
  1) Request Line (Method / Path / Version of Protocol)  
  2) Headers  
  3) Empty line  
  4) Body  
    - Method : 클라이언트가 실행하고자 하는 동작을 정의  
              (GET, POST를 주로 사용)
    - Path: 가져오려는 리소스의 경로, Protocol, domain, 또는 TCP port 요소들을 제거한 리소스의 URL  
    - Headers: 서버에 추가 정보를 전달  
    - Body: POST와 같은 메소드의 경우 추가 메세지를 갖는다. 

### 2. 응답 메세지
    서버가 클라이언트에게 보내는 메세지  
    ```
    HTTP/1.1 200 OK  
    Date: Sat, 29 Dec 2018  
    ```  
    1) Response Line (version of Protocol/ Status Code / Status Message)  
    2) Headers  
    3) Empty Line  
    4) Body  

      - Status Code: 요청의 성공 여부와 그 이유를 나타내는 코드  
      - Status Message: 상태 코드에 대한 설명 메세지  


---
## HTTPS Protocol 이란?  
> HTTPS(HyperText Transfer Protocol over Secure Socket Layer)는 HTTP의 보안이 강화된 버전이다.  
HTTPS는 소켓 통신에서 일반 텍스트를 이용하는 대신에, SSL이나 TLS 프로토콜을 통해 세션 데이터를 암호화한다. 

  

---
참고  
[우리 모두의 백과사전, 위키백과](https://ko.wikipedia.org/wiki/HTTP)