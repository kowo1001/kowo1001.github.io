---
title: Servlet을 알아보자-(3) ServletContext
---

## ServletContext란?
ServletContext는 톰캣 컨테이너(서버) 실행시 각 Context(Web Application)마다 한개의 ServletContext 객체를 생성한다.
그리고 톰캣 컨테이너(서버)가 종료되면 ServletContext 객체도 소멸된다
ServletContext객체는 Web Application 내에 있는 모든 서블릿들을 관리하며 공통 자원이나 정보를 공유할 수 있게 도와주는 역할을 한다

## ServletContext 특징
- 서블릿과 톰캣 컨테이너(서버) 간의 연동을 위해 사용한다
- 컨텍스트(웹 애플리케이션)마다 하나의 ServletContext가 생성된다
- 서블릿끼리 자원(데이터)를 공유하는데 사용한다
- 톰캣 컨테이너(서버) 실행시 생성되고 컨테이너 종료시 소멸된다

## ServletContext 기능
- 자원 바인딩 
- 컨텍스트(웹 애플리케이션)에서 제공하는 설정 정보 제공
- 서블릿에서 파일 접근 기능
- 로그 파일 기능

ServletContext 객체는 Web application이 실행되면서 애플리케이션 전체의 공통 자원이나 정보를 미리 바인딩(binding) 해서 <br>
서블릿들이 공유하여 사용하게 된다

```java
import javax.naming.Context;
import javax.naming.InitialContext;
import javax.sql.DataSource;

// Web Application Server의 설정 정보 활용할 수 있는 객체 생성
Context initContext = new InitialContext();
Context envContext = (Context)initContext.lookup("java:/comp/env");

// jdbc/myoracle 라는 이름으로 매핑된 자원 활용하겠다는 의미
ds = (DataSource)envContext.lookup("jdbc/myoracle");
```
