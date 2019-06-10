---
title: "[Currency Converter] Day 4"
layout: single
categories:
  - Currency Converter
Tags:
  - Currency Converter

---
개발 일지  

### 1. 버그
- frontend - index.html title을 바꾸면 build가 되지 않는다.  


### 2. 송금액 validation 처리  
- back: validation annotation을 이용  
- front: JavaScript로 값을 범위 내의 값인지 확인하고 아니면 에러 메세지 발생  

### 3. 외부 API 확인  
- 외부 API에 문제, 변동 사항이 발생할 가능성이 있으므로 이를 대비하는 장치가 필요하다.  
- 현재는 source가 "USD"인 환율 정보를 제공하는데 문제가 생겨 다른 source의 정보를 제공하는 경우를 대비해 source를 확인하고 아닌 경우 예외를 발생시킨다.  

### 4. Exception Handler 구현  
- @ControllerAdvice를 이용해서 Controller에서 발생하는 Exception을 한꺼번에 처리  
- 개발하면서 발생했던 NullpointerException과 외부 API로 인해 발생 가능성이 있는 RestClientException을 처리하는 코드 작성  

