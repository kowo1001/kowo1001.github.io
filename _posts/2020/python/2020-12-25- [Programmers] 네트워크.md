---
title: [Programmers] 네트워크
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

## 문제설명
네트워크란 컴퓨터 상호 간에 정보를 교환할 수 있도록 연결된 형태를 의미합니다. 예를 들어, 컴퓨터 A와 컴퓨터 B가 직접적으로 연결되어있고, 컴퓨터 B와 컴퓨터 C가 직접적으로 연결되어 있을 때 컴퓨터 A와 컴퓨터 C도 간접적으로 연결되어 정보를 교환할 수 있습니다. 따라서 컴퓨터 A, B, C는 모두 같은 네트워크 상에 있다고 할 수 있습니다.

컴퓨터의 개수 n, 연결에 대한 정보가 담긴 2차원 배열 computers가 매개변수로 주어질 때, 네트워크의 개수를 return 하도록 solution 함수를 작성하시오.
## 제한사항
숫자 N: 1 이상 10억 이하의 자연수<br>
숫자 K: 1 이상의 자연수

## 입출력예

|n|computers|return|
|:-------------------------:|:-------------------------------:|:-----------------------------:|
|3|[[1, 1, 0], [1, 1, 0], [0, 0, 1]]|2|
|3|[[1, 1, 0], [1, 1, 1], [0, 1, 1]]|1|


## 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```python
def solution(n, computers):
    answer = 0 # 네트워크 개수를 저장할 변수
    bfs = []    # 탐색을 위한 큐
    visited = [0]*n     # 방문한 노드를 체크해둘 리스트
    
    while 0 in visited: # visited 리스트의 모든 값에 방문 표시가 되어있을 때까지 반복
        x = visited.index(0) # 첫 노드(인덱스)  
        bfs.append(x)   # 큐에 첫 노드(인덱스) 추가
        visited[x] = 1 # 노드 방문 표시
        
        while bfs:  # 큐가 값이 존재하면 반복문 수행
            node = bfs.pop(0)   # 큐의 앞에서부터 노드(인덱스) 꺼내기
            visited[node] = 1   # 노드 방문 표시
            for i in range(n): # 꺼낸 노드의 인접 노드를 방문하기 위한 반복문 수행
                if visited[i] == 0 and computers[node][i] == 1: # 인접 노드이고, 방문된 적이 없는 경우
                    bfs.append(i) # 큐에 추가
                    visited[i] = 1 # 방문했음을 표시
        answer += 1 # 한 네트워크의 탐색을 마치면 개수 추가
    return answer
```
</div>
</details>

