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

## PlayFab 이란 ?
- 라이브 게임의 빌드와 운영을 위한 종합적인 LiveOps 백 엔드 플랫폼
- 관리되는 게임 서비스, 실시간 분석 및 LiveOps를 사용하여 라이브 게임을 위한 완벽한 백엔드 플랫폼 입니다.


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


#### PlayFab 활용하는 게임 회사
Playfab을 쓰는 업체들은 보시다시피 캡콤, 반다이남코, 로비오(앵그리버드 개발사), 미니클립 등 해외 유명 게임회사들이 있습니다.


#### PlayFab 주요 기능
Playfab은 모바일 게임이나 PC 게임 개발을 위한 게임서버 기능들을 두루 갖추고 있습니다.

1. 퀵로그인(페이스북,구글,게임센터,스팀,트위치 등)
2. 커스텀 로직 개발 기능 (아이템 인벤토리,캐릭터 강화,합성,조합 등등)
3. 통계 기능 (업적,부분유료화를 위한 기반 정보 등)
4. 모바일 푸시 기능, 전체 공지 뿌리기 기능
5. 플레이어 정보 검색 기능 (가령 친구 캐릭터를 게임 플레이에 가져다 쓰기 용도 등)
6. 어뷰징,해킹,불량 유저 제어 기능
7. 리더보드 즉 랭킹 시스템

[출처] : http://blog.naver.com/PostView.nhn?blogId=imays&logNo=221074670286&redirect=Dlog&widgetTypeCall=true&directAccess=false


ⓒ Copyright Microsoft Corporation. All rights reserved.