---
title: Spring-(1) 설치 및 설정
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

## SPRING 시작 및 설치 
- https://spring.io/ 로 접속
- Projects - Spring Tools 4 - Spring Tools 4 for Eclipse - 4.9.0 WINDOWS 64 BIT 다운로드
- Main 화면 - QUICKSTART - 참고해서 공부 가능
- Projects - Spring Framework - LEARN 탭 클릭 - spring framework 4.3 구글 검색 -  Spring Framework Reference Documentation 기술문서 클릭 -
https://docs.spring.io/spring-framework/docs/4.3.30.RELEASE/spring-framework-reference/htmlsingle/ - https://github.com/spring-projects/toolsuite-distribution/wiki/Spring-Tool-Suite-3
- 이클립스 작업폴더 경로 지정 - help - eclipse marketplace - spring 검색하기 - spring 관련 플러그인 검색 가능 - 괜찮은 plugin이 없다면 수동설치 고려할 것.
- 구글 검색 - eclipse spring plugin 검색 - 직접 수동 설치 가능 
- help -install new software - add - STS 이름 작성 - http://dist.springsource.com/release/TOOLS/update/e4.8/ 경로 넣기 
- help - About Eclipse IDE - Spring IDE 아이콘 확인 
- New - Other - Spring - Spring Legacy Project - Next - Simple Spring Maven - Project name: step00_sample - Select Spring version : 3.2.3 -Finish
- 프로젝트 오른쪽 마우스 클릭 -  build path - Libraries - jdk 1.8로 수정 - Java Compiler - Compiler compliance level - 1.8로 설정 - 왼쪽 Project Facets - JAVA 1.8 - Runtimes - jdk1.8.0_201 설정
- Project Explorer - pom.xml - <java.version>1.8 - <spring-framework.version> 4.3.3으로 수정  -<!-- Hibernate / JPA --> <hibernate.version> 버전 추후 수정 예정
- new -other -spring -Spring Bean Configuration File - applicationContext.xml 파일로 생성 - context - 밑단에 context-4.3.xsd 체크 클릭 
- Maven ClassNotFound 에러 발생 시 - Maven Repositories - Local Repository 삭제후 다시 설치
- 컨테이너 만들때 객체 자동 생성 - 객체를 가져와서 사용 가능 - 
```xml
// applicationContext.xml
<!-- step01 :getBean()으로 호출 전에 스프링 객체(스프링빈)을 자동 생성해서 하나만 고유하게 유지하는 설정 
		scope="singleton" default로 설정되어있음
	-->
<bean id="p1" class="model.domain.Person" />

<!-- step02 : getBean()로 호출시에 새롭게 생성해서 제공해주는 설정 -->
	<bean id="p1" class="model.domain.Person" scope="prototype"/>

```
```java
// RunTest.java
// 컨테이너 기능의 객체 생성
	public static void main(String[] args) {
		// 컨테이너 기능의 객체 생성
		ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
		
		
		// Person 객체 받아서 활용
		Person p = (Person)context.getBean("p1");
		p.setAge(100);
		System.out.println(p);
		
		Person p2 = context.getBean("p1", Person.class);
		System.out.println(p2);
	}
```
실행 결과
    기본 생성자
    setAge()
    Person [name=null, age=100]
    기본 생성자
    Person [name=null, age=0]

- New -Other- Spring- Spring Legacy Project - 
- New -Project- Java Project - step01_DI 오른쪽 마우스 클릭 - Configure - Convert to Maven - groupId: playdata 
- step01_DI 오른쪽 마우스 클릭- Spring -Add Spring Project Nature 
- Dependencies - Add... - spring-context 검색 - spring-context : 4.3.3.RELEASE 

```xml
<!-- public Customer(String name, int age, Car car) -->
	<bean id="c1" class="model.domain.Customer">
		<constructor-arg value="유재석"/>
		<constructor-arg value="77"/>
		<constructor-arg ref="car"/> <!-- 의존성 객체를 주입함 bean id="car" -->
	</bean>


<bean id="car" class="model.domain.Car">
		<constructor-arg value="그렌저"/>
		<constructor-arg value="77"/>
	</bean> 
```
```java
public static void main(String[] args) {
		ApplicationContext context = new ClassPathXmlApplicationContext("di.xml");
		// Car c = context.getBean("car", Car.class);
		Customer c = context.getBean("c1", Customer.class);
		System.out.println(c);
	}
```

실행 결과
    Car(String carName, int carNumber)
    Customer(String name, int age, Car car)
    Customer [name=유재석, age=77, car=Car [carName=그렌저, carNumber=77]]

의존성 객체 주입된 Car 객체가 먼저 생성되고, 그다음 Customer 객체가 생성된다


```xml
<bean id="car" class="model.domain.Car" scope="singleton">
		<property name="carName" value="소나타"/>
		<property name="carNumber" value="88"/>
		
	</bean>

	<bean id="c1" class="model.domain.Customer" scope="singleton">
		<property name="name" value="백종원"/>
		<property name="age" value="50"/>
		<property name="car" ref="car" />
	</bean>
```
```java
public static void main(String[] args) {
		ApplicationContext context = new ClassPathXmlApplicationContext("di2.xml");
		
		Customer c = context.getBean("c1", Customer.class);
		System.out.println(c); //c.toString() - Object의 메소드는 주소값 반환 로직
		
		Customer c2 = context.getBean("c1", Customer.class);
		System.out.println(c2);
		
		System.out.println(c.getCar());
		System.out.println(c2.getCar());
	}
```
실행 결과
    Car()
    setCarName(String carName)
    setCarNumber(int carNumber)
    Customer()
    setName(String name)
    setAge(int age)
    setCar(Car car)
    Customer [name=백종원, age=50, car=Car [carName=소나타, carNumber=88]]
    Customer [name=백종원, age=50, car=Car [carName=소나타, carNumber=88]]
    Car [carName=소나타, carNumber=88]
    Car [carName=소나타, carNumber=88]


## 기술문서 참고
https://docs.spring.io/spring-framework/docs/4.3.30.RELEASE/spring-framework-reference/htmlsingle/#beans-setter-injection

Whale을 통해 기술문서 참고하기
웨일(Whale) - 오른쪽 스페이스에서 보기 - https://docs.spring.io/spring-framework/docs/4.3.30.RELEASE/spring-framework-reference/htmlsingle/ 