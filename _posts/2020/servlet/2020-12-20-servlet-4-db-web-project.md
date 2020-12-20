---
title: Servlet-(4) DB 다운 방지 처리 및 Web Project 설정
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Servlet&JSP
toc: true
toc_sticky: true
toc_label: 목차
---

## DB 다운 방지 처리 기술
### DB의 동시 접속자 수를 제어하는 기술
- Connection 개수를 조절한다
- Connection pool은 생성, 삭제 개념이 아닌 재사용 개념이다

### 적용방식
- 처음부터 Connection 객체 생성해서 대기상태로 유지
- Client가 최대 접속자들에 한해서 생성후 접속 해제하면 Connection 삭제가 아닌 Connection들만 저장된 별도의 메모리에 반환
- 새로운 Client는 재사용하는 개념
- Web Application Server와 DB Server 구분한다 (Connection 개수 제한은 WAS의 설정 파일로 관리)

### Connection Pool 설정 방식
- 모든 서버에 동일하게 반영 ( 서버마다 설정방식이 다름 -벤더별 상이함)
- 모든 웹 프로젝트별 동일한 방식으로  WEB-INF/web.xml 에 설정 
- DB정보와 접속자수 제어의 설정 정보(벤더에 따라 다른 방식)를  META-INF/context.xml 에 설정
- 자바소스에서 JNDI라는 이름(별칭)으로 자원활용하는 스펙 (모든 소스에 동일한 표준화된 코드) 
## Web Project 설정
### 1. 설정 파일 : WEB-INF/web.xml
설정 정보
- url에 file명 기술 없이도 자동 실행되는 intro 파일명 무시
```xml
  <welcome-file-list>
    <welcome-file>index.html</welcome-file>
  </welcome-file-list>
```
- jdbc/myoracle와 같이 name 모두 같게 설정

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" id="WebApp_ID" version="3.1">
  <display-name>step05_CP</display-name>
  <welcome-file-list>
    <welcome-file>index.html</welcome-file>
  </welcome-file-list>
  <resource-ref>
    <description>Oracle Datasource example</description>
    <res-ref-name>jdbc/myoracle</res-ref-name>
    <res-type>javax.sql.DataSource</res-type>
    <res-auth>Container</res-auth>
  </resource-ref>
</web-app>
```
### 2. 설정파일: META-INF/context.xml

- DB 정보와 접속자수 제어의 설정 정보 (벤더에 따라 다름)
- 최대 접속 client 수를 20명으로 제한
- jdbc/myoracle와 같이 name 모두 같게 설정

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Context>
<Resource name="jdbc/myoracle" auth="Container"
              type="javax.sql.DataSource"
              driverClassName="oracle.jdbc.OracleDriver"
              url="jdbc:oracle:thin:@127.0.0.1:1521:xe"
              username="SCOTT" password="TIGER"
              maxTotal="20" maxIdle="10"
              maxWaitMillis="-1"/>
</Context>
```
