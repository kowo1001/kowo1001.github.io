---
title: Network-(2) NETBIOS
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Network
toc: true
toc_sticky: true
toc_label: 목차
---

# Network Essentials 2부 NETBIOS


## What NETBIOS?
- 넷바이오스(NetBIOS, Network Basic Input/Output System)는 **OSI 모형의 세션 계층에 관련된 서비스들을 제공하여 개개의 컴퓨터의 애플리케이션들이 근거리 통신망을 통해 통신할 수 있게 한다.**
- 네트워크에 대한 기본적인 입출력((Net + BIOS) 이라는 뜻으로 합성된 용어
- 프로토콜 보다는 소프트웨어 인터페이스 및 이름 명명법을 정의하고 있는 일종의 API
- IBM PC 네트워크 LAN 기술을 이용한 통신 소프트웨어용 API 

참고 ) 일반적으로 통신 프로토콜 만을 가리키는 경우, NetBIOS 대신에 NetBEUI라고 부름


## NETBIOS가 제공하는 3가지 서비스
- 넷바이오스는 아래와 같은 세 개의 서비스를 제공한다 :

### 이름 서비스 (NetBIOS-Name Service)
- 이름 : 16 바이트의 알파벳 문자 또는 숫자의 조합
- 대문자로 된 컴퓨터 이름 (15 바이트) + name type (1 바이트)
- NetBIOS 이름공간(Name Space)는 평평하다. 즉 DNS 처럼 계층적이지 않다.

### 데이터그램 분배 서비스 (NetBIOS-DGM)
- 데이터그램 모드는 비연결형(connectionless, 각 메시지가 독립적으로 전송)이다.
- 메시지가 보다 작으며 응용 프로그램이 통신 에러의 발견과 회복을 수행한다.
- 또한 메시지를 LAN의 모든 컴퓨터에 전송시키는 브로드캐스트(방송)을 지원한다.

### 세션 서비스 (NetBIOS-SSN)
- 두 컴퓨터가 통신할 수 있는 연결을 성립시키고, 보다 큰 메시지가 처리될 수 있게 한다.
- 통신 에러의 발견과 회복을 제공한다.


