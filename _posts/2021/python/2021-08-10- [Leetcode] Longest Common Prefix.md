---
title: LeetCode :Longest Common Prefix
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

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

------


## Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"

## Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.

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


    