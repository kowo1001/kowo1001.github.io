---
title: Unity-(4) Unity Input Basic
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

# 1. Unity Input Basic


## Input Class 
- 유니티에서 제공하는 입력과 관련된 모든 메소드가 정의되어 있는 클래스
- PC(키보드, 마우스), Mobile(터치, 가속도 센서, 위치 정보)
![그림1](https://user-images.githubusercontent.com/37354978/122495425-f9022700-d024-11eb-8ac3-d5024872ece5.png)

## GetKey~()
### 키보드 키 입력 여부를 확인하고 싶을 때 사용하는 함수
- 매개변수는 **KeyCode 열거형에 정의되어 있는 변수** 또는 **문자열(string)** 사용
- 반환되는 값은 조건에 만족할 때 true, 만족하지 않을 때 false가 반환

### GetKeyDown()
- 매개변수에 입력되는 **키를 누를 때 1회 true를 반환**
- bool result = Input.GetKeyDown(KeyCode key);
- bool result = Input.GetKeyDown(string key);

### GetKey()
- 매개변수에 입력되는 **키를 누르고 있는 동안 매 프레임 true를 반환**
- bool result = Input.GetKey(KeyCode key);
- bool result = Input.GetKey(string key);

### GetKeyUp()
- 매개변수에 입력되는 **키를 눌렀다 뗄 때 1회 true를 반환**
- bool result = Input.GetKeyUp(KeyCode key);
- bool result = Input.GetKeyUp(string key);

## KeyCode 열거형
- GetKey~() 함수의 매개변수로 사용
![그림2](https://user-images.githubusercontent.com/37354978/122496128-361ae900-d026-11eb-812b-167a87682b5e.png)

## anyKey~, inputString
### anyKeyDown
- 키보드 또는 마우스 중 아무 키나 누를 때 1회 true를 반환
- bool result = Input.anyKeyDown;

### anyKey
- 키보드 또는 마우스 중 아무 키나 누르고 있는 동안 매 프레임 true를 반환
- bool result = Input.anyKey;

### inputString
- 이번 프레임에 입력된 정보(키보드 키)를 저장하고 있음
- string key = Input.inputString

## GetMouseButton~()
- 마우스 키 입력 여부를 확인하고 싶을 때 사용하는 함수
- 매개변수는 정수 0,1,2 (0 : 왼쪽 버튼, 1 : 오른쪽 버튼, 2 : 휠 버튼)
- 반환되는 값은 조건에 만족할 때 true, 만족하지 않을 때 false가 반환

### GetMouseButtonDown()
- 매개변수로 입력되어 있는 마우스를 누를 때 1회 true를 반환
- bool result = Input.GetMouseButtonDown(int button);

### GetMouseButton()
- 매개변수로 입력되어 있는 마우스를 누르고 있는 동안 매 프레임 true를 반환
- bool result = Input.GetMouseButton(int button);

### GetMouseButtonUp()
- 매개변수로 입력되어 있는 마우스를 눌렀다 뗄 때 1회 true를 반환
- bool result = Input.GetMouseButtonUp(int button);

## mouseScrollDelta
- **마우스 휠**을 스크롤 했을 때 **스크롤된 방향 정보** 제공
- 반환되는 값은 Vector2로 float x, float y의 2개 데이터가 나오지만 일반 마우스의 휠은 위/아래로만 이동이 간으하기 때문에 y데이터만 사용
- y가 **'+'이면 전방 방향**으로 휠을 밀 때 (0,1)
- y가 **'-'이면 사용자 방향**으로 휠을 당길 때 (0,-1)
- Vector2 scroll = Input.mouseScrollDelta;

## mousePosition
- 게임의 좌하단을 기준(0,0)으로 **현재 마우스 좌표 값 반환**
- Vector3 position = Input.mousePosition;

## InputManager
- Input.GetKey~()를 이용하면 하나의 키에 대한 검사만 가능하지만
InputManager의 단축키 시스템을 이용해 2개 or 4개의 키를 한 세트로 묶어서 검사할 수 있다
- 이러한 단축키 등록은 Project Settings View의 InputManager에서 하고,
키 사용은 Input.GetAxis~(), Input.GetButton()로 할 수 있다.














