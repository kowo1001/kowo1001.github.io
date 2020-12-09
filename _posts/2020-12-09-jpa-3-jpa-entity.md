---
title: JPA를 알아보자-(3) JPA로 Entity 생성
---

# JPA table 생성
```java
package step01.entity;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.Id;

@Entity
public class Member {
	@Id  //pk로 설정
	@Column(name = "id")
	private String id;

	@Column(name = "name")
	private String userName;

	// 정수 10자리 타입 의미
	@Column(precision = 10)
	private int age;
}
```
## 1. @Entity
□ table로 매핑되는 자바 클래스

□ 미 존재했던 TABLE인 경우 자동 생성

□ 설정만으로 자동 생성되는 sql 문장 확인

□ @Entity(name="")

## 2. @Id
□ PK 설정

□ Entity 클래스 내부에 멤버변수 선언구에 설정(필수)


## 3. @Column
□ 멤버변수와 매핑되는 TABLE 컬럼 설정

□ 변수명과 동일, 변수명과 다르게 설정, 컬럼의 타입정보를 속성 정보(속성명=값)으로 보유

□ Column(name="employee_id")


## 4. @GeneratedValue
□ PK의 값을 자동 생성하기 위함

□ strategy

	● GenerationType.AUTO : 특정 DB에 맞게 자동선택
	● GenerationType.IDENTIFY : DB의 identify 컬럼 이용
	● GenerationType.SEQUENCE : DB의 sequence 컬럼 이용
	● GenerationType.TABLE : 유일성이 보장된 db 테이블을 이용

□ generator
SequenceGenerator나 TableGenerator 에노테이션에서 명시된 PK 생성자를 재사용할때 쓰인다. 이미 있는 값을 가져오는 방식

## 5. @SequenceGenerator
□ Sequence 만듬

□ name : generator의 이름

□ sequenceName : sequence의 이름

□ initialValue : 시작값

□ allocationSize : 미리 메모리에 할당할 값(default : 50)

# JPA CRUD
## ● create(insert)
```java
Member member = new Member("id2", "신동엽2", 10); 
em.persist(member); //insert 기능의 메소드, 영속성컨텍스트에저장, insert 생성, 스냅샵에 저장
Member member2 = new Member("id1", "신동", 10); 
em.persist(member2); //insert 기능의 메소드, 영속성컨텍스트에저장, insert 생성, 스냅샵에 저장
```
## ● select
```java
Member oneFindMember = em.find(Member.class, "id1"); // primary key를 활용해 하나만
List<Member> allMember = em.createQuery("select m from Member m", Member.class).getResultList(); //쿼리문 활용
```
## ● update
```java
member.setAge(40); 
```
## ● delete
```java
em.remove(oneFindMember);
```
