---
title: "[Web] Forward and Redirect"
layout: single
categories:
  - Web

---

Learn about Web :)  
    &nbsp;&nbsp;  
    
     

## Redirect와 Forward
현재 작업중인 페이지에서 다른 페이지로 이동하는 페이지 전환 기능

## Redirect
- 프로세스
    1) 클라이언트가 서버에 리소스를 요청
    2) 서버는 상태값 3XX와 함께 Recirect 주소를 응답
    3) 클라이언트는 새로운 주소로 다시 리소스를 요청
    4) 서버는 새로운 리소스를 응답

- 두 요청에 대해 내부 자원을 공유할 수 없다.
- 새로운 request와 response 객체가 생성된다. 
- URL의 변화가 생긴다.

## Forward
- 프로세스
    1) 클라이언트가 서버에 리소스를 요청
    2) 서버는 Web Container(Tomcat, Jboss등)에 의해 Servlet1 에서 Servlet2로 forward
    3) 서버는 최종적으로 Servlet2의 결과를 응답
    4) 클라이언트는 한번의 요청으로 응답을 받을 수 있다.

- 웹 브라우저에서 페이지의 이동을 알 수 없다. 
- Forward는 Web Container의 내부에서 이동하기 때문에 request와 response 객체를 공유할 수 있다. 

***

### 적용에 대한 부분은 잘 이해가 되지 않는다.
Redirect- 시스템(세션, DB, ...)에 변화가 생기는 요청(로그인, 회원가입, 글쓰기 등)   
Forward- 시스템에 변화가 생기지 않는 단순 조회 요청(글 목록 보기, 검색 등)    

***

#### 참고

https://nesoy.github.io/articles/2018-04/Redirect-Forward  
http://blog.naver.com/saintw/100165339381  
https://doublesprogramming.tistory.com/63  
 



