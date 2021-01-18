---
title: Vue-(6) vue component와 v-bind
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- Vue
toc: true
toc_sticky: true
toc_label: 목차
---

## Component 
재사용 가능한 component
- 코드를 간소화하고 재사용할 수 있게 하는 구성요소
- 컴포넌트들을 조합해 전체 애플리케이션 작성
- 조합해서 화면을 구성할 수 있는 블록
- 재사용성 향상이 주 목적

## Component 장점
- 뛰어난 재사용성
- 테스트가 용이
- 디버깅이 편리함

## Component란?
등록방식에 따른 컴포넌트 종류
사용시 등록한 tag명으로 사용
- 전역 컴포넌트
- 지역 컴포넌트

### 전역 컴포넌트(컴포넌트 전역 등록)
Vue.component를 이용해서 컴포넌트를 아래와 같이 만든다.

```javascript
Vue.component('my-component-name', {
  // ... options ...
})
```

이런 컴포넌트를 전역 등록되었다고 한다. 즉 어떤 Vue 인스턴스(new Vue)에서도 사용할 수 있게 된다.

```javascript
Vue.component('component-a', { /* ... */ })
Vue.component('component-b', { /* ... */ })
Vue.component('component-c', { /* ... */ })
```

```javascript
new Vue({ el: '#app' })

<div id="app">
  <component-a></component-a>
  <component-b></component-b>
  <component-c></component-c>
</div>
```

이렇게 등록한 컴포넌트들은 모든 하위 컴포넌트에도 사용가능하다. 즉 위의 3개 컴포넌트들은 각각의 컴포넌트 안에서도 사용할 수 있다.

### 지역 컴포넌트(컴포넌트 지역 등록)
웹팩같은 빌드 시스템을 사용하고 모든 컴포넌트를 전역 등록했으면 설사 어떤 컴포넌트를 더 이상 사용하지 않더라도 최종 빌드에는 들어가 있게 된다.
사용자가 내려받아야 하는 자바스크립트의 양이 불필요하게 커지게 된다. 이 경우에 컴포넌트를 일반 자바스크립트 객체로 정의할 수 있다.

```javascript
var ComponentA = { /* ... */ }
var ComponentB = { /* ... */ }
var ComponentC = { /* ... */ }
```

그러면 사용할 컴포넌트들만 components 옵션을 통해 쓸 수 있다.

```javascript
new Vue({
  el: '#app',
  components: {
    'component-a': ComponentA,
    'component-b': ComponentB
  }
})
var ComponentC = { /* ... */ }
```

components 객체의 각 속성에서 key가 custom element의 이름이 되고 value가 사용할 컴포넌트 객체를 지정한다.
지역 등록된 컴포넌트는 하위컴포넌트에서는 사용이 불가능하다는 점을 유의해야 한다.
예를 들어 ComponentA를 ComponentB에서 쓰고 싶다면 아래와 같이 해야한다.

```javascript
var ComponentA = { /* ... */ }

var ComponentB = {
  components: {
    'component-a': ComponentA
  },
  // ...
}
```

바벨이나 웹팩을 이용해서 ES2015를 적용하고 있다면 싱글파일 컴포넌트를 이용해서 이렇게 할 수도 있다.

```javascript
import ComponentA from './ComponentA.vue'

export default {
  components: {
    ComponentA
  },
  // ...
}
```

ES2015 이상에서는 객체 내의 components 옵션에서 ComponentA: ComponentA라고 하지 않고 ComponentA라고만 해도 된다.
즉 key로 아래의 두 가지가 모두 가능하다.(역자 주: component-a: ComponentA, ComponentA: ComponentA, ComponentA가 모두 가능)
- 템플릿에서 사용할 사용자정의 엘리먼트 이름
- 컴포넌트 옵션에 들어갈 변수명


## Vue Component 이름 등록
컴포넌트를 등록할 때는 항상 이름을 지워줘야 한다
컴포넌트의 이름은 Vue.component 의 첫번째 인자이다
Vue.component('component-name', { /* */ })
component-name이 'listUp'와 같이 단어 중간에 대문자가 있을 경우,

```html
<div id="app">
  <list-up></list-up>
</div>
```

위와 같이 대문자 앞에 '-'기호로 구분해줘야 인식이 된다(단, 대소문자 상관없이 인식됨)

## Vue Component간 통신 
- 컴포넌트간 통신과 유효범위
- 각 컴포넌트의 유효 범위가 독립적, 따라서 다른 컴포넌트의 값을 직접적으로 참조 불가

