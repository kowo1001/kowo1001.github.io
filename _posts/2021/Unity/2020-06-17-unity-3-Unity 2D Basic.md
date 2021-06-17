---
title: Unity-(3) Unity 2D Basic
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

# 1. Unity 2D Basic


## Time.deltaTime
- 두 컴퓨터에서 캐릭터 이동을 했을 때
- 캐릭터의 Update() 1회 당 이동거리를 5m 라고 할 때
- 사양이 좋지 않은 컴퓨터는 60초에 Update()가 60회 호출
- 사양이 좋은 컴퓨터는 60초에 Update()가 120회 호출
![그림1](https://user-images.githubusercontent.com/37354978/122320316-048a1b00-cf5d-11eb-8cf1-018d2a5a96b6.png)


## Time.deltaTime 이란?
- 이전 Update() 종료부터 다음 Update() 시작까지의 시간
- 즉, 업데이터 사이의 시간
- ex) 1분(60초)에 Update()가 60번 호출된다면 Time.deltaTime은 1

- 사양이 좋지 않은 컴퓨터는 60초에 Update()가 60번 호출
- Time.deltaTime의 값은 1
- 사양이 좋은 컴퓨터는 60초에 Update()가 120번 호출
- Time.deltaTime의 값은 0.5

**이동거리 = 방향(Direction) + 속도(Speed) * Time.deltaTime**
![그림2](https://user-images.githubusercontent.com/37354978/122320785-c50ffe80-cf5d-11eb-95fd-d5849cf8e978.png)

### Time.deltaTime 관련 코드
```c#
// 새로운 위치 = 현재 위치 + (방향 * 속도)
transform.position = transform.position + new Vector3(1, 0, 0) * 1;

// 이렇게도 표현 가능합니다.
// transform.position += Vector3.right * 1;

// 새로운 위치 = 현재 위치 + (방향 * 속도)
transform.position += Vector3.right * 1 * Time.deltaTime;
```

## Input Class
- 입력에 관련된 모든 프로퍼티, 메소드 제공
![그림3](https://user-images.githubusercontent.com/37354978/122321753-592e9580-cf5f-11eb-853f-fdbf9e89103e.png)

## 물리와 관련된 컴포넌트
- 2D : Component - Physics 2D
- 3D : Component - Physics

## Rigidbody2D 컴포넌트 
- 2차원 공간에서 오브젝트의 물리와 중력을 담당하는 컴포넌트
![그림4](https://user-images.githubusercontent.com/37354978/122354773-48484900-cf8c-11eb-9cc5-7a326a7367ee.png)

## Collider2D 컴포넌트
- 2차원 공간에서 오브젝트의 충돌 범위를 나타내는 컴포넌트
- 충돌 범위의 생김새나 특징에 따라 "OO Collider 2D"와 같이 이름을 명명함
- Box Collider 2D
- Circle Collider 2D
- Edge Collider 2D
- Polygon Collider 2D
- Capsule Collider 2D
- Composite Collider 2D
![그림5](https://user-images.githubusercontent.com/37354978/122356033-61052e80-cf8d-11eb-9c5f-c574ab01fe8e.png)

### Box Collider 2D
- 특징 : 사각형 범위의 충돌 범위
- 변수 :
- 1) Offset : 충돌 범위 중심점
- 2) Size : 충돌 범위 크기

### Circle Collider 2D
- 특징 : 원 범위의 충돌 범위. 연산 속도가 가장 빠름.
- 변수 :
- 1) Offset : 충돌 범위 중심점
- 2) Radius : 충돌 범위 반지름 크기

### Edge Collider 2D
- 특징 : 점의 개수, 각 점의 위치를 설정할 수 있기 때문에 다양한 곡선 형태로 충돌 범위 표현 가능 (주로 2D 게임의 바닥 충돌에 사용)
- 변수 :
- 1) Offset : 충돌 범위 중심점
- 2) Edge Radius : 충돌 선의 두께
- 3) Points : 선을 이루는 점의 개수와 각 점의 위치

### Polygon Collider 2D
- 특징 : 텍스처의 모양과 비슷한 형태로 충돌 범위 생성 (Edge와 마찬가지로 Points 수정 가능)
- 변수 : 
- 1) Offset : 충돌 범위의 중심점
- 2) Points : 선을 이루는 점의 개수와 각 점의 위치 

### Capsule Collider 2D
- 특징 : 캡슐 모양의 충돌 범위 생성 (사람 형태의 캐릭터에 주로 사용)
- 변수 : 
- 1) Offset : 충돌 범위 중심점
- 2) Size : 충돌 범위 크기
- 3) Direction : 둥근 캡슐이 표현되는 방향 (Vertical : 위/아래, Horizontal : 좌/우)

### Composite Collider 2D
- 특징 : 다른 게임오브젝트의 Collider 2D들을 하나로 묶어주는 역할 (Box Collider 2D, Polygon Collider 2D만 가능)
![그림6](https://user-images.githubusercontent.com/37354978/122361985-b5f77380-cf92-11eb-8a4b-41f9a06ec6fb.png)












