---
title: [Programmers] 구명보트
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
무인도에 갇힌 사람들을 구명보트를 이용하여 구출하려고 합니다. 구명보트는 작아서 한 번에 최대 2명씩 밖에 탈 수 없고, 무게 제한도 있습니다.

예를 들어, 사람들의 몸무게가 [70kg, 50kg, 80kg, 50kg]이고 구명보트의 무게 제한이 100kg이라면 2번째 사람과 4번째 사람은 같이 탈 수 있지만 1번째 사람과 3번째 사람의 무게의 합은 150kg이므로 구명보트의 무게 제한을 초과하여 같이 탈 수 없습니다.

구명보트를 최대한 적게 사용하여 모든 사람을 구출하려고 합니다.

사람들의 몸무게를 담은 배열 people과 구명보트의 무게 제한 limit가 매개변수로 주어질 때, 모든 사람을 구출하기 위해 필요한 구명보트 개수의 최솟값을 return 하도록 solution 함수를 작성해주세요.

## 제한사항
- 무인도에 갇힌 사람은 1명 이상 50,000명 이하입니다. <br>
- 각 사람의 몸무게는 40kg 이상 240kg 이하입니다. <br>
- 구명보트의 무게 제한은 40kg 이상 240kg 이하입니다. <br>
- 구명보트의 무게 제한은 항상 사람들의 몸무게 중 최댓값보다 크게 주어지므로 사람들을 구출할 수 없는 경우는 없습니다.<br>


## 입출력예

|people|limit|return|
|:-------------------------:|:-------------------------------:|:-----------------------------:|
|[70, 50, 80, 50]|100|3|
|[70, 80, 50]|100|3|


## 알고리즘
- people의 몸무게가 가장 많이 나가는 사람과 가장 적게 나가는 사람의 몸무게 합이 구명보트 무게 제한보다 적으면 count에 1을 더해준다
- 다음 start 인덱스와 end 인덱스의 people 몸무게 합과 구명 보트 무게제한을 비교한다
- people의 몸무게가 가장 많이 나가는 사람과 가장 적게 나가는 사람의 몸무게 합이 구명보트 무게 제한보다 크면 끝에서부터 한명씩 탐색을 해준다
- 전체 사람수에 count를 빼주면 필요한 구명보트 개수의 최솟값을 구할 수 있게 된다


## 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```python
def solution(people, limit):
    people.sort()
    count = 0
    length = len(people)
    start = 0
    end = length - 1
    
    while start < end:
        if people[start] + people[end] <= limit:
            count += 1
            start += 1
            end -= 1
        else:
            end -= 1
        
    return length - count
```
</div>
</details>

