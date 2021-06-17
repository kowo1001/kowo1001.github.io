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






