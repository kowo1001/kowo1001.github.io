---
title: Programmers 멀리뛰기
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- JAVA
toc: true
toc_sticky: true
toc_label: 목차
---

## 문제설명
효진이는 멀리 뛰기를 연습하고 있습니다. 효진이는 한번에 1칸, 또는 2칸을 뛸 수 있습니다. 칸이 총 4개 있을 때, 효진이는
(1칸, 1칸, 1칸, 1칸)
(1칸, 2칸, 1칸)
(1칸, 1칸, 2칸)
(2칸, 1칸, 1칸)
(2칸, 2칸)
의 5가지 방법으로 맨 끝 칸에 도달할 수 있습니다. 멀리뛰기에 사용될 칸의 수 n이 주어질 때, 효진이가 끝에 도달하는 방법이 몇 가지인지 알아내, 여기에 1234567를 나눈 나머지를 리턴하는 함수, solution을 완성하세요. 예를 들어 4가 입력된다면, 5를 return하면 됩니다.

## 제한 사항
n은 1 이상, 2000 이하인 정수입니다.


## 입출력 예
|n|result|
|:-------------------------:|:-------------------------------:|
|4|5|
|3|3|

## 입출력 예 설명
어느 한 컴퓨터공학과 학생이 유명한 교수님을 찾아가 물었다. <br>
입출력 예 #1<br>
위에서 설명한 내용과 같습니다.<br>

입출력 예 #2<br>
(2칸, 1칸)<br>
(1칸, 2칸)<br>
(1칸, 1칸, 1칸)<br>
총 3가지 방법으로 멀리 뛸 수 있습니다.<br>


## 알고리즘
- 피보나치 수열 사용
- 시간초과 문제가 있어서 해결방법 필요함

## 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```java
import java.util.*;

class Solution {
    
    public int muli(int n) {
        if (n == 1) {
            return 1;
        }else if (n == 2){
            return 2;
        }
        return muli(n-1) + muli(n-2);
    }
    
    public long solution(int n) {
        
        return muli(n)%1234567;
    }
}
```
</div>
</details>

