---
title: LeetCode :Palindrome Number
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
Given an integer x, return true if x is palindrome integer.<br>

An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.<br>

------


## Example 1:

Input: x = 121<br>
Output: true<br>

## Example 2:

Input: x = -121<br>
Output: false<br>
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.<br>

## Example 3:

Input: x = 10<br>
Output: false<br>
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.<br>

## Example 4:

Input: x = -101<br>
Output: false<br>


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


    