---
title: JPA를 알아보자-(4) JPA Foreign Key, 관계
---

# 관계(Relationship) 설정하기

## OneToOne 단방향 관계
상황을 생각해보자.  하나의 반에 강사님은 한명만 있고 강사님 한명은 하나의 반만 맡을 수 있다. 이것이 일대일 관계이다.

주로 이러한 관계에서는  반에는 강사님이 반드시 존재하고 강사님은 반드시 반을 맡아야 하지 않는 것을 고려하여 반에 FK를 부여한다.

```java
public class Class{
	@Id
	private String className;

	@OneToOne
	@JoinColumn(name="teacher_name")
	private Teacher teacherName;
}
```
이를 통해,  class가 teacher의 PK인 teacherName을 FK로 설정하는 단방향 관계가 된다.

## OneToOne 양방향 관계
아래와 같이 코드를 작성할 경우, Teacher가 Class를 Class가 Teacher를 서로 가져오는 양방향 OneToOne 관계가된다.
```java
pulic class Teacher{
	@Id
	private String Name;

	@OneToOne(mappedBy = "teacherName")
    private Class className;
}
```
mappedBy가 있는 teacher를 먼저 선언해주고 이를 FK로 사용하는 class를 선언한다.
teacher table에는 classname은 없지만 t1.getclassName으로 SW개발 및 분석반을 가져올 수 있다.
```java
Teacher t1 = Teacher.builder().name("김○○").build();
Class c1 = Class.builder().className("SW개발및분석반").teacherName(t1).build();
em.persist(c1);
em.persist(t1);
```

## OneToMany
상황을 생각해보자.  사내 동아리에는 사원이 여러명 존재한다.  반대로 사원은 동아리를 하나만 들을 수 있다.
이런 경우를 일대다 관계라고 한다.

주로 사원이 동아리를 가입하지 않을 수 있다는 것을 고려하여 Club에 FK를 부여한다.
```java
public class Club{
	@Id
	private String name;

	@OneToMany
	@JoinColumn(name="employee_name")
	private list<Employee> employees;
}
```
하지만 이 경우에는 Employee_name column이 유동적이라는 것 때문에 관계형 데이터 모델링에서는 사용되지 않는다.


## ManyToOne
OnetoMany에서 외래키를 Club이 아닌 Employee에 부여하는 경우이다. 이럴 경우 column의 값이 유동적이지 않기 때문에 이 방법을 많이 사용한다.
```java
public class Employee{
	@Id
	private String name;

	@ManyToOne
	@JoinColumn(name="club_name")
	private Club club;
}
```
Employee가 Club을 FK로 가져오는 형태이다.

```java
pulic class Club{
	@Id
	private String name;

	@OneToMany(mappedBy = "club")
	private list<Employee> employees;
}
```
Club Table에는 존재하지 않지만,  Club에 속하는 employees를 객체 안에 저장한다.
```java
Club c1 = Club.builder().name("축구부").employees(new ArrayList<Employee>()).build();
Employee e1 = Employee.builder().name("김주임").club(c1).build();
Employee e2 = Employee.builder().name("이주임").club(c1).build();
em.persist(c1);
em.persist(e1);
em.persist(e2);
```
위와 마찬가지로 mappedBy가 있는 Club객체 먼저 선언하고 Student를 선언해준다.
