---
title: Spring-(1) DI와 Annotation
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

## Spring Framework(DI, AOP, MVC) 특징

## Aspect Oriented Programming [AOP] 지원

Spring은 자체적으로 AOP를 지원하고 있기 때문에 트랜잭션이나 로깅, 보안과 같이 여러 비즈니스 모듈에서
공통적으로 필요로 하는 공통 관심 사항을 핵심 로직과 분리시켜 각 모듈에 적용할 수 있음

**AOP하면 '중복 코드 삭제' 무조건 암기할 것**

## Aspect 란 ?
보안과 로깅 모듈처럼 그 자체로 애플리케이션의 핵심 기능을 다루고 있지는 않지만,
애플리케이션을 구성하는 중요한 요소이고,
핵심 기능에 적용 되어야만 의미를 갖는 특별한 모듈을 의미
( 공통으로 가지는 중요 기능 로직을 구성하고 있는 것을 말함)

|API유형|처리결과|
|:-------------------------:|:-------------------------------:|
|axios.get('URL주소').then().catch()|해당 URL로 get방식으로 요청<br>then()안에 반환값 로직 작성<br>catch()안에는 오류발생시 로직 작성|
|axios.post('URL주소').then().catch()|해당 URL로 POST방식으로 요청<br>then()안에 반환값 로직 작성<br>catch()안에는 오류발생시 로직 작성|
|axios({옵션})| HTTP요청에 대한 자세한 속성들을 직접 정의하여 보낼 수 있음|


## Dependency Injection [DI]

## 의존성이란?
- 객체가 다른 객체를 참조

- 의존성을 주입한다는 의미
- 자동차 내부에서 타이머를 생산하는 것이 아닌 외부에서 생산된 타이머를 자동차에 장착하는 작업
