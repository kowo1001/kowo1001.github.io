---
title: Vue-(9) eventbus와 router
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


## Vue 컴포넌트간 통신 : 이벤트 버스

### 관계없는 컴포넌트 간 통신 - 이벤트 버스
- 컴포넌트 간의 통신은 상하위 관계에서만 적용
- 서로 다른 컴포넌트 간의 통신 불가능, 가령 형제 관계, 부모 손자, 증손자 관계인 컴포넌트들 사이의 정보 전달
- 별도의 데이터 정보를 가지지 않고, 순수하게 이벤트를 통해서 컴포넌트 간의 정보 교환만을 위해서 사용

### 해결책
- 이벤트 버스 활용 : 발행자 구독자 패턴이라고 함

### 개발 방식 
- 애플리케이션 로직의 instance 생성
- 애플리케이션 로직과 무관한 새로운 instance 1개 생성
- 새 instance를 이용하여 이벤트 전달
- 보내는 컴포넌트에서는 $emit()
- 받는 컴포넌트에서는 $on() 구현

### 이벤트 버스에서의 발행자(Publisher)
- EventBus.$emit('event_name', ['parameter']) 
- event_name은 발행할 이벤트 이름
- parameter는 전달할 데이터 

### 이벤트 버스에서의 구독자(Subscriber)
- EventBus.$on('event_name', ['parameter'])
- event_name 구독할 이벤트 이름
- parameter 전달된 데이터

## Vue 라우터

### 라우팅이란? 
- 웹사이트는 다수의 페이지로 구성되어 있어서 웹사이트 내의 웹페이지들간의 이동과 접근에 대한 내용을 정의하는 것
- 현대 웹, 앱에서 자주 사용되는 싱글 페이지 애플리케이션(SPA, Single Page Application)에서 주로 사용

### 라우팅 장점
- 화면간의 전환이 매끄러움
- 요청 응답 진행시 발생되는 깜빡임 현상 해소 

### 뷰 라우터 참고
https://router.vuejs.org/kr/
https://router.vuejs.org/kr/installation.html


### 참고
template태그는 반드시 Root tag 구성후, 작업 진행해야한다
(단축키) ctrl + D 반복해서 사용하면 동일 키워드 선택 및 수정 가능