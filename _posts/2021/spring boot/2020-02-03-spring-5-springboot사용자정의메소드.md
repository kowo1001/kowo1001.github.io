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

## Controller란?
- Controller에 대해 간단히 말하자면 MVC에서 C에 해당 하며 주로 사용자의 요청을 처리 한 후 지정된 뷰에 모델 객체를 넘겨주는 역할을 한다.

1)  @Controller
 - Controller의 역할을 수행 한다고 명시(해당 클래스를 Controller로 사용한다고 Spring FrameWork에 알린다.)

   필요한 비즈니스 로직을 호출하여 전달할 모델(Model)과 이동할 뷰(View) 정보를 DispatherServlet에 반환 한다.

 - Bean으로 등록

 - @Component의 구체화 된 어노테이션

 
 ##  @Controller와 @RestController의 차이
@Controller와 @RestController의 차이를 설명한다.

Spring MVC에서 컨트롤러 클래스에 어노테이션으로 @Controller 또는 @RestController을 붙인다.

@Controller는 주로 Web 페이지의 컨트롤러에서 사용한다.
Web 페이지용 컨트롤러는 JSP나 템플릿 엔진 View로 전환 응답의 HTML을 생성하기 때문에 기본적으로 메소드의 반환 값은 View 전환 대상을 지정하는 데 사용한다.

@RestController는 Json이나 XML 등을 반환 WebAPI 용 컨트롤러로 사용한다.
이것은 View로 전환하지 않기 때문에 메소드의 반환 값은 응답(response)의 내용(content)이 된다.

## @RequestMapping
1)  @RequestMapping

 - 요청에 대해 어떤 Controller, 어떤 메소드가 처리할지 맵핑하기 위한 어노테이션

 - 클래스나 메서드 선언부에 @RequestMapping과 함께 URL을 명시하여 사용한다.

 -  viewName 생략시 @RequestMapping의 path로 설정한 URL이 default viewName
 
## RequestMapping 속성들
1) value(String[])  : URL 값
```java
/* EX) */
@RequestMapping(value="/login")
@RequestMapping("/login") 
 ```

2) method (RequestMethod[]) : HTTP Request 메소드 값

 - GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE

```java
/* EX1) */
@RequestMapping(value="/login", method=@RequestMethod.GET)
/* EX2) */
@RequestMapping(value="/login", method=@RequestMethod.POST)
 ```
**※ Spring4.3 이후 ex1), ex2)는 다음과 같이 쓸수 있다.**


    ex1) @GetMapping("/login")

        == @RequestMapping("/login", method=@RequestMethod.GET)

    ex2) @PostMapping("/login")

    == @RequestMapping("/login", method=@RequestMethod.POST)


**@GetMapping : @RequestMapping(method = RequestMethod.GET) 의 축약형으로써, 애너테이션만 보고 무슨 메소드 요청인지 바로 알아볼 수 있다.**
 

3) params(String[]) : HTTP Request 파라미터

① @RequestParam : 사용자가 원하는 매개변수에 값을 매핑하기위해 사용한다.
```java
/* EX1) */
@PostMapping("/member")
public String member(@RequestParam String name, @RequestParam Int age)
```
여기서 @ReauestParam은 생략 가능하다. 사용자가 입력한 key값과 매개변수의 이름을 비교하여 값을 넣어주기 때문이다. 결국 다음의 ex2)와 ex1)은 동일한의미다.

```java
/* EX2) */
@PostMapping("/member")
public String member(String name, Int age)
 ```

② @PathVariable : url 경로를 변수화하여 사용할 수 있도록 해준다.
```java
@RequestMapping("/member/{name}/{age}")
public String member(@PathVariable("name") String name, @PathVariable("age") String age)
 ```
=> RequestMapping의 {name}과 PathVariable 의 String name을 매핑 하여 준다.

 

그리고 잘 사용해보진 않지만 다음과 같은 속성도 존재 한다.

 

4) consumes(String[]) : Request Body에 담는 타입을 제한할 수 있다.

    ex) @PostMapping("/login", consumes="application/json")

헤더에 application/json이 존재 해야 처리한다.



