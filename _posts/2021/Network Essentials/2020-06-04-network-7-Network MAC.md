---
title: Network-(7) MAC주소
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

## MAC 주소란?
각 IP 제품에는 맥이라는 번호가 정해져 있습니다
MAC은 16진수로 12자리 48bit 숫자로 구성되어 있습니다
앞 여섯자리 24bit는 제조사에 대한 정보, 
뒤 여섯 자리 24bit는 제조사가 붙이는 일련번호 입니다
16진수이기 때문에 F이상의 알파벳이 나올 수 없습니다

## MAC주소 특징
- 네트워크가 되는 모든 장비는 맥주소를 가지고 있습니다
- 노트북의 유선랜, 무선랜은 물론이고, 블루투스, 공유기, 스위치, IoT 장비까지 모두 맥을 가지고 있습니다.
- 맥주소는 하드웨어에 적용된 물리적인 주소로, 중복이나 변경이 불가합니다

## MAC주소 확인 방법
컴퓨터의 맥주소를 확인하는 방법은
명령프롬프트에서 getmac이라고 치시거나, ipconfig /all 을 하시면 됩니다
물리적인 주소가 맥주소인 것입니다.
다만, 공유기의 경우 맥을 차단하는 경우가 있습니다
이를 우회하거나, iptime의 공유기 기능 중에 트윈아이피 기능을 사용할 때
맥을 공유기의 맥으로 덮어씌울 수가 있습니다.
절대로! 공유기의 MAC이 바뀌는 것은 아닙니다

## MAC주소 용도
맥주소는 하드웨어 별로 고유의 주소값을 가지고 있기 때문에 많은 용도로 사용됩니다
- 가장 대표적으로, 공유기의 자동 IP 할당할 때는 맥주소를 기준으로 합니다
- cctv 쪽에서는 시리얼넘버와 같이 이용이 되며, 암호를 찾거나 기계를 구분하거나
녹화기에서 카메라를 등록하는 기준으로 사용되기도 합니다
- 네트워크 장비중에서 스위치는 포트에 연결된 맥주소를 알아내서 데이터를 전송할때 
어떤 포트로 전송할지 결정하는데 사용합니다.

## MAC주소 테이블
관리형 스위치 경우에는 맥주소 테이블을 확인할 수 있습니다
이 화면이 관리형 스위치 화면 입니다
맥 테이블은 내가 관리하고 있는 맥주소들을 테이블화 해서 보실 수가 있습니다.
일반적인 스위치들은 화면이 없기 때문에 확인은 불가능하며, 관리형 스위치에만 해당합니다

## MAC주소 테이블 초기화
arp-a : 맥테이블의 리스트 확인
arp-d* : 맥테이블 초기화
다시 arp-a를 하면 리스트가 심플하게 나옵니다-> 맥테이블이 초기화 된 것 입니다


