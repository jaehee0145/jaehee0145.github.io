---
title: "[Web] Cookie and Session"
layout: single
categories:
  - Web

---

Learn about Web :)  
    &nbsp;&nbsp;  
  &nbsp;&nbsp;  

  
## Cookie와 Session이 필요한 이유  

HTTP 프로토콜의 특성 때문에 Cookie와 Session이 필요하다.  
    &nbsp; 1) Connectionless : 클라이언트와 서버가 요청 응답을 마치면 연결을 끊는다.  
    &nbsp; 2) Stateless : 연결이 끝나면 상태 정보를 유지하지 않는다.
    
HTTP 프로토콜을 사용하면서 Server가 Client를 식별하기 위해 Cookie와 Session이 필요하다.   
        (쿠키와 세션이 없다면 어떤 페이지를 이동할때마다 로그인을 다시 해야 한다)

  

## Cookie
- 클라이언트 로컬에 저장되는 키와 값이 들어있는 데이터 파일
- 이름, 값, 만료 날짜, 경로 정보가 들어있다.
- 일정 시간 동안 데이터를 저장할 수 있다.

- 프로세스
    1) 브라우저에서 웹페이지 접속
    2) 클라이언트가 요청한 웹페이지를 받으면서 쿠키를 클라이언트 로컬에 저장 (Response - header field인 set-cookie)
    3) 클라이언트가 재 요청시 Request Header에 쿠키값을 포함시켜 전송
    4) 지속적으로 로그인 정보를 가지고 있는 것처럼 사용

## Session
- 웹 브라우저를 통해 웹 서버에 접속한 이후로 브라우저를 종료할 때까지 유지되는 상태
- 클라이언트가 요청을 보내면, 해당 서버의 엔진이 클라이언트에게 Session ID를 부여

- 프로세스
    1) 클라이언트가 서버에 접속시 Session ID를 발급하고 ID와 매핑 정보를 서버 메모리에 저장
    2) 서버에서는 클라이언트에게 발급한 세션 ID를 쿠키를 사용해 저장
    3) 클라이언트가 다시 접속할 때, 이 쿠키를 이용해서 Session ID를 서버에 전달

- Session을 구별하기 위해 ID가 필요하고 해당 ID를 쿠키에 저장  
    웹 페이지 요청과 함께 쿠키값을 전달하므로 서버에서 ID를 인식하고 처리

## Cookie와 Session의 차이
1) 저장 위치
    쿠키는 클라이언트에 파일로 저장, 세션은 서버에 저장

2) 보안
    쿠키는 로컬에 저장되기 때문에 보안에 취약하지만  
    세션은 쿠키를 이용해서 Session ID만 저장하고 서버에서 처리하기 때문에 쿠키에 비해 보안성이 높음

3) 라이프 사이클
    쿠키는 만료시간이 있지만 파일로 저장되기 때문에 브라우저를 종료해도 유지  
    세션은 브라우저가 종료되면 삭제
  &nbsp;  


  ***

## From Wiki
1. Cookie  
An HTTP cookie is a small piece of data sent from a website and stored on the user's computer by the user's web browser while the user is browsing. Cokkies were desined to be a reliable mechanism for websites to remember stateful information (such as items added in the shopping cart in an online store) or to record the user's browsing activity (including clicking particular buttons, logging in, or recording which pages were visited in the past). They can also be used to remember arbitary pieces of information that the user previously entered into form fields such as names, addresse, passwords, and credit card numbers.

2. Session  
In web analytics, a session, or visit is a unit of measurement of a user's actions taken within a period of time or with regard to completion of a task. 

***
#### 참고  
https://jeong-pro.tistory.com/80  
http://ledgku.tistory.com/72  
http://ledgku.tistory.com/72V  


