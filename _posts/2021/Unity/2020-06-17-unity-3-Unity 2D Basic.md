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

### 두 오브젝트가 충돌하려면?
- 서로 다른 두 오브젝트가 충돌하기 위한 필수 조건
- 1. 두 오브젝트 모두 충돌 범위인 Collider2D 컴포넌트를 가지고 있어야 한다
- 2. 둘 중 하나 이상의 오브젝트가 물리 처리를 담당하는 Rigidbody2D 컴포넌트를 가지고 있어야 한다
![그림7](https://user-images.githubusercontent.com/37354978/122529770-c96d1200-d058-11eb-8e69-e3fc2969e78a.png)

![그림8](https://user-images.githubusercontent.com/37354978/122530711-bdce1b00-d059-11eb-98ce-dda45896055e.png)
- Tip. Rigidbody2D는 오브젝트에 물리를 적용, 처리하는 클래스로 클래스 내부에 이동 관련 함수가 작동하고 있다
단지, 이동 방향과 속도를 나타내는 속력(velocity)의 초기 값이 (0,0)이어서 움직이지 않는 것이다
- 코드와 같이 기존의 transform.position += ... 이동 코드 대신 Rigidbody2D에 있는 속력(velocity) 변수만 설정해주면 Rigidbody2D에 의해서 이동이 가능하다

**04:35 게임 오브젝트 충돌 처리 실습 난이도 상..**

- 게임 내에선 오브젝트가 단순히 충돌했다!로 끝나는 것이 아닌 충돌에 의해 함수가 호출되고, 함수에서 다양한 역할을 하게 된다
**아이템을 획득하거나 적을 공격하거나 함정을 밟아 장애물이 튀어나온다거나와 같이..**

- 물리적인 충돌이 일어나고, 이벤트 함수가 호출
- **OnCollisionEnter2D()** : 두 오브젝트가 충돌하는 순간 1회 호출
- **OnCollisionStay2D()** : 충돌 직후 맞닿아 있는 동안 매 프레임 호출
- **OnCollisionExit2D()** : 두 오브젝트가 떨어져서 충돌이 종료되는 순간 1회 호출

매개변수 Collision2D collision
- 현재 컴포넌트를 가지고 있는 오브젝트에 부딪힌 오브젝트 정보
![그림9](https://user-images.githubusercontent.com/37354978/122533244-4b126f00-d05c-11eb-8108-ed14e1e66fc1.png)

- 물리적인 충돌 없이 이벤트 함수가 호출
- OnTriggerEnter2D() : 두 오브젝트가 충돌하는 순간 1회 호출
- OnTriggerStay2D() : 충돌 직후 맞닿아 있는 동안 매 프레임 호출
- OnTriggerExit2D() : 두 오브젝트가 떨어져서 충돌이 종료되는 순간 1회 호출

매개변수 Collider2D collision
- 현재 컴포넌트를 가지고 있는 오브젝트에 부딪힌 오브젝트 정보
![그림10](https://user-images.githubusercontent.com/37354978/122534349-6467eb00-d05d-11eb-82ef-f032fe98191a.png)

- 내가 소속된 게임오브젝트의 컴포넌트 정보
- GetComponent<컴포넌트>()
- 내가 아닌 다른 게임오브젝트의 컴포넌트 정보
- 게임오브젝트.GetComponent<컴포넌트>()
- 다른 게임오브젝트의 정보는 코드와 같이 미리 변수를 만들어서 게임오브젝트 정보를 저장해두고 사용할 수도 있고, 유니티에서 제공하는 함수를 이용해 탐색할 수도 있다

- LeftTilt & RightTilt
![그림11](https://user-images.githubusercontent.com/37354978/122534974-0a1b5a00-d05e-11eb-8825-58f0505ee6eb.png)

## 게임오브젝트 생성 함수 Instantiate()

### 프리팹(Prefab)이란 ?
- 게임(Hierarchy View)에 존재하는 게임오브젝트를 Project View에 파일로 저장해 둔 것
- 1. 원하는 형태로 게임오브젝트를 꾸며준다. (적 캐릭터, 아이템 등)
- 2. Hierarchy View의 게임오브젝트를 Project View로 드래그&드롭한다
- 3. Hierarchy View에 있는 게임 오브젝트를 삭제한다














