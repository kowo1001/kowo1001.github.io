---
title: Vue-(5) Web Basic
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Vue
toc: true
toc_sticky: true
toc_label: 목차
---

## <GET 방식>
- 입력한 데이터를 URL에 붙여서 전송한다. 데이터가 다 보이므로 보안에 취약하다.
- 전송할 수 있는 데이터는 256바이트를 넘을 수 없다.
- 전송속도는 POST방식 보다 빠르다.

## <POST 방식>
- 입력한 데이터를 본문안에 포함해서 전송한다.
- 입력한 데이터가 URL에 보이지 않으므로 GET방식 보다 보안에 우수하다.
- 전송할 데이터의 길이에 제한이 없다.
- 복잡한 형태의 데이터를 전송할 때 유용하다.
