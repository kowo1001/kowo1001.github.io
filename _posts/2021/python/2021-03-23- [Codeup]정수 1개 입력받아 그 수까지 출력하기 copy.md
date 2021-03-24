---
title: 코드업 정수 1개 입력받아 그 수까지 출력하기
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- PYTHON
toc: true
toc_sticky: true
toc_label: 목차
---

## 문제 
정수(0 ~ 100) 1개를 입력받아 0부터 그 수까지 순서대로 출력해보자.
------

## 제한 사항
- 섬의 개수 n은 1 이상 100 이하입니다.<br>
- costs의 길이는 ((n-1) * n) / 2이하입니다.<br>
- 임의의 i에 대해, costs[i][0] 와 costs[i] [1]에는 다리가 연결되는 두 섬의 번호가 들어있고, costs[i] [2]에는 이 두 섬을 연결하는 다리를 건설할 때 드는 비용입니다.<br>
- 같은 연결은 두 번 주어지지 않습니다. 또한 순서가 바뀌더라도 같은 연결로 봅니다. 즉 0과 1 사이를 연결하는 비용이 주어졌을 때, 1과 0의 비용이 주어지지 않습니다.<br>
- 모든 섬 사이의 다리 건설 비용이 주어지지 않습니다. 이 경우, 두 섬 사이의 건설이 불가능한 것으로 봅니다.<br>
- 연결할 수 없는 섬은 주어지지 않습니다.<br>

## 입력
정수 1개가 입력된다.
(0 ~ 100)

## 출력
0부터 그 수까지 줄을 바꿔 한 개씩 출력한다.

## 풀이
```python
import sys

n = int(sys.stdin.readline())

for i in range(n+1):
    print(i)
```
