---
title: "[Spring] JDBC vs Spring JDBC"
layout: single
categories:
  - Spring
  - Java

---

Learn about Spring :)  
    &nbsp;&nbsp;  

### JDBC(Java Database connectivity)  
- DB에 접근할 수 있도록 Java에서 제공하는 API
- 표준 SQL을 실행하는 메소드를 갖고 있기 때문에 DBMS에 의존하지 않는 개발이 가능하다.
- 단점  
  1) 쿼리 실행 전후에 필요한 코드가 있다.  
  &nbsp;ex) connection, preparedStatement, resultSet 등등  
        2) 예외 처리 코드가 필요하다.  
        3) 트랜잭션을 처리해야 한다.(Commit, rollback 등)  
        4) 이상의 코드가 반복된다.  
 &nbsp;&nbsp;

### Spring JDBC  
- JDBC의 단점을 보완하여 간결하게 사용할 수 있도록 제공하는 API
- Spring JDBC가 해주는 작업  
    1) Connection 열기와 닫기:  
       - Connection과 관련된 모든 작업을 알아서 진행  
       - 예외가 발생하면 모든 Connection 객체를 닫아준다.  
      &nbsp;&nbsp;  

    2) Statement 준비와 닫기: 
        - SQL 정보가 담긴 Statement 또는 PreparedStatement를 생성, 준비, 닫기      &nbsp;&nbsp;  

    3) Statement 실행:  
        - SQL이 담긴 Statement 실행  
        - 실행 결과는 다양한 형태로 가져올 수 있다.      &nbsp;&nbsp;  

    4) ResultSet Loop 처리 :  
       - ResultSet에 담긴 쿼리 실행 결과가 한 건 이상이면 Loop를 만들어서 반복      &nbsp;&nbsp;  

    5) Exception 처리와 반환:  
       - JDBC 작업 중 발생하는 모든 예외를 처리  
       - Checked Exception인 SQL Exception을 Runtime Exception인 DataAccessException 타입으로 반환      &nbsp;&nbsp;  

    6) Transaction 처리:  
        - Commit, rollback등 transaction과 관련된 작업을 알아서 진행      &nbsp;&nbsp;  


- Spring JDBC의 단점  
    1) 학습의 필요성  
    2) 선택의 어려움  
   동일한 작업에 대해 다양한 선택지를 제시하는 것이 장점이자 단점 → 1. 학습의 필요성      &nbsp;&nbsp;  

    ex) 스프링 부트 vs 스프링 프레임워크  
        xml 기반 의존성 vs 애너테이션 기반 의존성  
        리액티브 웹 vs 서블릿 웹  
        스피링 전용 애너테이션 vs 표준호환 애너테이션  
    
&nbsp;&nbsp;
&nbsp;&nbsp;

*** 

##### 참고

##### Spring JDBC https://smallgiant.tistory.com/13  
##### 스프링의 단점과 대안 https://www.bangseongbeom.com/spring-downsides-alternatives.html
