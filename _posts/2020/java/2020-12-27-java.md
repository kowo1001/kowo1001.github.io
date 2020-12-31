---
title: [Programmers] 다리를 지나는 트럭
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
tags: JAVA
categories:
- JAVA
toc: true
toc_sticky: true
toc_label: 목차
---

## 문제설명
트럭 여러 대가 강을 가로지르는 일 차선 다리를 정해진 순으로 건너려 합니다. 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 알아내야 합니다. 트럭은 1초에 1만큼 움직이며, 다리 길이는 bridge_length이고 다리는 무게 weight까지 견딥니다.
※ 트럭이 다리에 완전히 오르지 않은 경우, 이 트럭의 무게는 고려하지 않습니다.

예를 들어, 길이가 2이고 10kg 무게를 견디는 다리가 있습니다. 무게가 [7, 4, 5, 6]kg인 트럭이 순서대로 최단 시간 안에 다리를 건너려면 다음과 같이 건너야 합니다.

|경과 시간|다리를 지난 트럭|다리를 건너는 트럭|대기 트럭|
|:-------------------------:|:-------------------------------:|:-----------------------------:|:-----------------------------:|
|0|[]|[]|[7,4,5,6]|
|1~2|[]|[7]|[4,5,6]|
|3|[7]|[4]|[5,6]|
|4|[7]|[4,5]|[6]|
|5|[7,4]|[5]|[6]|
|6~7|[7,4,5]|[6]|[]|
|8|[7,4,5,6]|[]|[]|

따라서, 모든 트럭이 다리를 지나려면 최소 8초가 걸립니다.

solution 함수의 매개변수로 다리 길이 bridge_length, 다리가 견딜 수 있는 무게 weight, 트럭별 무게 truck_weights가 주어집니다. 이때 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 return 하도록 solution 함수를 완성하세요.


## 제한사항
- bridge_length는 1 이상 10,000 이하입니다. <br>
- weight는 1 이상 10,000 이하입니다. <br>
- truck_weights의 길이는 1 이상 10,000 이하입니다. <br>
- 모든 트럭의 무게는 1 이상 weight 이하입니다. <br>


## 입출력예

|bridge_length|weight|truck_weights|return|
|:-------------------------:|:-------------------------------:|:-----------------------------:|:-----------------------------:|
|2|10|[7,4,5,6]|8|
|100|100|[10]|101|
|100|100|[10,10,10,10,10,10,10,10,10,10]|110|



## 알고리즘
- 처음으로 말한 단어를 set()을 이용해서 리스트에 저장한다
- 이전 단어를 기억하기 위한 변수를 만든다
- 이전 단어의 마지막 글자와 제시단어의 첫글자가 다르거나, 이미 있는 단어일 경우, 사람이 몇번째인지 차례가 몇번째 인지 리턴한다
- 세번째 제시된 조건에 해당하지 않을 경우, 등장한 단어를 저장하고 이전 단어 변수에도 단어를 저장한 후 [0,0]을 1부터 단어개수만큼 반복문을 돌리고 리턴한다

## 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```java
import java.util.Queue;
import java.util.concurrent.ConcurrentLinkedQueue;

class Solution {
    public int solution(int bridge_length, int weight, int[] truck_weights) {
        int answer = 0;
        
        Queue<Integer> q = new ConcurrentLinkedQueue<>();
        int sum = 0;
        for(int t : truck_weights) {
            while(true) {
                if(q.isEmpty()) {
                    q.add(t);
                    sum += t;
                    answer++;
                    break;
                } else if(q.size() == bridge_length) {
                    sum -= q.poll();
                } else {
                    if(sum + t > weight) {
                        answer++;
                        q.add(0);
                    } else {
                        q.add(t);
                        sum += t;
                        answer++;
                        break;
                    }   
                }
            }
        }
        return answer + bridge_length;
    }
}
```
</div>
</details>

