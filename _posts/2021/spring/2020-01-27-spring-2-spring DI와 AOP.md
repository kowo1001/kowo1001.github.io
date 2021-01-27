---
title: Spring-(1) DI와 AOP
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

## Spring Framework 장점
- 개발자들이 개발하고자 하는 애플리케이션 로직 개발에만 집중할 수 있음
- 개발이 단순해짐
- POJO 방식의 기술 사용이 가능 

## Spring 빈(bean)이란?
- Spring이 제어권을 가지고 생성 및 객체간의 관계를 관리하는 객체 의미

## IoC컨테이너 또는 Spring 컨테이너란?
- Spring 빈의 생성과 관계 설정, 사용, 생명주기 관리 등을 관장하는 기능을 제공해주며
Spring의 주요 핵심 기능이므로 컨테이너라고도 함 


## BeanFactory , ApplicationContext란 ?
- Spring에선 빈의 생성과 관계 설정, 사용, 제거 등의 기능을 담당하는 컨테이너를 의미함
- 컨테이너 기능을 담당하는 Spring의 주요 API
![spring주요 API](https://user-images.githubusercontent.com/37354978/106012858-32320d00-60ff-11eb-9719-033b56efe74e.PNG)

## Aspect Oriented Programming [AOP] 지원

Spring은 자체적으로 AOP를 지원하고 있기 때문에 트랜잭션이나 로깅, 보안과 같이 여러 비즈니스 모듈에서
공통적으로 필요로 하는 공통 관심 사항을 핵심 로직과 분리시켜 각 모듈에 적용할 수 있음

**AOP하면 '중복 코드 삭제' 무조건 암기할 것**

## Aspect 란 ?
보안과 로깅 모듈처럼 그 자체로 애플리케이션의 핵심 기능을 다루고 있지는 않지만,
애플리케이션을 구성하는 중요한 요소이고,
핵심 기능에 적용 되어야만 의미를 갖는 특별한 모듈을 의미
( 공통으로 가지는 중요 기능 로직을 구성하고 있는 것을 말함)


## Dependency Injection [DI]

## 의존성이란?
- 객체가 다른 객체를 참조

- 의존성을 주입한다는 의미
- 자동차 내부에서 타이머를 생산하는 것이 아닌 외부에서 생산된 타이머를 자동차에 장착하는 작업

## 의존관계
- 집합 관계(Aggregation) : 부분이 전체와 다른 생명주기를 가진다.(세탁기 in 집)
- 구성 관계(Composition) : 부분은 전체와 같은 생명 주기를 가진다. (심장 in 사람)


## Spring Project 만들기

Java Project - Convert to Maven - Spring - Add Spring Project Nature


## lombok 활용법
-> </build> 아래 다음 코드를 넣어주기
```xml
    <properties>

		<!-- Generic properties -->
		<java.version>1.8</java.version>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>

		<!-- Spring -->
		<spring-framework.version>4.3.30.RELEASE</spring-framework.version>

	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
			<version>${spring-framework.version}</version>
		</dependency>
		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<version>1.18.8</version>
		</dependency>
	</dependencies>
```

playdata.xml - Namesspaces - beans, context 체크

```xml
<!-- 애노테이션 사용하겠다는 설정 -->
<context:annotation-config />
```
```java
@NoArgsConstructor
@AllArgsConstructor
@Getter
@Setter
@ToString

@Component // <bean id="car" class="model.domain.Car" /> 동일한 설정
public class Car {
	private String carName;
	private int carNumber;
}
```

```java
//Customer.java
@NoArgsConstructor
@AllArgsConstructor
@Getter
@Setter
@ToString

@Component
public class Customer {
	private String name;
	private int age;
	private Car car;
}
```

```xml
<!-- 스프링 빈으로 설정하고자 하는 class들이 내장된 package명 제시하면 스프링에게 스캔 요청 -->
<context:component-scan base-package="model.domain" />
```

```java
@NoArgsConstructor
@AllArgsConstructor
@Getter
@Setter
//@ToString

@Component // <bean id="car" class="model.domain.Car" scope="singleton"/> 동일한 설정
@Scope("prototype") // <bean id="car" class="model.domain.Car" scope="prototype"/> 동일한 설정
public class Car {
	private String carName;
	private int carNumber;
}
```

```java
@Component("c") // <bean id="c" class="model.domain.Car" scope="singleton"/> 동일한 설정
@Scope("prototype") // <bean id="car" class="model.domain.Car" scope="prototype"/> 동일한 설정
public class Car {
	private String carName;
	private int carNumber;
}
```
```java
//Test.java
	public static void main(String[] args) {
		ApplicationContext context = new ClassPathXmlApplicationContext("playdata.xml");
		
		Car c1 = context.getBean("c", Car.class);
		System.out.println(c1);
		
		Car c2 = context.getBean("c", Car.class);
		System.out.println(c2);
		
	}
```
사용자가 지정한 Component 이름으로 사용 가능

## @Autowired
- 의존 객체 주입시에 사용되는 애노테이션
- 선언 위치 : 변수, 메소드, 생성자 (변수,메소드,생성자 중 하나에만 애노테이션 선언하기 -> 반드시 한 곳에만 설정)
- 기능 : 타입과 일치가 되는 스프링 빈을 자동 주입
- 예시 
Customer가 Car를 의존
- Car car
- setCar() : setter injection
- Customer(Car c) : constructor injection
