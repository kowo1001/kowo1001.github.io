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
![그림3](https://user-images.githubusercontent.com/37354978/122520027-1b5c6a80-d04e-11eb-91b1-fb2f9a265646.png)

## GetAxis~()
### 키보드 또는 마우스 키 입력 여부를 확인하고 싶을 때 사용하는 함수
- GetKey~(), GetMouseButton~()과 차이점은 동시에 여러 키 정보를 확인 가능
- 매개변수는 InputManager에 등록되어 있는 단축키 명을 문자열(string)로 사용
- 반환되는 값은 긍정 키 : +, 부정 키 : -, 아무 키도 안 누르면 : 0

### GetAxis()의 반환 데이터
- 키를 누르고 있으면 0에서 1(or -1)까지 점점 증가하여 1(or -1)에 도달하고 키에서 손을 떼기 전까지 1(or -1)이 반환되며,
떼었다 다시 누르면 0부터 다시 증가

### GetAxisRaw()의 반환 데이터
- 반환되는 값은 -1,0,1의 3가지 숫자만 반환
![그림4](https://user-images.githubusercontent.com/37354978/122520827-151abe00-d04f-11eb-9557-cd2ea4befffd.png)

## GetButton~()
- 키보드 또는 마우스 키 입력 여부를 확인하고 싶을 때 사용하는 함수
- 동시에 2개의 키 정보를 확인 가능
- 매개변수는 InputManager에 등록되어 있는 단축키명을 문자열(string)로 사용
- 반환되는 값은 true, false
- bool Input.GetButtonDown(string key);  단축키를 누를 때 1회 true를 반환
- bool Input.GetButton(string key);  단축키를 누르고 있을 때 매 프레임 true를 반환
- bool Input.GetButtonUp(string key);  단축키를 눌렀다 뗄 때 1회 true를 반환

- GetAxis(), GetAxisRaw()는 이동과 같이 +, -의 값이 필요할 때 사용하고, GetButton()은 공격과 같이 눌렀는지 안 눌렀는지 판단할 때 사용
- **GetButton()은 앞에 배운 GetKey()와 흡사한데 매개변수로 사용하는 문자열이 InputManager에 정의된 단축키라는 점이 다름**

## InputField - TextMeshPro GameObject
- 키보드를 이용해 문자열을 입력할 때 사용하는 상호작용 UI
- 아이디/패스워드 입력, 채팅 등에 사용

![그림5](https://user-images.githubusercontent.com/37354978/122521943-5f506f00-d050-11eb-969a-fe0e2d6501cb.png)
![그림6](https://user-images.githubusercontent.com/37354978/122522063-80b15b00-d050-11eb-884b-cd686f6eaa95.png)

## TextMeshPro - InputField Component
![그림7](https://user-images.githubusercontent.com/37354978/122523216-c0c50d80-d051-11eb-8447-b9285628fde2.png)
### Text Viewport
- 입력된 문자열이 표시되어야 하는 영역을 나타내는 RectTransform

### Text Component
- 우리가 입력한 문자열을 표시하는 텍스트 UI

### Text
- 우리가 입력한 문자열 내용
- Text Component에 동일한 내용이 입력된다
![그림8](https://user-images.githubusercontent.com/37354978/122523731-4e086200-d052-11eb-8bcc-67dd7a800553.png)
![그림9](https://user-images.githubusercontent.com/37354978/122523740-506abc00-d052-11eb-9d2a-f0e345393cea.png)

### Line Type
![그림10](https://user-images.githubusercontent.com/37354978/122523907-814af100-d052-11eb-95b7-6f7f3bfbbf98.png)
![그림11](https://user-images.githubusercontent.com/37354978/122524056-aa6b8180-d052-11eb-9220-534209a1fd4d.png)

### Content Type
![그림12](https://user-images.githubusercontent.com/37354978/122524182-d0912180-d052-11eb-9dab-0ac6fde78073.png)
![그림13](https://user-images.githubusercontent.com/37354978/122524265-e7377880-d052-11eb-9158-b959f677fdd2.png)
![그림14](https://user-images.githubusercontent.com/37354978/122524357-01715680-d053-11eb-87f1-9422890a4a2a.png)
![그림15](https://user-images.githubusercontent.com/37354978/122524493-2960ba00-d053-11eb-9378-36f722d6212d.png)
![그림16](https://user-images.githubusercontent.com/37354978/122524618-52814a80-d053-11eb-9b2d-0f19db6adf8a.png)

### Input Type
![그림17](https://user-images.githubusercontent.com/37354978/122524770-7e9ccb80-d053-11eb-8144-95960e96f4ca.png)

### Keyboard Type
![그림18](https://user-images.githubusercontent.com/37354978/122524919-a8ee8900-d053-11eb-891d-c573953266ec.png)

### Character Validation
![그림19](https://user-images.githubusercontent.com/37354978/122525106-db988180-d053-11eb-9d69-c2029979f1cf.png)

### TextMeshPro - InputField Component Event Method
![그림20](https://user-images.githubusercontent.com/37354978/122525296-11d60100-d054-11eb-893c-059f74076948.png)







