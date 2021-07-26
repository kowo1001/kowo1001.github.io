---
title: Programmers Lv1-K번째수
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
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.<br>

You may assume that each input would have exactly one solution, and you may not use the same element twice.<br>

You can return the answer in any order.<br>


## 예시1
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].

## 예시2
Input: nums = [3,2,4], target = 6
Output: [1,2]

## 알고리즘
1. 


## 나의 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```java

import java.util.*;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        int a,b;
        
        int[] result = new int[2];
        
        // List<Integer> result = new ArrayList<Integer>();
        
        for(int i=0; i < nums.length-1; i++) {
            for(int j=1; j < nums.length-1; j++) {
                if(nums[i]+nums[i+j] == target){
                    a = i;
                    b = i+j;
                    result[0] = a;
                    result[1] = b;
                }
            }
        }
        
        return result;
        
    }
}

```
</div>
</details>

## 정답

<details>
<summary>소스코드</summary>
<div markdown="1">

```java



```
</div>
</details>

## 다른 사람 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```java



```
</div>
</details>
