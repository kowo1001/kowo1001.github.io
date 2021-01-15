---
title: Vue-(2) Javer Server Page
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Vue
toc: true
toc_sticky: true
toc_label: 목차
---

## JSP
- servlet만으로는 view 개발에 한계가 있을 수 있다
- 화면단에 tag 위주로만 개발하고, 자바 코드도 소화할 수있다
- 확장자는 * . jsp, URL은 http://ip:port/context/../file명.jsp 형태를 가진다
- 개발은 쉬운 편이지만, 컴파일 및 실행시 발생되는 에러는 처리가 어렵다

## JSP ScriptingTag
### 지시자
- JSP intro 설정 tag
- JSTL tag : 외부에서 tag들 조합해서 사용 가능
- 화면 분할시 사용 가능한 지시자

### JSP 주석 
- <%--   blablabla --%> : client 브라우저에 전송되지 않는 보안을 고려한 주석
- <!-- blablabla --!> : client 브라우저에 전송해서 소스보기로 확인 가능

### 출력 담당 Tag <%= %>
- expression tag
- <%= %>
### 멤버 변수, 메소드 구현 Tag <%! %>
- JSP는 Servlet으로 변환된다
- <%! %>
### 스클립틀릿 <% %>
- 모든 자바 코드 다 개발 가능한 tag

※  service(), doGet(), doPost() 메소드 구현부로 변환되는 tag는 멤버변수와 관련된 tag를 제외하고 나머지 모든 tag로 사용 가능하다

## JSP Action
- <jsp: 다양한 이름/>  또는 <jsp: 다양한 이름> 또는 </jsp: 다양한 이름>
-  객체 생성 : <jsp: useBean />
-  forward로 page이동 : <jsp: forward page="이동 page" />
-  forward tag 하위에 내장될 수 있으면서 query string 조합하는 tag, parameter값 표현 tag : <jsp: param name="별칭" value="값">

※ JSP ScriptingTag와 JSP Action은 sun에서 제시한 표준 jsp tag이다
