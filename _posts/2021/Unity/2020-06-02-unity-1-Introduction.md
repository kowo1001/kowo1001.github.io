---
title: Unity-(1) Unity Introduction
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Unity
toc: true
toc_sticky: true
toc_label: 목차
---

# Unity 1부 Unity Introduction
Unity는 게임을 쉽고 빠르게 개발할 수 있게 하는 게임 엔진입니다.


## Unity 용어 
- Unity Hub : Unity Editor 버전 관리 프로그램 ( 설치, 삭제, 실행 )
- Unity Editor : 프로젝트를 생성하고, 게임 개발을 할 수 있는 프로그램


## Unity 설치
1. Unity 허브 설치
- 네이버 검색창에 '유니티 코리아' 라고 검색합니다

2. Unity 계정 생성하기

3. Unity Hub 라이선스 등록
- 라이선스 등록이 완료되면 유니티를 이용할 수 있습니다

4. 파일 경로 설정 및 Unity Editor 설치
- 모든 유니티에디터는 유니티 허브에 안에서 설치합니다
- Unity 버전에서 년도가 다르면 다른 게임 엔진 입니다

5. Unity Editor 설치 시 프로젝트를 빌드해서 내보내는 OS에 따라 Build Support 모듈을 추가로 설치할 수 있습니다


## Unity 허브
- 프로젝트 : 원하는 버전으로 Unity 프로젝트 생성 및 열기 
- 학습 : Unity에서 제공하는 Unity 콘텐츠 학습 자료
- 설치 : 원하는 버전의 Unity 설치


# 1. Unity3D Engine 입문

# Unity3D 기본 용어

## 프로젝트(Project)
- 하나의 게임, 콘텐츠, 애플리케이션을 뜻한다

## 씬 (Scene)
- 게임의 장면이나 상태를 저장하는 단위
- 하나의 거대한 게임을 씬 단위로 관맇며, 코드를 이용해 이동이 가능하다
ex) Intro Scene, Menu Scene, Stage 1~N Scene, GameOver Scene, Ending Scene, etc ...

![그림1](https://user-images.githubusercontent.com/37354978/122668637-f99ce800-d1f3-11eb-8094-ba0ff1944835.png)


## 게임 오브젝트 (GameObject)
### 씬에 배치되는 하나의 물체를 지칭하는 단위
- 모든 게임 오브젝트는 위치/회전/크기를 제어하는 "Transform" 컴포넌트를 가지고 있다
- 게임 오브젝트는 컴포넌트를 묶어서 관리하고, 접근할 수 있는 수단

### 게임 오브젝트에 원하는 컴포넌트를 추가하여 다양한 오브젝트 제작 가능
ex) 적 오브젝트, 나무 오브젝트, 공격 효과음 오브젝트, 불 이펙트 오브젝트 등

![그림2](https://user-images.githubusercontent.com/37354978/122668647-091c3100-d1f4-11eb-976f-7142f6252842.png)

