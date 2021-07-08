---
title: Spring-(1) SpringBoot 설치 및 시작
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Spring
toc: true
toc_sticky: true
toc_label: 목차
---



## Restful 
- 쿠키를 통한 세션 트랙킹 같은 별도의 전송 계층 없이 전송하기 위한 아주 간단한 인터페이스를 말한다.

## Rest 개념
URL : https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html
참고해서  Rest 개념 잡기

## Spring Boot 시작 및 설치
spring boot -> spring starter Project -> Packaging: Jar ->Spring boot Version : 2.3.8 -> 왼쪽에 SQL -> Spring Data JPA 차후에 쓸 건데 지금은 선택 안함 ->
왼쪽에 Web - Spring Web -> 왼쪽에 Developer Tools -> Spring Boot DevTools, Lombok 체크 -> configuration file 엑박 뜬다 ! ->demo 삭제(delete)

spring boot -> spring starter Project -> Packaging: War,Type Maven: Javerversion 8 , Group:playdata, Package: io.playdata  ->Spring boot Version : 2.3.8 -> 왼쪽에 SQL -> Spring Data JPA 차후에 쓸 건데 지금은 선택 안함 ->
왼쪽에 Web - Spring Web -> 왼쪽에 Developer Tools -> Spring Boot DevTools, Lombok 체크 -> 성공!!

ServletInitializer 제거 
RunAs - Spring Boot App - 에러 발생시 - application.properties - server.port=80 작성 - RunAs - Spring Boot App - 성공!!


cmd창에서 curl http://127.0.0.1/getdata 명령어를 통해 서버에 있는 데이터 확인 가능 

## Postman 사용
Postman 사용 - '+' 버튼 클릭 - Get - http://127.0.0.1/getdata - Send 
Body - row 선택시 - 데이터를 입력할 수 있음 - JSON 포맷 형식으로 변경 - 데이터 입력


## Spring Boot 장점
- 라이브러리 관리 자동화
- 설정의 자동화
- 라이브러리 버전 자동 관리
- 테스트 환경과 내장 톰캣
- 독립적으로 실행가능한 JAR or WAR

## apication.properties
- 프로젝트 전체에서 사용할 프로퍼티 정보들을 관리하고 설정하는 파일 
- 필요한 프로퍼티들을 등록하면 복잡한 자바 코드를 수정하지 않고도 애플리케이션의 동작을 변경할 수 있음

## src/main/resources 
자바소스가 아닌 xml이나 properties 파일

## spring boot banner 만들기
src/main/resources 하단에 banner.txt 만들기 - 원하는 정보 입력 - run as - 출력 
참고 URL : https://eblo.tistory.com/53

## 주요 Annotation
@Controller 
- subController로 활용됨 
- JSP 응답

@RestController
- subController로 활용됨 
- 메소드 응답

Spring Bean으로 등록하는 애노테이션
- @Component
- @Repository
- @Service
- @Controller
- @RestController

## Project Packaging 하기
프로젝트 오른쪽 마우스 클릭 - Run As - 8 Maven install 클릭
step05_bootBasic-0.0.1-SNAPSHOT.war - Show in local Terminal - Terminal - 하단에 

## packaging 파일 실행해보기 
터미널창 오픈 -> 다음 명령어 입력 -> 터미널창 정상 실행 확인 -> 브라우저로 요청 및 응답 확인
java -jar step05_bootBasic-0.0.1-SNAPSHOT.war

## Spring Data JPA란 ?
Spring Boot에서 JPA를 쉽게 사용할 수 있도록 지원하는 모듈

## Repository interface 작성
- 실제 DB와 연동
- CRUD 기능을 처리할 Repository
- DAO와 동일한 개념
- 개발방법 
1) Spring에서 제공하는 Repository 중 하나를 상속
2) Spring Data JPA 사용시 별도의 하위 클래스
3) 구현 없이 interface만 정의
Spring Boot가 내부적으로 interface에 대한 구현 객체를 자동으로 생성


## REST란?
웹에 존재하는 모든 자원에 고유한 URI를 부여해 활용하는 것
자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미한다.
GET/POST/PUT/DELETE 등의 HTTP 메소드로 제어하자는 개념
PUT은 업데이트(update)
Delete은 삭제 

## REST API의 정의
REST 기반으로 서비스 API를 구현한 것
최근 OpenAPI(누구나 사용할 수 있도록 공개된 API: 구글 맵, 공공 데이터 등), 마이크로 서비스(하나의 큰 애플리케이션을 여러 개의 작은 애플리케이션으로 쪼개어 변경과 조합이 가능하도록 만든 아키텍처) 등을 제공하는 업체 대부분은 REST API를 제공한다.

## API(Application Programming Interface)란
데이터와 기능의 집합을 제공하여 컴퓨터 프로그램간 상호작용을 촉진하며, 서로 정보를 교환가능 하도록 하는 것

## Http Method 종류 및 특징
POST,GET,PUT,DELETE 4가지의 Method로 CRUD 수행
POST : POST를 통해 해당 URI를 요청하면 리소스를 생성 or 수정
GET : GET을 통해 해당 리소스 조회, 리소스를 조회하고 해당 도큐먼트에 대한 정보를 가져옴
PUT : 리소스 수정 or 생성
DELETE : 리소스 삭제

프로젝트 오른쪽 마우스 클릭 - Run As -  Maven clean클릭

spring boot -> spring starter Project -> Packaging: War,Type Maven: Javerversion 8 , Group:playdata, Package: io.playdata  ->Spring boot Version : 2.3.8 -> 왼쪽에 SQL -> Spring Data JPA , Oracle Driver 체크 ->
왼쪽에 Web - Spring Web -> 왼쪽에 Developer Tools -> Spring Boot DevTools, Lombok 체크 -> 성공!! 


application.properties에 아래 코드와 같이 작성하기
```properties
server.port=80

#DataSource Setting
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
spring.datasource.url=jdbc:oracle:thin:@127.0.0.1:1521:xe
spring.datasource.username=SCOTT
spring.datasource.password=TIGER

#JPA Setting
spring.jpa.hibernate.ddl-auto=create
#spring.jpa.hibernate.ddl-auto=none
spring.jpa.generate-ddl=false
spring.jpa.show-sql=true
#spring.jpa.properties.hibernate.format_sql=true
spring.jpa.database=oracle
spring.jpa.database-platform=org.hibernate.dialect.OracleDialect

# Logging Setting
logging.level.org.hibernate=info
```

