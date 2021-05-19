---
title: PlayFab-(1) 핵심 개념
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

ⓒ Copyright Microsoft Corporation. All rights reserved.

## PlayFab 용어 정리
- PlayStream은 게임의 전체 데이터 흐름을 단일 이벤트 스트림으로 통합하는 이벤트 처리 시스템입니다.
- CloudScript는 원격 서버에 거주하는 JavaScript 코드로 규칙에서 또는 클라이언트에서 직접 실행할 수 있습니다.
- Playfab insights는 서비스에서 생성 되거나 외부 원본에서 가져온 경우와 관계 없이 데이터에 대 한 중앙 리포지토리를 제공하는 프리미엄 playfab 제공입니다.

## PlayFab Questions

### Xbox

#### Xbox가 무엇인가요 ?
- 마이크로소프트에서 제작하는 가정용 게임기 시리즈이자, 윈도우(PC)와 엑스박스(콘솔)을 통합하는 게임 서비스.
- 현재는 게임기 사업을 제외하면 Windows 10의 자체 게임 서비스 명칭만으로 사용되고 있다.

#### Xbox Live가 무엇인가요 ?
- 엑스박스 게임기와 Windows 10용 온라인 게이밍 서비스
- 마이크로소프트에서 운영하는 콘솔 사상 최초의 통합형 온라인 서비스. 
- 콘솔 게임기 최초의 유료 온라인 게임 서비스이기도 하다. 추후 엑스박스 라이브를 토대로 온라인 스토어가 제작되었다.
- 2002년 11월 15일 미국에서 서비스를 시작하여 현재 총 30개의 국가에서 서비스 중이다. 
- 기존의 게임마다 따로따로 설정하고 따로따로 가입했던 온라인 서비스에 비하면 확실히 편리하다. 
- 또한 서버를 전부 마이크로소프트가 관리하고 있다는 것도 특징.
- 플레이 스테이션 브랜드의 온라인 서비스인 PSN이 PS4 들어 나온 유료 요금제(PSN+)도 XBL골드의 콘텐츠를 거의 빼다박았다.
- 윈도우 폰의 출시 이후부터는 마이크로소프트가 보유한 모든 플랫폼의 통합 게임 ESD로서 그 입지가 확대되었고, 
- 점점 그 범위를 넓혀서 구글 안드로이드, iPhone, 닌텐도 스위치 등 타 플랫폼에도 접근하는 중이다.

## Azure PlayFab 멀티 플레이

### 멀티 플레이 이해 
멀티 플레이어 시나리오에 중점을 둘 수 있는 서비스 제공

- 순위표 : 통계 및 순위표를 사용하여 플레이어 작업 추적 및 응답
- 엔터티 그룹 : 플레이어 및 신호 동작의 영구 그룹과 임시 그룹을 만듭니다 
- 매치 메이킹 : 사용자 지정 매치 메이킹 규칙을 배포하여 빠르게 플레이어 그룹화
- 파티 : 네트워킹 및 접근성 높은 게임 채팅을 사용하여 플레이어 연결
- 서버 : Azure에서 사용자 지정 멀티 플레이어 서버를 동적으로 크기 조정

ⓒ Copyright Microsoft Corporation. All rights reserved.