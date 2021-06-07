---
title: Unity-(2) Unity3D Engine 입문
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

# 1. Unity 2부 Unity3D Engine 입문

# Unity3D 기본 용어

## 프로젝트(Project)
- 하나의 게임, 콘텐츠, 애플리케이션을 뜻한다

## 씬 (Scene)
- 게임의 장면이나 상태를 저장하는 단위
- 하나의 거대한 게임을 씬 단위로 관맇며, 코드를 이용해 이동이 가능하다
ex) Intro Scene, Menu Scene, Stage 1~N Scene, GameOver Scene, Ending Scene, etc ...

![그림1](https://user-images.githubusercontent.com/37354978/121036299-9f5e5900-c7e9-11eb-9724-ff0fd0761424.png)

## 게임 오브젝트 (GameObject)
### 씬에 배치되는 하나의 물체를 지칭하는 단위
- 모든 게임 오브젝트는 위치/회전/크기를 제어하는 "Transform" 컴포넌트를 가지고 있다
- 게임 오브젝트는 컴포넌트를 묶어서 관리하고, 접근할 수 있는 수단

### 게임 오브젝트에 원하는 컴포넌트를 추가하여 다양한 오브젝트 제작 가능
ex) 적 오브젝트, 나무 오브젝트, 공격 효과음 오브젝트, 불 이펙트 오브젝트 등

![그림2](https://user-images.githubusercontent.com/37354978/121036460-bb61fa80-c7e9-11eb-9900-70e7e16e19c1.png)

