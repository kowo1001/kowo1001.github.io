---
title: Vue-(12) vuex 주요기술요소
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



## Vue.use(Vuex)의 사용
```javascript
Vue.use(Vuex);
```
use는 vue의 플러그인이라는 기능
Vue를 쓸 때 전역에 특정 기능을 사용하고 싶을 때 사용한다.

## Vuex 기술요소
- state : 여러 컴포넌트에 공유되는 데이터 -> data
- getters : 연산된 state값을 접근하는 속성 -> computed
- mutations : state값을 변경하는 이벤트 로직 또는 메서드 -> methods
- actions : 비동기 처리 로직을 선언하는 메서드 -> async methods

## state란?
- 여러 컴포넌트간에 공유할 데이터  -> **상태** 
```javascript
//Vue
data: {
    message: 'Hello Vue.js!'
}

//Vuex
state: {
    message: 'Hello Vue.js!'
}

```
```html
<!-- Vue -->
<p>{{message}}<p>

<!-- Vuex -->
<p>{{this.$store.state.message}}</p>
```

## getter란?

- state값을 접근하는 속성이자 computed() 처럼 미리 연산된 값을 접근하는 속성

```javascript
//store.js
state: {
    num: 10
},
getters: {
    getNumber(state) {
        return state.num;
    },
    doubleNumber(state) {
        return state.num * 2;
    }
}
```

```html
<p>{{this.$store.getters.getNumber}}</p> 
<!-- 10 -->
<p>{{this.$store.getters.doubleNumber}}</p> 
<!-- 20 -->
```

## mutation란?
- state의 값을 변경할 수 있는 유일한 방법이자 메서드
- 뮤테이션은 commit()으로 동작시킨다.
- mutations은 state을 변경시키는 역할을 합니다.
- mutations에 정의된 함수를 commit를 통해서 호출하는 것으로 저장소의 state에 정의된 변수의 값을 변경할 수 있습니다.

```javascript
// store.js
import { createStore } from 'vuex';

const store = createStore({
    state () {
        return {
            count: 0
        }
    },
    mutations: {
        increment (state) {
            state.count++
        }
    }
})

export default store;

// StoreAccess.vue
methods: {
    increment() {
        this.$store.commit('increment');
    }
}
```

```javascript
//store.js
state: { num:10 },
mutations: {
    printNumbers(state) {
        return state.num
    },
    sumNumbers(state, anotherNum) {
        return state.num + anotherNum;
    }
}

//App.vue
this.$store.commit('printNumbers'); // 10
this.$store.commit('sumNumbers', 20); // 30
```
## mutations의 commit()형식
- state를 변경하기 위해 mutations를 동작시킬때 인자(payload)를 전달할 수 있음
```javascript
state: {storeNum: 10},
mutations: {
    modifyState(state, payload) {
        console.log(payload.str); // passed from payload
        return state.storeNum += payload.num; // return 30 = 10 + 20
    }
}

//App.vue
this.$store.commit('modifyState', {
    str: 'passed from payload',
    num: 20
});
```
## actions의 역할
- 여러 개의 mutations을 실행시킬 수 있습니다.
- mutations와 달리 비동기 작업이 가능합니다.



