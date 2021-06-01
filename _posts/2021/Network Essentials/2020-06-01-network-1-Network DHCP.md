---
title: Network-(1) DHCP
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

# Network Essentials 1부 DHCP(Dynamic Host Configuration)


## What DHCP?
- 호스트가 네트워크와 통신하려면 물리적 네트워크 구성은 물론 IP 주소, 서브넷 마스크, 게이트웨이와 같은 네트워크 정보와 DNS 주소 설정이 필요합니다.
- 수동으로 IP와 네트워크 정보를 직접 설정하는 것을 '정적 할당'이라고 하고 자동으로 설정하는 것을 '동적 할당'이라고 합니다.
- 핸드폰이나 PC를 사용할 때, IP를 별도로 설정하지 않아도 네트워크에 쉽게 접속되므로 특별한 경우를 제외하고 동적 할당 방식을 기본으로 사용합니다. 가정에서 사용하는 공유기도 동적 할당 방식을 기본으로 사용합니다.
- **이렇게 IP를 동적으로 할당하는데 사용되는 프로토콜이 바로 DHCP(Dynamic Host Configuration) 입니다.** 

## DHCP 이점
- DHCP를 사용하면 사용자가 직접 입력해야 하는 IP 주소, 서브넷 마스크, 게이트웨이, DNS 정보를 자동으로 할당받아 사용할 수 있습니다.
- IP가 자동으로 관리되므로 사용자가 직접 입력하면서 발생할 수 있는 설정 정보 오류나 중복 IP 할당과 같은 문제를 예방할 수 있습니다.
- 별도의 IP 설정 작업이 필요없어 사용자와 관리자 모두 편리하게 네트워크에 접속할 수 있습니다.
- 사용하지 않는 IP 정보는 회수되어 사용하는 경우에만 재할당되어 사용자 이동이 많고 한정된 IP 주소를 가진 경우 유용하게 사용될 수 있습니다.

## DHCP 프로토콜


