---
title: Network-(1) 핵심 개념
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Spring
toc: true
toc_sticky: true
toc_label: 목차
---

## 인캡슐레이션과 디캡슐레이션

- 인캡슐레이션, 디캡슐레이션 과정을 통해 데이터가 전송되는 과정
- 각 계층 헤더를 이용해 송신자 계층과 수신자 계층 간의 논리적 통신 과정

인캡슐레이션 : 트랜스포트 계층(Transport) --> 네트워크 계층(Network) --> 데이터 링크 계층(Data Link) --> 피지컬 계층(Physical)
디캡슐레이션 : 피지컬 계층(Physical) --> 데이터 링크 계층(Data Link)--> 네트워크 계층(Network) --> 트랜스포트 계층(Transport)

실제 데이터는 상위 계층 --> 하위 계층, 하위 계층 --> 상위 계층으로 전달되고 헤더 정보는 각 계층끼리 전달됩니다.
만약 4계층에서 헤더를 추가했다면 그 정보는 받는 쪽의 4계층에서 확인합니다.


