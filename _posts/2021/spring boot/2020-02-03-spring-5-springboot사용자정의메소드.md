---
title: Spring-(1) SpringBoot 사용자정의메소드
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

## 사용자 정의 검색 메소드
사용자 정의 검색 메소드 추가 구현 가능[쿼리 메소드]
1. 네이밍 규칙
- find엔티티명By(타입변수명) 또는 findBy변수명(타입 변수명)
- "select * from 엔티티명 where 컬럼명=데이터" 문장 자동 생성
	
2. 검색 데이터가 포함(like 연산자) 조건의 명명 규칙
- findBoardByTitleContaining
- "select * from board where title like %데이터%" 자동 생성
  
3.예시
- title에 맞게 제목의 게시물 검색(Board 엔티티)
findBoardByTitle()
findByTitle()
select * from board where title=?

## Defining Query Methods(Query Creation)
https://docs.spring.io/spring-data/jpa/docs/2.1.11.RELEASE/reference/html/#jpa.query-methods

## Spring Boot Starters 재설정 방법
pom.xml 오른쪽 마우스 클릭 - Spring - Edit Spring Boot Starters - 설정파일 재설정 가능

## JSP 사용방법
jsp를 Spring Boot 구조에선 어떻게 어디에 개발해야 하는지에 대한 학습
jsp - ViewResolver setting
src/main/resources -> application.properties에 jsp를 추가하기 위한 설정 코드 작성

**spring.mvc.view.prefix=/WEB-INF/views/**
**spring.mvc.view.suffix=.jsp**


## HTML, CSS 사용방법
html를 Spring Boot 구조에선 어떻게 어디에 개발해야 하는지에 대한 학습
src/main/resources -> static 폴더  -> 하단에 index.html 생성 
src/main/resources/static/*.html, *.css, *.js, image 등으로 구성-> src/main/webapp/ 경로와 동기화시켜주기

## @RequestBody 역할
- @RequestBody => HTTP 요청 몸체를 자바 객체로 변환
- @RestController 사용시 client가 입력하는 데이터를 JSON 포멧으로 수용할 때 필수
- @RequestBody 애노테이션을 이용하면 HTTP 요청 Body를 자바 객체로 전달받을 수 있다.
- 클라이언트가 전송하는 Http 요청의 Body 내용을 Java Object로 변환시켜주는 역할.
- 그렇기 때문에 Get방식의 메소드에 @RequestBody를 활용하는 것은 적합하지 않다.
- @RequestBody는 Json이나 XML같은 형태의 data를 jackson등의 MessageConverter를 활용하여 Java Object로 변환한다.


## @ResponseBody 역할
- @ResponseBody => 자바 객체를 HTTP 응답 몸체로 변환
- @RequestMapping 기반의 서비스 메소드에서 jsp 등을 거치지 않고 메소드 반환값으로 client에게 데이터 응답시 필수 사용
- @GetMapping 등의 rest api 기반의 애노테이션으로 선언된 서비스 메소드엔 코딩 불필요
- java 객체를 HTTP 요청의 body 내용으로 매핑하는 역할.
- VO 객체를 JSON으로 바꿔서 HTTP body에 담는 스프링 어노테이션
- 메서드의 return 값을 HTTP Response의 body에 담는 역할을 한다.


## 참고
src -> main -> webapp -> WEB-INF 폴더 생성 - views 폴더 생성 
views 폴더 왜 생성했는지 ?

@RequestBody,@ResponseBody  내용 참고
https://spring.io/guides/tutorials/rest/
https://2ham-s.tistory.com/294

Spring 실행이 안되는 경우 아래 코드 pom.xml에 추가
```xml
<dependency>
<groupId>com.jslsolucoes</groupId>
<artifactId>ojdbc6</artifactId>
<version>11.2.0.1.0</version>
</dependency>

<!-- dependencies와 build 사이에 아래 코드 넣어주기 -->
<repositories>
<repository>
<id>oracle</id>
<name>ORACLE JDBC Repository</name>
<url>https://maven.atlassian.com/3rdparty/</url>
</repository>
</repositories>
```


