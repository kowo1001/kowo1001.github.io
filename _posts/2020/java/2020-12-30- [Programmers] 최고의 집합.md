---
title: [Programmers] 최고의 집합
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
자연수 n 개로 이루어진 중복 집합(multi set, 편의상 이후에는 집합으로 통칭) 중에 다음 두 조건을 만족하는 집합을 최고의 집합이라고 합니다.

각 원소의 합이 S가 되는 수의 집합
위 조건을 만족하면서 각 원소의 곱 이 최대가 되는 집합
예를 들어서 자연수 2개로 이루어진 집합 중 합이 9가 되는 집합은 다음과 같이 4개가 있습니다.
{ 1, 8 }, { 2, 7 }, { 3, 6 }, { 4, 5 }
그중 각 원소의 곱이 최대인 { 4, 5 }가 최고의 집합입니다.

집합의 원소의 개수 n과 모든 원소들의 합 s가 매개변수로 주어질 때, 최고의 집합을 return 하는 solution 함수를 완성해주세요.


## 제한사항
- bridge_length는 1 이상 10,000 이하입니다. <br>
- 최고의 집합은 오름차순으로 정렬된 1차원 배열(list, vector) 로 return 해주세요.<br>
- 만약 최고의 집합이 존재하지 않는 경우에 크기가 1인 1차원 배열(list, vector) 에 -1 을 채워서 return 해주세요.<br>
- 자연수의 개수 n은 1 이상 10,000 이하의 자연수입니다.<br>
- 모든 원소들의 합 s는 1 이상, 100,000,000 이하의 자연수입니다.<br>


## 입출력예

|n|s|result|
|:-------------------------:|:-------------------------------:|:-----------------------------:|
|2|9|[4, 5]|
|2|1|[-1]|
|2|8|[4, 4]|



## 알고리즘
- 문제 풀이 조건인 각 원소의 합이 s가 되는 수의 집합, 원소의 곱이 최대인 집합을 구해야한다
- 각 원소의 합이 s가 되는 것에 집중하기보다 어떻게 하면 최대 곱이 나올 것인지를 생각한다
- s를 n으로 나눴을떄 나오는 "수"의 범위에서 벗어나지 말아야 한다
- 즉, n = 3, s = 6 일 때, 2, 2, 2가 최대 곱이라는 것을 직관적으로 이해할 수 있다. (3 2 1, 4 1 1은 최대 곱이 아닌 2 2 2가 최대 곱이다)
- 그러나 n = 3, s = 10 or 11일 때 어떻게 해야할 것인가를 생각해봐야한다
- n = 3, s = 9이면 3 3 3으로 답을 구할 수 있지만, 10이나 11일 때는 3 3 4, 3 4 4를 구해야 한다
- 그래서 s가 n으로 나누어 떨어지지 않는다면, 나머지가 존재할 것이고 나머지 만큼의 범위를 return하는 배열의 뒷부분에 +1씩 넣어서 반환하면 된다는 것을 알 수 있었다
- (ex. 10일땐 나머지 1 그래서 3 3 4, 11일땐 나머지 2, 3 4 4가 될 것이다)

## 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```java
class Solution {
    public int[] solution(int n, int s) {
        if(n > s) {
            return new int[] {-1};
        }
        
        int[] answer = new int[n];
        if(s % n == 0) {
            for(int i = 0; i < n; i++){
                answer[i] = s / n;
            }
        } else {
            int rem = s % n;
            int pos = n - rem;
            for(int i = 0; i < pos; i++){
                answer[i] = s / n;
            }
            for(int i = pos; i < n; i++) {
                answer[i] = s / n +1;
            }
        }
        return answer;
    }
}
```
</div>
</details>

