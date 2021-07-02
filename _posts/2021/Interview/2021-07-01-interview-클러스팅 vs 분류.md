---
title: [데이터 분석] 클러스터링과 분류의 차이점
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Spring
toc: true
toc_sticky: true
toc_label: 목차
---


## 클러스터링(Clustering) 이란?

클러스터링(Clustering)은 데이터 마이닝의 범주에 속한다.<br>

데이터 마이닝(Data mining)이란,<br>
방대한 양의 데이터에 체계적, 자동적으로 통계적 규칙 또는 특징, 패턴 등을 찾아내는 것이다.<br>

데이터 마이닝의 방법들로는<br>
분류(Classification)<br>
군집화(Clustering)<br>
연관성(Association)<br>
연속성(Sequencing)<br>
예측(Forecasting)<br>
이 있다.<br>

그래서 클러스터링이란, 주어진 데이터들의 특성을 파악하여 데이터 집단(클러스터)를 정의하고<br>

그 데이터 집단을 대표할 수 있는 점을 찾는 것이다.<br>

클러스터링 알고리즘을 통해 데이터를 군집화 하고 나면,<br>

비슷한 특성을 가진 데이터들은 같은 클러스터에 포함되고, 특성이 다르다면 다른 클러스터에 포함된다.<br>

그리고 군집화(Clustering)와 분류(Classification)가 혼동될 수도 있는데,<br>

분류는 간단히 말하면 특정 카테고리를 정하고, 그 카테고리에 속하는 것들을 '구분'하는 것이다.<br>

이미지 인식의 Object Classification을 예로 들면,<br>

수십만장의 사진 데이터를 학습시킨 후, 어떠한 사진을 입력했을 때<br>

이 사진은 자동차(Car)에 속한다. == 이 사진은 자동차 사진이다.<br>

이 사진은 말(Horse)에 속한다. == 이 사진은 말 사진이다.<br>

위와 같은 결과를 도출해내는 것이 Classification의 한 예이다.<br>

긴 글을 내 생각대로 한줄 정리하자면<br>

**군집화(Clustering)는 비슷한 것들을 집단단위로 묶는 것, 분류(Classification)는 어디에 속하는지 구분하여 내는 것. 이라고 생각한다.**<br>


**출처 : JW공부스토리**