---
title: (1)Javascript&Jquery
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Javascript&Jquery
toc: true
toc_sticky: true
toc_label: 목차
---

# (1)Javascript&Jquery

## UI만드는 step
1. HTML/CSS로 미리 디자인 (필요하면 미리 숨김)
2. 필요할 때 보여달라고 코드짬 (자바스크립트로)

알림창 닫기버튼과 기능 만들어오기

버튼 누르면 보여주고 싶음 
- 평소에는 숨겨야할 듯
`(교훈1)` 컴퓨터는 지능이 0임 구체적으로 설명해야함
`(교훈2)` UI 알아서 만드는 법 배움
 
(팁) 초보시절엔 자동완성 활용 많이 하기
function 작명은 구체적인게 좋음
함수명 작명은 CamelCase로 하기
function 쓰는 이유 : 코드 짧게 축약해서 쓰고 싶을때 function 꺼내서 쓰면 됩니다
+ 긴 코드 재사용이 잦을 때도 편리

## 오타 조심
1. 자바스크립트는 조작할 html의 하단에 코드짜야 잘됩니다
2.  셀렉터 오타 주의
3. 크롬 우클릭 - Console - 에러 확인
4. 그냥 기본문법 오타


## bootstrap 활용
starter template 활용 가능
- list group
- nav
- button 
검색을 통해 원하는 bootstrap을 가져올 수 있음

class 부착식으로 개발하면
- 애니메이션(fade in, fade out) 추가 쉬움
- 나중에 재사용이 편리함
```html
<ul class="list-group show" > 
<ul class="list-group" >
<p>class명 띄어쓰기로 탈부착화</p>
```


`원하는 요소에 클래스명을 추가하는 방법`
document.getElementByClassName('list-group')[0].classList.add('show');
※ 0번째 list-group 클래스를 찾아서 show라는 클래스를 추가해준다.

`버튼 한번 더 누르면 숨기기?`
document.getElementByClassName('list-group')[0].classList.toggle('show');
※ show가 있으면 제거, 없으면 추가하라는 뜻이다.

셀렉터들
getElementById()
getElementByClassName()
querySelector()
querySelectorAll()

querySelector()는 css문법 그대로 쓸 수 있는 셀렉터이다.
id Selector : document.querySelector('#test1')
class Selector : document.querySelector('.list-group-item')










