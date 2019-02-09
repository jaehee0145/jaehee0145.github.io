---
title: "[Web] Servlet"
layout: single
categories:
  - Web

---

Learn about Web :)  
  &nbsp;&nbsp;  

### Servlet Container의 동작 과정
1. 브라우저에서 서버에 연결
2. 요청 정보(context path, path) 전달
3. 객체 생성 
    HttpServletRequest
    HttpServletResponse
4. Context path에 해당하는 Web Application을 찾는다.  
5. 해당 Web Application에서 path에 해당하는 resource를 찾는다.  
6-1. 정적 컨텐츠를 요청한 경우  
    defaultServlet이 resource(html/css)를 실행  
6-2. 동적 컨텐츠를 요청한 경우
    JSP, Servlet이 실행
7. 실행된 결과를 브라우저에 응답

### servlet
- 연결: 브라우저 - HttpServletRequest - servlet filter(0개 이상의 필터가 존재)- servlet  
- 모두 servlet이라고 할 수 있다.  
    &nbsp; resource(html/css) - default servlet 사용  
    &nbsp; JSP - servlet 기술 사용  

- HttpServlet (추상클래스)를 상속받는 servlet을 생성
- 오버라이딩을 위한 메서드를 갖고 있다. (init, destroy, service 등)

- servlet을 생성해서 오버라이딩하면 클라이언트가 아니라  
   was가 이를 호출한다.   
    servlet의 life cycle을 잘 파악해야 한다. 


### path- Servlet
1. path를 이용해서 servlet을 찾는다.  
2-1. 메모리에 없는 경우  
    인스턴스를 생성하고 init()으로 초기화  
2-2. 메모리에 있는 경우  
    service() 실행하여 결과를 브라우저에 전달  

- WAS는 Thread를 가지고, Servlet은 공유 객체이므로 필드 선언하지 않는 것이 안전하다. 

#### HttpServlet의 service()  
http method에 따라서 동작하도록 구현되어 있다.  
if (Get) { doGet() }  
if (POST) { doPost() }  

- path가 같은데 http method에 따라 동작하도록 구현하고 싶으면  
  &nbsp;&nbsp; service() 대신 doGet(), doPost()를 오버라이딩
- http method에 상관없이 path에 따라 동작하도록 구현하고 싶으면  
  &nbsp;&nbsp; service() 오버라이딩



***
#### 참고   
서블릿 컨테이너의 동작 과정  
http://blog.naver.com/PostView.nhn?blogId=elren&logNo=220786145135 


