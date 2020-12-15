---
title: JPA MiniProject
---

# JPA MiniProject

## 마트의 민족
코로나 시대에 누가 마트에서 물건 하나하나 골라서 장을 보나?

미리 어플을 통해 장을 보면 마트에서 물건을 미리 포장해주고 고객은 마트에 들려 간단하게 들고가면 된다.

## Intruduction
- ![ok_woman](https://github.githubassets.com/images/icons/emoji/unicode/1f64b.png){: width="30" height="30"} ![ok_woman](https://github.githubassets.com/images/icons/emoji/unicode/1f646.png){: width="30" height="30"}  마트의 민족은 앱이나 웹으로 원하는 물건을 주문하면 직접 고객이 인근 마트에서 구매했었던 상품들을 찾아가는 JPA로 구현한 서비스입니다.
- 마트 관리자가 상품을 추가하고, 검색하고, 수정하고, 삭제하는 것을 목표로 합니다.
- 고객이 상품을 구매하기 위해 주문을 하고, 주문 조회, 주문건 수정 및 삭제를 하는 것을 목표로 합니다.

## ![eyes](https://github.githubassets.com/images/icons/emoji/unicode/1f440.png){: width="40" height="40"} Structure
![Structure](https://user-images.githubusercontent.com/37354978/102043369-89ae3f00-3e17-11eb-8c55-87486554a7b6.PNG)
## ![hammer&wrench](https://github.githubassets.com/images/icons/emoji/unicode/1f6e0.png){: width="40" height="40"} Service Process
![Slide1](https://user-images.githubusercontent.com/37354978/102005472-5ce92180-3d5c-11eb-8e75-327304f69ee7.jpg)
![admin](https://github.githubassets.com/images/icons/emoji/unicode/1f481.png){: width="30" height="30"} 관리자
  - 마트 검색
  - 마트 추가
  - 마트 수정
  - 마트 삭제

![mart](https://github.githubassets.com/images/icons/emoji/unicode/1f3ea.png){: width="30" height="30"} 마트사장
  - 마트 수정
  - 주문 보기
  - 상품 변경
  - 수령 완료

![guests](https://github.githubassets.com/images/icons/emoji/unicode/1f46a.png){: width="30" height="30"}회원
  - 상품 확인
  - 주문
  - 주문금액 확인

## 💡 Technologies Used
![new page1](https://user-images.githubusercontent.com/37354978/102030120-ba30b180-3df4-11eb-960a-26c82137cfe3.JPG)

## 🌊 Data Flow

### MVC Model Architecture

![데이터흐름도2](https://user-images.githubusercontent.com/37354978/102006703-7e4f0b00-3d66-11eb-81c3-690095433932.JPG)


## ✍️ Author
 Team PeopelOfMarket
  - 최태열 [(TaeyeolChoi)](https://github.com/ta-ye)
  - 김성호 [(SeonghoKim)](https://github.com/seongho726)
  - 장종욱 [(JongwookJang)](https://github.com/kowo1001)
  
## 🔥 Issues
  - 프론트엔드가 없어서 화면을 구현하기 어려웠다. 따라서 node-red를 사용하게 되었다.
  - 임의로 data를 구현하여 OrcleDB에 저장하는 과정을 진행했기 때문에 실제 서비스에서의 과정과는 다소 달랐다.
  
  - 추후 프론트엔드 부분도 구현하여 전체적인 프로젝트를 완성해야할 필요성을 느끼게 되었다.
  
## 참고
[테이블 내부 구성 엑셀 문서 링크](https://docs.google.com/spreadsheets/d/1tmYgHqzKEgwfonAy3ZgYwQT_1SNpU3c6bemWXRXWOFw/edit#gid=0)

[데이터모델링 링크](https://www.erdcloud.com/d/CcRRWzyoKKBKYuwbf)