## 상위 하위 컴포넌트 관계
- Vuew의 컴포넌트간 데이터 전달 방법의 기본
- props와 emit Events 사용
- props : 상위(부모) -> 하위(자식) 컴포넌트로 데이터 전달 방법
- emit events -> 하위에서 상위로 : 메세지 전달

![상위하위컴포넌트 데이터전달](https://user-images.githubusercontent.com/37354978/104907277-3015d300-59c8-11eb-916d-9596e60dc0ee.png)
상위컴포넌트 -> props -> 하위 컴포넌트 -> $emit -> 상위 컴포넌트
$emit , props 두가지 용어 잘 알기

상위(부모 컴포넌트)에서 하위 컴포넌트(자식 컴포넌트)로 데이터 전달 
- props : [props_name] : 부모가 제공하는 데이터를 받기 위한 property 및 name 선언
- 하위 컴포넌트에서 등록한 props 속성을 v-bind라는 속성으로 상위 컴포넌트의 data 속성명 사용

```html
<div id="app">
  <child-component v-bind:childvar="supermessage"> </child-component>
</div>

<script>
//자식 & 전역 컴포넌트
Vue.component('child-component', {
  props: ['childvar'],
  template: '<p>{{childvar}}</p>'
});
//부모 컴포넌트
new Vue({
  el: '#app',
  data: {
	supermessage: '부모인스턴스에서 제공해주는 데이터'
}
```

## v-bind 기능

HTML 태그의 속성값을 데이터(data)값을 사용해야한다면 v-bind를 활용하면 된다
예를 들어,  v-bind는 <img v-bind:src(속성명)="속성의 이름">와 같은 형식으로 사용한다
아래 예시를 더 살펴보자

```html
<script>
        Vue.component('listUp',{
            template: '#listTemplate',
            props : ['contacts'] //property 및 props_name을 선언한다
        });
        //새로운 뷰를 정의한다
        var vm = new Vue({ 
            el: "#app", // 어떤 element에 적용을 할 지 정한다
            data: { // data는 해당 뷰에서 사용할 정보를 지닌다
                list1: [  //1차 고객 명단
                    { "no": 97, "name": "유재석", "tel": "010-3456-8296", "address": "서울시" },
                    { "no": 96, "name": "신동엽", "tel": "010-3456-8295", "address": "서울시" },
                    { "no": 95, "name": "이승기", "tel": "010-3456-8294", "address": "서울시" }
                ],
                list2: [ //2차 고객 명단
                    { "no": 82, "name": "김혜수", "tel": "010-3456-8281", "address": "서울시" },
                    { "no": 81, "name": "전지현", "tel": "010-3456-8280", "address": "서울시" }
                ]
            }
        });
    </script>


<!-- 부모 -->
<div id="app">
        <h3>고객 명단</h3>
        <hr>
        <h3>1차 고객 : 1월 1~3일</h3>
        <list-up v-bind:contacts="list1"></list-up>
        <!-- v-bind:속성(props)= "list1(속성의 이름)"  -->

        <h3>2차 고객 : 1월 13~15일</h3>
        <list-up v-bind:contacts="list2"></list-up>
        <!-- v-bind:속성(props)= "list1(속성의 이름)"  -->
    </div>

<!-- 자식 -->
<template id="listTemplate"> 
        <div>
            <table id="list">
                <thead>
                    <tr>
                        <th>번호</th>
                        <th>이름</th>
                        <th>전화번호</th>
                        <th>주소</th>
                    </tr>
                </thead>
                <tbody id="contacts">
                    <!--? contracts : props로 설정하시면 됩니다-->
                    <tr v-for="contact in contacts">
                        <td>{{contact.no}}</td>
                        <td>{{contact.name}}</td>
                        <td>{{contact.tel}}</td>
                        <td>{{contact.address}}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </template
```

상위(부모 컴포넌트)에서 하위 컴포넌트(자식 컴포넌트)로 데이터 전달하기 위해서는
props : [props_name] 을 통해 부모가 제공하는 데이터를 받을 수 있다
즉, 부모로부터 자식에게 데이터를 전달하기 위해서는 
Vue.component({ props : ['contracts'] }); 와 같이 속성을 선언해야 한다

(참고) Emmet 기능을 꼭 사용해주기
Vscode에서 div#app1-1는 <div id="app1-1"></div> 결과와 같다