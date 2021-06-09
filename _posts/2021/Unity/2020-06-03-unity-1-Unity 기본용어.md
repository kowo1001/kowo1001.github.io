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

- Sprite Renderer 컴포넌트 : 2차원의 이미지를 화면에 출력
- Mesh Renderer 컴포넌트 : 3차원의 오브젝트(물체)를 화면에 출력
- Audio Source 컴포넌트 : AudioClip 변수에 등록된 사운드 에셋을 재생

## 컴포넌트 (Component) [C# Script]
- 게임 오브젝트에 부착할 수 있는 C# 스크립트 파일을 지칭하는 단위
- 게임 오브젝트에 컴포넌트를 부착하여 게임 오브젝트에 여러 기능을 부여 

![그림3](https://user-images.githubusercontent.com/37354978/121276696-1ee34980-c90a-11eb-8f62-9a8866e1759f.png)

## 에셋 (Asset)
- 프로젝트 내부에서 사용하는 모든 리소스를 지칭하는 단위 (Project View)
- Audio, 3D Model, Animaion, Texture, Script, Prefab, etc ..

![그림4](https://user-images.githubusercontent.com/37354978/121276702-2145a380-c90a-11eb-919a-00c8c0a784ff.png)

## 프리팹 (Prefab)
- Hierarchy View에 있는 게임 오브젝트를 파일 형태로 저장하는 단위
- 주로 게임 중간에 생성되는 게임 오브젝트를 프리팹으로 저장해두고 사용한다
### 프리팹의 장점
- 동일한 게임 오브젝트를 여러 Scene이나 게임 월드 특정 장소에 배치할 때 Project View에 저장되어 있는 프리팹을 Drag & Drop하여 배치할 수 있다
- 기획상의 변경이 있을 때 프리팹 원본을 갱신하게 되면 모든 씬에 복사되어 배치된 게임 오브젝트 들도 원본과 동일하게 업데이트 된다

![그림5](https://user-images.githubusercontent.com/37354978/121276742-34f10a00-c90a-11eb-886e-0e660af42a6a.png)

- Project, Scene, GameObject, Component, Asset 관계도

![그림6](https://user-images.githubusercontent.com/37354978/121276747-37536400-c90a-11eb-9582-014ebb74a99b.png)
![그림7](https://user-images.githubusercontent.com/37354978/121276749-391d2780-c90a-11eb-8181-0c6f5f65e5b2.png)
![그림8](https://user-images.githubusercontent.com/37354978/121276752-3a4e5480-c90a-11eb-9dc3-fddc9d23f70d.png)
![그림9](https://user-images.githubusercontent.com/37354978/121276759-3d494500-c90a-11eb-89c1-7bf861b2cac8.png)

## Unity3D 좌표 체계
- Unity3D의 게임 월드는 왼손 좌표계를 기준으로 x,y,z축을 나타낼 수 있다.

2. 게임 오브젝트의 종류
## 게임 오브젝트 메뉴
## 빈 오브젝트 (Empty Object)
- 모든 오브젝트가 가지는  "Transform" 컴포넌트만 붙어있는 오브젝트
![그림10](https://user-images.githubusercontent.com/37354978/121276763-3fab9f00-c90a-11eb-80c6-233f636b92b4.png)

## 3D Object
- 게임 화면에 배치할 수 있는 3D 오브젝트
![그림11](https://user-images.githubusercontent.com/37354978/121276768-40dccc00-c90a-11eb-8140-2bda5d56e61a.png)

## Cube
- 한변의 길이가 1이고, 6개의 면으로 이루어진 육면체
- 텍스처를 적용하면 모든 면에 동일한 이미지가 표현된다.

## 2D Object
## Effect
## Audio
## Video
##UI


3. Camera & Light

4. 게임 오브젝트 Texture 출력