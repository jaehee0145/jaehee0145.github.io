---
title: "[Currency Converter] Day 3"
layout: single
categories:
  - Currency Converter
Tags:
  - Currency Converter

---
개발 일지  

### 1. 환율과 입금액으로 송금액 계산하는 기능  
- Service에서 구현  
- Controller에서 API 호출로 송금액 계산하는 기능 구현  
- index.html에서 ajax로 송금액 계산하는 화면 구현 

### 2. Refactoring 
- 외부 API 요청시 사용하는 AccessKey를 코드와 분리  
  -  AccessKey는 application.properties에 저장  
  -  Environment API를 이용해서 properties를 읽어서 사용  

- Method 이름 직관적으로 수정하고 기능에 대한 주석 추가

- 테스트 코드를 활용하니까 효율이 오른다. 매번 전체 애플리케이션을 구동시켜서 수동으로 테스트를 했는데 이제서야 테스트 코드를 왜 쓰는지 알겠다.  

### 3. Select Box 초기 선택값을 인식하지 않는 문제  
- Select Box에서 선택값이 변경되어야 API를 호출하도록 작성되어서 초기 선택값에 대한 환율을 바로 가져오지 못하는 문제  
- 해결: 수취 국가 이외 별도 초기값을 설정  

### 4. 환율, 수취 금액 표기 규칙에 맞게 출력  
- JavaScript 문법을 이용해서 간단히 처리  
- 서버에서 처리하는 것이 더 좋을지 확인이 필요  

### 5. README 작성  
- 각각의 요구사항에 대해 어떻게 구현했는지 작성 
- 추후 일별 개발일지 추가 예정  

### 6. Vue.js 프로젝트 생성해서 연동  
- Vue.js 프로젝트를 생성하고 프로젝트 빌드시 html, css,js 파일을 WAS가 접근 가능한 경로에 생성되도록 설정  

### 7. 기존 화면 코드를 Vue.js로 변경   
