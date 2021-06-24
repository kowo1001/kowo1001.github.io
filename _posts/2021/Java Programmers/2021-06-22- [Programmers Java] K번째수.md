---
title: Baekjoon 2884:알람 시계
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
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.<br>

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면<br>

array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.<br>
1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.<br>
2에서 나온 배열의 3번째 숫자는 5입니다.<br>
배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을<br> 
적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.<br>


## 알고리즘
1. 


## 풀이

<details>
<summary>소스코드</summary>
<div markdown="1">

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int h = sc.nextInt();
        int m = sc.nextInt();
        
        if(m < 45) {
            h--;
            m = 60 - (45 - m);
            if(h < 0) {
                 h = 23;
            }
            System.out.println(h + " " + m);
        }else {
            System.out.println(h + " " + (m - 45));
        }
    }
}
```
</div>
</details>

