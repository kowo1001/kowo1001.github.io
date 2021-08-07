---
title: LeetCode :Reverse Integer
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
Given a signed 32-bit integer x, return x with its digits reversed. <br>
If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.<br>

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).<br>

------


## Example 1:

Input: x = 123<br>
Output: 321<br>

## Example 2:

Input: x = -123<br>
Output: -321<br>

## Example 3:

Input: x = 120<br>
Output: 21<br>

## Example 4:

Input: x = 0<br>
Output: 0<br>



## 정답 풀이
```python
class Solution:
    def reverse(self, x: int) -> int:
        if x>0:
            result = int(str(x)[::-1])
        else:
            result = -1*int(str(x*-1)[::-1])
            
        if result not in range(-2**31, 2**31):
            result = 0
            
        return result

```

## 핵심 알고리즘 및 스킬
- str(x)[::-1]의 의미
- str(x*-1)[::-1]의 의미

## 다른 사람 풀이
```python

```

## 배워야할 점


    