---
title: [Programmers] 영어 끝말잇기
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
1부터 n까지 번호가 붙어있는 n명의 사람이 영어 끝말잇기를 하고 있습니다. 영어 끝말잇기는 다음과 같은 규칙으로 진행됩니다.

1. 1번부터 번호 순서대로 한 사람씩 차례대로 단어를 말합니다.
2. 마지막 사람이 단어를 말한 다음에는 다시 1번부터 시작합니다.
3. 앞사람이 말한 단어의 마지막 문자로 시작하는 단어를 말해야 합니다.
4. 이전에 등장했던 단어는 사용할 수 없습니다.
5. 한 글자인 단어는 인정되지 않습니다.
다음은 3명이 끝말잇기를 하는 상황을 나타냅니다.

tank → kick → know → wheel → land → dream → mother → robot → tank

위 끝말잇기는 다음과 같이 진행됩니다.

- 1번 사람이 자신의 첫 번째 차례에 tank를 말합니다.
- 2번 사람이 자신의 첫 번째 차례에 kick을 말합니다.
- 3번 사람이 자신의 첫 번째 차례에 know를 말합니다.
- 1번 사람이 자신의 두 번째 차례에 wheel을 말합니다.
- (계속 진행)
끝말잇기를 계속 진행해 나가다 보면, 3번 사람이 자신의 세 번째 차례에 말한 tank 라는 단어는 이전에 등장했던 단어이므로 탈락하게 됩니다.

사람의 수 n과 사람들이 순서대로 말한 단어 words 가 매개변수로 주어질 때, 가장 먼저 탈락하는 사람의 번호와 그 사람이 자신의 몇 번째 차례에 탈락하는지를 구해서 return 하도록 solution 함수를 완성해주세요.

## 제한사항
- 끝말잇기에 참여하는 사람의 수 n은 2 이상 10 이하의 자연수입니다. <br>
- words는 끝말잇기에 사용한 단어들이 순서대로 들어있는 배열이며, 길이는 n 이상 100 이하입니다.<br>
- 단어의 길이는 2 이상 50 이하입니다.<br>
- 모든 단어는 알파벳 소문자로만 이루어져 있습니다.<br>
- 끝말잇기에 사용되는 단어의 뜻(의미)은 신경 쓰지 않으셔도 됩니다.<br>
- 정답은 [ 번호, 차례 ] 형태로 return 해주세요.<br>
- 만약 주어진 단어들로 탈락자가 생기지 않는다면, [0, 0]을 return 해주세요.<br>


## 입출력예

|n|words|result|
|:-------------------------:|:-------------------------------:|:-----------------------------:|
|3|[tank, kick, know, wheel, land, dream, mother, robot, tank]|[3,3]|
|5|[hello, observe, effect, take, either, recognize, encourage, ensure, establish, hang, gather, refer, reference, estimate, executive]|[0,0]|
|2|[[hello, one, even, never, now, world, draw]|[1,3]|


## 알고리즘
- 처음으로 말한 단어를 set()을 이용해서 리스트에 저장한다
- 이전 단어를 기억하기 위한 변수를 만든다
- 이전 단어의 마지막 글자와 제시단어의 첫글자가 다르거나, 이미 있는 단어일 경우, 사람이 몇번째인지 차례가 몇번째 인지 리턴한다
- 세번째 제시된 조건에 해당하지 않을 경우, 등장한 단어를 저장하고 이전 단어 변수에도 단어를 저장한 후 [0,0]을 1부터 단어개수만큼 반복문을 돌리고 리턴한다

## 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```python
def solution(n, words):
    dataset = set([words[0]]) # 처음으로 말한 단어 리스트에 저장
    prev_words = words[0] # 이전 단어 기억하기 위함
    
    for i in range(1,len(words)): 
        if (prev_words[-1] != words[i][0]) or words[i] in dataset:
            return [(i % n)+1,(i // n)+1]
        
        dataset.add(words[i])
        prev_words = words[i]
    return [0,0]
```
</div>
</details>

