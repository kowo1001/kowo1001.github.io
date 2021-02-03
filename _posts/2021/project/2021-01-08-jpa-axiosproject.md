---
title: JPA & AXIOS MiniProject
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- PROJECT
toc: true
toc_sticky: true
toc_label: 목차
---


# WORKMAN_BLIND Project



---
### WORKMAN_BLIND 두번째 이야기

안녕하세요! 새롭게 돌아온 **WORKMAN_BLIND**입니다.:smile:
저희는 템플릿을 대폭 수정하고 각종 기능을 추가하여 더욱 유용한 프로그램으로 거듭났답니다.
달라진 워크맨의 모습을 지금 바로 영상에서 만나보세요!


---


## WORKMAN BLIND 시연 영상
[![workmanblind 시연영상](https://img.youtube.com/vi/HYjsBZNoflA/0.jpg)](https://www.youtube.com/embed/HYjsBZNoflA) 
---


> **팀원 : 장종욱, 권희성, 장문희**

---

### WORKMAN_BLIND의 탄생과정
<br><br><br><br>
안녕하세요 알바몬 여러분:smile: 
<br><br><br><br>

다들 돈을 모으기 위해 야심차게 새로운 아르바이트를 구해 출근했다가 

일주일도 안되어, 3일도 안되어, 혹은 반나절만에 탈주한 경험이 있으실겁니다. (저만 그런건 아니겠지요..?:joy:)
<br><br><br><br>


이유는 다양! 

일이 너무 힘들어서:weary:

동료 혹은 사장님이 최악이라:scream:

진상손님이 많아서:rage:
<br><br><br><br>



이럴때 '거기 알바자리 최악이래!:grimacing:' 하고 미리 친구가 알려주었더라면 

우리의 소중한 시간과:clock4: 노동력을:muscle: 세이-브 할수 있었을텐데 말이에요..
<br><br><br><br>



저희 :fire:**WORKMAN_BLIND**:fire:는 바로 이런 서러운 알바몬들의 고충을 해결하기위해 탄생하였답니다!
<br><br><br><br>


아르바이트를 지원하기전에 미리 그 곳에서 근무해봤던 선배들의 후기를 **WORKMAN_BLIND**에서 빠르게 스캔한다음!:eyes::eyes::eyes:

거를곳은 거르고!:no_good: 꿀알바는 누구보다 빠르게 지원하고!:ok_woman:

우리의 신중한 초이스를 도와주는 멋진 친구:two_women_holding_hands:가 되어드리겠습니다. 
<br><br><br><br>

맡겨만 주세요!!:punch::punch::punch:
<br><br><br><br>

---


## Service 

---

#### 1. 회원가입 및 로그인 - CREATE

---

1. 로그인 페이지에서 로그인

2. 로그인 성공 페이지 -> 회원정보수정/탈퇴

---

#### 2. 알바 평가게시판 작성 - CREATE

---

1. 회원가입 또는 로그인

2. 알바스토리 클릭 -> 알바리스트 페이지에서 평가 게시글 등록 버튼을 통해 작성

---

#### 3. 알바 검색- READ

---

1. 회원가입 또는 로그인

2. 메인 페이지에서 '알바리뷰' 클릭

3. 알바리스트 페이지로 넘어간다

4. (1-알바리스트페이지 ->알바평가게시판페이지) 지역 검색 -> 지역에 속한 기업 리스트 출력(알바리스트페이지) -> 기업명 클릭시 해당 기업 평가게시판으로 이동

   (2-알바리스트페이지 ->알바평가게시판페이지) 기업명 클릭 -> 기업에 해당하는 알바평가게시판으로 이동

---

#### 4. 알바 평가 게시글에서 내용 수정 - UPDATE

---

1. 회원가입 또는 로그인

2. 아이디로 평가 게시글 검색(본인이 작성한 글 검색) -> 알바 평가 게시판에서 수정하기 버튼 클릭 -> 수정 -> 수정완

---

#### 5. 로그인 성공 페이지에서 비밀번호 수정 - UPDATE

---

1. 회원가입 또는 로그인

2. 비밀번호 수정 버튼 클릭 -> 아이디로 회원 정보 가져오기(아이디, 비밀번호, 이름, 이메일) -> 비밀번호 수정 -> 수정완료

---

#### 6. 알바 평가 게시글 삭제 - DELETE

---

1. 회원가입 또는 로그인

2. 아이디로 평가 게시글 검색(본인이 작성한 글 검색) -> 알바 평가 게시판에서 삭제하기 버튼 클릭 -> 삭제 -> 삭제완료

---

#### 7. 회원 탈퇴 - DELETE

---

1. 회원가입 또는 로그인

2. 로그인 성공 페이지 -> 회원 탈퇴하기 버튼 클릭 -> 회원 탈퇴 완료

---

### :thumbsup: 구현 과정 - 깃허브 프로젝트 기능 이용

![todo](https://user-images.githubusercontent.com/73862504/103252477-74611500-49c0-11eb-9bda-f586027cfe8e.PNG)

---

## :speech_balloon: WORKMAN_BLIND 기능 설명

---
## 💡 Technologies Used

<img width="486" alt="technology used" src="https://user-images.githubusercontent.com/37354978/104281745-4ff15680-54f1-11eb-8a4f-9b796d67dcb5.png">

---
### Structure

#### 기존 테이블 구조
![erd](https://user-images.githubusercontent.com/73862504/103251857-ff8cdb80-49bd-11eb-99ca-70a725b0e7a8.png)

#### 변경된 테이블 구조
![image](https://user-images.githubusercontent.com/37354978/104269652-28db5a80-54da-11eb-8c69-3bcca26c5c8e.png)

#### 테이블 구조 변경 이유
- 기존 테이블 구조는 하나의 테이블에 모든 참조키를 가지고 있는 구조이어서 기업, 회원, 알바리스트를 모두 참조해야 했습니다
- 그래서 하나의 테이블에서 모든 부모키를 참조하지 않고, 꼭 필요한 부분에만 부모키를 참조하도록 수정하였습니다

---

## SQL TABLE

* DDL

```SQL
-- 회원
DROP TABLE member cascade constraint;

-- 알바 리스트
DROP TABLE parttimelist cascade constraint;

-- 알바 평가 게시판
DROP TABLE parttimeeval cascade constraint;

-- 기업
DROP TABLE company cascade constraint;

-- 알바 리스트 게시판 sequence
DROP sequence partlist_seq_num;

-- 알바 평가 게시판 sequence
DROP sequence parteval_seq_id;


CREATE TABLE company (
   company_name      VARCHAR2(50)    PRIMARY KEY,
   company_pw        VARCHAR2(50)    NOT NULL,   
   category          VARCHAR2(50)    NOT NULL,
   company_loc       VARCHAR2(200)    NOT NULL,
   company_num       VARCHAR2(50)    NOT NULL
);


CREATE TABLE member (
       user_id    VARCHAR2(50)  PRIMARY KEY,
       user_pw    VARCHAR2(100) NOT NULL,
       user_name    VARCHAR2(20) NOT NULL,
       user_num    VARCHAR2(50) NOT NULL,
       company_name    VARCHAR2(50) NOT NULL

);


CREATE TABLE parttimelist (
       list_num             NUMBER(10) PRIMARY KEY,
       company_name          VARCHAR2(50) NOT NULL,
       work_time              VARCHAR2(50) NOT NULL,
       hourly_wage       VARCHAR2(50) NOT NULL,
       work_period          VARCHAR2(50) NOT NULL,
       objective         VARCHAR2(50) NOT NULL
);


CREATE TABLE parttimeeval (
       eval_num            NUMBER(10) PRIMARY KEY,
       user_id            VARCHAR2(50) NOT NULL,
       company_name         VARCHAR2(50) NOT NULL,
       pros_cons           VARCHAR2(100) NOT NULL,
       wage_delay             VARCHAR2(100) NOT NULL,
       environment          VARCHAR2(100) NOT NULL,
       incline              VARCHAR2(100) NOT NULL,
       opinion         VARCHAR2(200) NOT NULL
);


CREATE SEQUENCE parteval_seq_id START WITH 1 INCREMENT BY 50 ;
CREATE SEQUENCE partlist_seq_num START WITH 1 INCREMENT BY 50 ;



ALTER TABLE member  ADD FOREIGN KEY (company_name) REFERENCES company (company_name);
ALTER TABLE parttimelist ADD FOREIGN KEY (company_name)  REFERENCES company (company_name);
ALTER TABLE parttimeeval ADD FOREIGN KEY (company_name)  REFERENCES company (company_name);
ALTER TABLE parttimeeval ADD FOREIGN KEY (user_id) REFERENCES member (user_id);
```

* DML

```sql
-- company 테이블 기업 저장
insert into company values('샹떼pc방인천동춘점','1234','pc방','인천광역시 연수구 동춘동 933-5번지 영창빌딩 5층','010-9280-4437');
insert into company values('cu충정로프랑스점','1234','편의점','부산광역시 금정구 장전2동 금강로279번길 81-14','010-9280-7637');
insert into company values('이마트 천안서북점 이니스프리','1234','화장품가게','대구광역시 중구 서성로 99 104동 상가 141호 대구역센트럴자이','010-9280-7624');
insert into company values('GS25대구역자이점','1234','편의점','대구광역시 중구 서성로 99 104동 상가 141호 대구역센트럴자이','010-8920-8402');
insert into company values('한솥도시락시화점','1234','음식점','경기도 시흥시 정왕동 1742-17','010-9280-7629');
insert into company values('투썸플레이스송도점','1234','카페','인천광역시 연수구 송도1동 컨벤시아대로 69','010-9280-7557');
insert into company values('플레이데이터','1234','교육기관','서울시 서초구 서초대로46길 42, 엔코아 타워','010-9280-7887');

-- member 테이블 회원 저장 -문제
insert into member values('kwon0329','1234','권희성','010-1234-5678','플레이데이터');
insert into member values('jongwook123','1234','장종욱','010-1234-5666','샹떼pc방인천동춘점');
insert into member values('moonyangels2','1234','장문희','010-1234-5632','이마트 천안서북점 이니스프리');
insert into member values('kwon1234','1234','홍길동','010-1234-5633','GS25대구역자이점');
insert into member values('kwon5678','1234','이순신','010-1234-5655','샹떼pc방인천동춘점');


-- member 테이블 회원 저장
insert into member values('kwon0329','restplease00','권희성','010-1234-5678','플레이데이터');
insert into member values('jongwook123','restplease01','장종욱','010-1234-5666','샹떼pc방인천동춘점');
insert into member values('moonyangels2','restplease02','장문희','010-1234-5632','이마트 천안서북점 이니스프리');
insert into member values('kwon1234','restplease03','홍길동','010-1234-5633','GS25대구역자이점');
insert into member values('kwon5678','restplease04','이순신','010-1234-5655','샹떼pc방인천동춘점');


-- parttimelist 테이블 알바리스트 저장
insert into parttimelist values(208254,'샹떼pc방인천동춘점','6시간',9000,'1년이상','피씨방 꿀알바 식대무한제공');
insert into parttimelist values(208252,'cu충정로프랑스점','3시간',8590,'6개월이상','편의점 알바 급구합니다');
insert into parttimelist values(208255,'이마트 천안서북점 이니스프리','8시간',9000,'6개월이상','화장품 좋아하는분 환영');
insert into parttimelist values(208253,'GS25대구역자이점','5시간',8590,'3개월이상','오전알바 구합니다');
insert into parttimelist values(208258,'한솥도시락시화점','6시간',8590,'6개월이상','식대무료 알바구함');
insert into parttimelist values(208257,'투썸플레이스송도점','5시간',9500,'6개월이상','카페알바 경력구함');
insert into parttimelist values(208256,'플레이데이터','5시간',10000,'1년이상','가족같은 직원 구합니다');


-- parttimeeval 테이블 알바평가게시글 저장-문제
insert into parttimeeval values(208275,'kwon0329','플레이데이터','칼퇴가능','안밀려요','식사제공','깐깐해요','오래오래 일하고 싶어요');
insert into parttimeeval values(208234,'jongwook123','샹떼pc방인천동춘점','칼퇴가능','안밀려요','식사제공','깐깐해요','너무 바빠요');
insert into parttimeeval values(208211,'moonyangels2','이마트 천안서북점 이니스프리','칼퇴가능','안밀려요','식사제공','깐깐해요','단기로 할거면 추천');
insert into parttimeeval values(208287,'kwon1234','GS25대구역자이점','칼퇴가능','안밀려요','식사제공','깐깐해요','진상손님이 많아요');


commit;
```

---

## ISSUE <1> JPA Project

---

#### 1. 일부 팀원에게만 나타나는 404오류

---

깃허브 데스크탑을 이용해 푸쉬한 같은 파일임에도 불구하고 일부 팀원에게만 404에러가 발생했다.

문제의 원인을 찾아보니 각자 탐캣의 경로가 미세하게 달랐던 탓이었고

C:\ITStudy\00.sw\04.WAS\apache-tomcat-8.5.61\lib

다음과 같은 경로로 모두 통일하고

 jsp-api.jar과 servlet-api.jar 의 경로 또한 통일함으로써 해결할 수 있었다. 

---

#### 2. @WebSevlet(/)과 httprequest에 엑박이 뜸

---

jsp-api.jar, servlet-api.jar를 추가헤 해결하였다.

---

#### 3. CSS파일 로드가 되지않음

---

이클립스 상의 탭이 아닌 크롬으로 창을 띄우니 해결되었다.

탭으로 띄울 경우, 업데이트가 반영되지 않거나 느리게 되는 경우가 많기 때문에

꼭 Window - Web browser - Chrome로 설정해 크롬으로 띄우는 것이 안전하다.


그 외에 css 파일 경로 출력해보기, URL 에 직접 css 파일 경로를 넣어보는 방법으로

CSS파일에 오류가 있어서 로드가 안되는건 아닌지 확인해보는 방법이 있다.

---

#### 4. VARCHAR2 vs CLOB 사용 여부

---
게시판 작성 기능을 두고 varchar2보다 더 큰 데이터 타입을 찾았고, 최대 4GB까지 작성가능한 CLOB이라는 걸 알게되었다.

하지만, 시스템상에서 문제가 생길 수 있다는 강사님의 조언에 따라 varchar2를 최대 크기인 4000바이트로 설정했다. -> varchar2(4000)

---

#### 5. JSP 파일 생성 직후 에러

---
- The superclass "javax.servlet.http.HttpServlet" was not found on the Java Build Path


이클립스에 tomcat8.5가 연동이 안되어서 생긴 문제

tomcat 8.5 서버를 이클립스에 연동해서 해결함

---

#### 6. 아쉬웠던 점

---

- **테이블 초기 관계 설정** : 복잡하게 짜여져 코드짤때 어려움이 많았다. 다음부턴 테이블이 서로 하나씩만 참조하도록 설정하면 좀 더 수월할 것이라 생각한다.

- **일관성있는 변수명설정** : 여러명이 각자 파트에서 변수명을 짓다보니 아무래도 일관성이 없어 참조할때 헷갈리는 일이 많았다. 처음부터 규칙을 확실히 정해둬야겠다.

- **DDL, DML** : entity와 순서가 다르게 되어있어 생성 및 추가 시 애를 먹었던 테이블도 있었고 구조가 자주 바뀐 점이 아쉬웠다. 그 과정에서 헷갈려하는 팀원들도 있고 오류도 다소 나온편이라 당연한 말이지만 초기에 확실하게 잡아놓는것이 중요하다고 느꼈다.

---
## ISSUE <2> JavaScript project

---

#### 1. ORA-02289: 시퀀스가 존재하지 않습니다.

---


테이블 생성 시, @SequenceGenerator 어노테이션 선언을 해놓고 Sequence를 생성하지 않아 위와같은 에러가 발생했었다. 
시퀀스는 유일한 값을 생성해주는 오라클 객체로 보통 primary key로 사용할 수 있는 순차적으로 증가하는 숫자 컬럼을 생성할 때 사용한다.


---

#### 2. 절대경로를 이용한 파일 경로 문제 해결

---

bootstrap의 css를 불러오지 못할때 상위 폴더에 접근하고 싶은데 접근하지 못해서 net::ERR_ABORTED 404 (Not Found) 에러가 뜸
-${path}.. 경로 앞단에 이 부분을 추가하면 접근 가능

---

#### 3. parttimeList 데이터를 넣어도 전체 불러오지 못하는 문제

---
parttimelist의 DTO에만 적용되어 있는 시퀀스 값을 DDL에서도 추가함으로써 해결하였다.
 

---

#### 4. 이클립스 commit 후 한글 깨짐 현상

---
pageEncoding="UTF-8"으로 되어있는데도 한글 깨짐 현상이 지속되어 아래 블로그를 참고하여

이클립스의 window-preference의 각종 언어 설정을 utf-8로 변경하여 해결하였다.

https://insight-bgh.tistory.com/117

---




## ✍️ Author
 Team WORKMAN_BLIND
  - 권희성 [(HeeSeongKwon )](https://github.com/shiningcastle)
  - 장문희 [(MoonheeJang)](https://github.com/JANGMOONHEE)
  - 장종욱 [(JongwookJang)](https://github.com/kowo1001)
 

## 참고

:mag: [엑셀문서링크](https://docs.google.com/spreadsheets/d/19So7A99qJnlKGLl4MukpBJ5gDMmvVqs-dZwoCNEFR7c/edit#gid=0)

:mag: [ERDCLOUD 링크 ](https://www.erdcloud.com/d/Hqr6Gx6qMu6i9wZ8i)

:mag: [카카오 오븐 페이지 설계](https://ovenapp.io/project/VAWmAEwLwYoCOj8CLJ8i0hJKVkupt41v#f5ld6)

