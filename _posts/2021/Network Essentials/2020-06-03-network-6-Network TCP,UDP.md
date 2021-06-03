---
title: Network-(5) Router
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

# Network Essentials 6부 TCP & UDP
TCP와 UDP 프로토콜은 TCP/IP 프로토콜 스택의 4계층에서 동작합니다.

## 4계층의 목적
- 목적지를 찾아가는 주소가 아니라 애플리케이션에서 사용하는 프로세스를 정확히 찾아가고 데이터를 분할한 패킷을 잘 쪼개 보내고 잘 조립하는 것 입니다.

## TCP 프로토콜의 기능
- TCP 프로토콜은 신뢰할 수 없는 공용망에서도 정보유실 없는 통신을 보장하기 위해 **세션을 안전하게 연결하고 데이터를 분할하고 분할된 패킷이 잘 전송되었는지 확인하는 기능**이 있습니다.
- 패킷에 번호(Sequence Number)를 부여하고 잘 전송되었는지에 대해 응답(Acknowledge Number)합니다.
- 패킷을 한꺼번에 얼마나 보내야 수신자가 잘 받아 처리할 수 있는지 전송 크기(Window Size)까지 고려해 통신합니다.

이러한 TCP의 다양한 역할 덕분에 네트워크 상태를 심각하게 고려하지 않고 특별한 개발 없이도 쉽고 안전하게 네트워크를 사용할 수 있습니다.

## 패킷순서와 응답번호
- TCP에서는 분할된 패킷을 잘 분할하고 수신 측이 잘 조합하도록 패킷에 순서를 주고 응답 번호를 부여합니다.
- **패킷에 순서를 부여하는 것을 시퀀스 번호**, **응답 번호를 부여하는 것을 ACK 번호**라고 부릅니다.







