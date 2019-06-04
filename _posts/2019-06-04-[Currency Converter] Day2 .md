---
title: "[Currency Converter] Day 2"
layout: single
categories:
  - Currency Converter
Tags:
  - Currency Converter

---
개발 일지  

### 1. Annotation 설정  
- 1. @RestContoller  
  - @RestController는 데이터를 리턴하는 것이 주용도   
  - @Controller는 view(화면)를 리턴하는 것이 주용도  
    - @ResponseBody를 사용해서 객체를 리턴할 수도 있음  
- 참고: [@Controller VS @RestController](https://doublesprogramming.tistory.com/105)  

- 2. @RequestMapping  
  - 클라이언트가 URL을 통해 전달한 요청을 어떤 클래스, 어떤 메서드가 처리할지 매핑  

- 3. @RequiredArgsConstructor  
  - final이나 @NotNull인 객체만 파라미터로 받는 생성자를 생성  

### 2. 외부 API 호출 기능 
- service layer에서 구현  
- 다른 API를 사용하게 되는 경우에도 CurrencyDto를 가져오는 메서드를 반드시 구현하도록 Interface를 만들고 이를 구현하도록 함  
  
- RestTemplate객체를 만들고, 요청 URI와 응답 객체로 데이터 수신  
- 간단하게 API 요청 url을 String으로 생성해서 구현
  
- TODO. url에 Access key가 포함되어 있으므로 코드와 분리할 예정  


### 3. Test Code 작성  
- Annotation 설정  
  - @SpringBootTest, @RunWith()
- 참고: [Junit을 이용한 단위테스트](https://epthffh.tistory.com/entry/Junit%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EB%8B%A8%EC%9C%84%ED%85%8C%EC%8A%A4%ED%8A%B8)  
[Spring Boot Test](https://meetup.toast.com/posts/124)  

#### Error 1. RestTemplate을 bean으로 등록하지 않음  
```java
Description:
Parameter 0 of constructor in com.jaehee.currencyconverter.service.CurrencyAPIServiceImpl required a bean of type 'org.springframework.web.client.RestTemplate' that could not be found.

Action:
Consider defining a bean of type 'org.springframework.web.client.RestTemplate' in your configuration.
```
- 해결  
  - SpringBoot 1.4 이상부터 RestTemplateBuilder를 이용해서 정의해야 함  
  - RestTemplate은 다른 클래스에서도 사용할 수 있으므로 WebConfig클래스에서 별도로 빈으로 생성함  

- 참고: [How to autowire RestTemplate using annotations](https://stackoverflow.com/questions/28024942/how-to-autowire-resttemplate-using-annotations)  


### 4. 화면 구현  

- index.html 작업

#### Error. pom.xml 파일이 업데이트 되지 않음  
- 문제: webjars를 이용하기 위해 dependency를 추가했는데 변경 내용을 인식하지 않음  
- 해결: 프로젝트에서 maven - reimport  
- 느낀 점: 한 시간은 낑낑 거린 것 같은데 이렇게 쉽게 해결되다니.. 에러를 해결할때도 체계적으로 접근해야 한다.  

### 5. 수취 국가에 따라 환율 정보를 가져오는 기능 완성  
- 선택한 수취국가를 파라미터로 넘기고 GET 요청을 보냄
- 서비스 레이어에서 외부 API에 요청을 보내고 dto 형식으로 데이터를 받음  
- 데이터 중에서 파라미터로 넘긴 수취 국가에 해당하는 환율을 리턴  
- 자바스크립트 문법을 이용해서 환율을 소수점 두 자리까지만 보여주도록 함  

