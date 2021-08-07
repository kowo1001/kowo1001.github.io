---
title: LeetCode :Roman to Integer
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
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M. <br>

Symbol <br>       Value <br>
I <br>              1 <br> 
V <br>              5 <br> 
X <br>              10 <br> 
L <br>              50 <br> 
C <br>              100 <br> 
D <br>              500 <br> 
M <br>              1000 <br> 
 <br> 
For example, 2 is written as II in Roman numeral, just two one's added together. 12 is written as XII, which is simply X + II.  <br> 
The number 27 is written as XXVII, which is XX + V + II. <br>

Roman numerals are usually written largest to smallest from left to right.  <br>
However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four.  <br>
The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used: <br>

I can be placed before V (5) and X (10) to make 4 and 9.  <br>
X can be placed before L (50) and C (100) to make 40 and 90.  <br>
C can be placed before D (500) and M (1000) to make 400 and 900. <br>
Given a roman numeral, convert it to an integer. <br>

------


## Example 1:
Input: s = "III" <br>
Output: 3 <br>

## Example 2:
Input: s = "IV" <br>
Output: 4 <br>

## Example 3:
Input: s = "IX" <br>
Output: 9 <br>

## Example 4:
Input: s = "LVIII" <br>
Output: 58 <br>
Explanation: L = 50, V= 5, III = 3. <br>

## Example 5:
Input: s = "MCMXCIV" <br>
Output: 1994 <br>
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4. <br>


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


    