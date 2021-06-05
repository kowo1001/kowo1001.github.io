---
title: Network-(8) VLAN
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

# Network Essentials 7부 MAC주소
TCP와 UDP 프로토콜은 TCP/IP 프로토콜 스택의 4계층에서 동작합니다.

## VLAN (Virtual LAN) 이란?
- 하나의 네트워크로 논리적인 네트워크로 분할
- 특정 VLAN에서 전달된 트래픽은 해당 VLAN에 속한 포트로만 전달
- 하나의 VLAN = 하나의 브로드캐스트 도메인 = 하나의 논리적 네트워크

## VLAN 장점
**네트워크 트래픽 감소**
- ARP Request, NetBIOS Name Query 등과 같은 브로드캐스트 프레임
전달 범위를 제한함으로써 네트워크 트래픽 감소
**보안 취약점 발생 가능성 감소**
- ARP Request, NetBIOS Name Query 등과 같은 브로드캐스트 프레임
제한함으로써 웜이나 바이러스의 전파 범위를 제한함

VLAN을 통해 논리적인 네트워크로 나눔으로써 웜이나 바이러스를 막을 수 있게 됩니다