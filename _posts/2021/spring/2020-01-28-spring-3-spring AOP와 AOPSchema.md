---
title: Spring-(1) Spring 개념과 DI
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


## Aspect Oriented Programming [AOP] 지원

Spring은 자체적으로 AOP를 지원하고 있기 때문에 트랜잭션이나 로깅, 보안과 같이 여러 비즈니스 모듈에서
공통적으로 필요로 하는 공통 관심 사항을 핵심 로직과 분리시켜 각 모듈에 적용할 수 있음

**AOP하면 '중복 코드 삭제' 무조건 암기할 것**

## Aspect 란 ?
보안과 로깅 모듈처럼 그 자체로 애플리케이션의 핵심 기능을 다루고 있지는 않지만,
애플리케이션을 구성하는 중요한 요소이고,
핵심 기능에 적용 되어야만 의미를 갖는 특별한 모듈을 의미
( 공통으로 가지는 중요 기능 로직을 구성하고 있는 것을 말함)


## AOP Advice 종류

|Advice 종류|XML스키마 기반의 POJO 클래스를 이용|@Aspect애노테이션 기반|설명|
|:-------------------------:|:-------------------------------:|:-------------------------------:|:-------------------------------:|
|Before|\<aop:before\>|@Before|target 객체의 메소드 호출시 호출 전에 실행|
|AfterReturning|\<aop:after-returning\>|@AfterReturning|target 객체의 메소드가 예외없이 실행된 후 호출|
|AfterThrowing|\<aop:after-throwing\>|@AfterThrowing|target객체의 메소드가 실행하는 중 예외가 발생한 경우에 호출|
|After|\<aop:after\>|@After|target 객체의 메소드를 정상 또는 예외 발생 유무와 상관없이 실행<br> try의 finally와 흡사|
|Around|\<aop:around\>|@Around|target객체의 메소드 실행 전, 후 또는 예외 발생 시점에 모두 실행해야할 로직을 담아야 할 경우|

## 로직구분
1. 핵심 로직 : 비즈니스 로직 (core) ex. 구매와 판매
2. 공통 로직 : 핵심이 아닌 공통으로 사용되는 로직 ex. 구매로직에만 적용되는 공지사항, 판매로직에만 적용되는 공지사항

## 핵심로직과 공통로직 적용시점
- 공통로직 반영 시점은 각 핵심 로직들이 실행 전, 실행 후 적용
- before : 핵심로직 실행전, 전처리
- after : 핵심로직 실행후, 후처리
- throwing : 예외 발생 - 핵심로직 실행중 예외 발생
- returning : 핵심 로직 정상 실행되면서 반환시 - 후처리
- around : before,after,throwing,returning 포괄적인 설정 가능

## 용어 및 특징
- pointcut , pointcut-ref : 공통로직을 적용받을 핵심 로직의 위치 + 시점
- 공통로직의 클래스 : ~Aspect


```xml
<!-- aop 사용을 위한 필수 설정 -->
	<aop:aspectj-autoproxy />
	
	<!-- 핵심로직(biz, core)과 공통로직(aspect)을 스프링 빈으로 등록 -->
	<bean id="biz" class="step02.biz.aop.Car" />
	
	<bean id="common" class="step02.common.aop.NoticeAspect" />
	
	<!-- 핵심로직 실행 전, 후 공통 로직 적용
		핵심의 어떤 메소드들에 공통 로직 적용할지도 결정을 해야함
		어떤 핵심 로직의 메소드에 어떤 공통로직의 메소드를 정해진 시점에 적용
		spring은 aspectj라는 framework 활용
		 - 기능을 메소드에만 적용 + 표현법은 그대로 사용
		  
	 -->
	 
	 <aop:config>
	 	<aop:pointcut id="bizLogic" expression="execution(* step02.biz.aop.Car.buy*(..))"/>
	 	
	 	<aop:aspect ref="common">
	 		<aop:before method="noticBuyStart" pointcut-ref="bizLogic"/>
	 		<aop:after method="noticBuyEnd" pointcut-ref="bizLogic"/>
	 		
	 		<!-- <aop:before method="noticeBuyStart" pointcut="execution(* step02.biz.Car.buy*(..))" />
	 		<aop:after method="noticBuyEnd" pointcut="execution(* step02.biz.Car.buy*(..))" /> -->
	 	</aop:aspect>
	 </aop:config>
```