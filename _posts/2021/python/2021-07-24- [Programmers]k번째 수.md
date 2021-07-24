---
title: 프로그래머스 :k번째 수
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
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
2에서 나온 배열의 3번째 숫자는 5입니다.
배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

제한사항
array의 길이는 1 이상 100 이하입니다.
array의 각 원소는 1 이상 100 이하입니다.
commands의 길이는 1 이상 50 이하입니다.
commands의 각 원소는 길이가 3입니다.


------

## 입력
array
[1, 5, 2, 6, 3, 7, 4]<br>
commands
[[2, 5, 3], [4, 4, 1], [1, 7, 3]]<br>


## 출력
[5, 6, 3]<br>


## 잘못된 풀이(1차)
```python
def solution(array, commands):
    answer = []
    temp = []
    
    for i in range(3):
        array[commands[i][0]-1:commands[i][1]].sort()
        answer[i] = temp[commands[i][2]-1]
            
    return answer

```
### 왜 틀렸는가?(1차)
- 

### 반성일지(1차)
- 

## 정답 풀이
```python

    
```

## 핵심 알고리즘 및 스킬
- 

## 다른 사람 풀이
```python

```

## 배워야할 점


    