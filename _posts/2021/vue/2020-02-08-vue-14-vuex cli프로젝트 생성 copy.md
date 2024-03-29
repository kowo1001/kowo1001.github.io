---
title: Vue-(14) vuex 주요기술요소
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



## 권장 설치 플러그인
Atom Keymap : 아톰의 키 설정을 불러오는 플러그인
Vetur : Vue.js 플러그인
Night Owl : 코드 하이라이팅 플러그인
Material Dark Syntax : 코드 하이라이팅 플러그인
Google Material Icon Theme : 폴더 아이콘 테마
ESLint : 자바스크립트 문법 검사 플러그인
TSLint : 타입스크립트 문법 검사 플러그인
Auto Close tag : HTML 태그 자동 닫기 플러그인
Live Server : 정적 파일을 로컬 서버에 올리고 자동 갱신해주는 플러그인


## 코딩 컨밴션 참고 URL
https://vuejs.org/v2/style-guide/

vue init webpack-simple vue-news5(프로젝트 폴더명)

vue create vue-cli3

npm i -g @vue/cli

default (Manually X) 

--------------

CLI 2.x vs CLI 3.x
-명령어
- 2.x :  vue init '프로젝트 템플릿 이름' '파일 위치'
- vue init webpack-simple '파일 위치'
- 3.x :  vue create '프로젝트 이름'

- 웹팩 설정 파일
- 2.x webpack.config.js -> 노출 O
- 3.x -> 노출 X

- 프로젝트 구성
- 2.x : 깃헙의 템플릿 다운로드
- 3.x : 플러그인 기반으로 기능 추가

- ES6 이해도
- 2.x : 필요X
- 3.x : 필요O

------------------------
터미널창에서 eslint 검사기능 OFF 

module.exports = {
    lintOnSave: false
}

------------vue router ----------
npm i vue-router --save

------------vue axios------------
npm i axios --save

----------- vue-news api 참고 ---
https://github.com/tastejs/hacker-news-pwas/blob/master/docs/api.md

-------

## 프로젝트 폴더 만들기
진행할 프로젝트 폴더에서
vue create vue-til -Manually select features - 스페이스바로 Babel, Linter, Unit Testing 선택 -  2.X - ESLint + Prettier - Lint on save - Jest - In dedicated config files-
프로젝트 preset 저장? ->n - 끝! <br>

## vue config 파일 설정
프로젝트 폴더 오른쪽마우스 클릭 - New File - vue.config.js 파일 생성 - 아래 코드 넣기 <br>

module.exports = {
    devServer: {
        overlay: false
    }
};

- 위 코드를 통해 페이지에서 오류(error)보이는 화면이 안나오게끔 할 수 있음 <br>

## prettier 코드 정의 도구
- 팀원들간에 일관된 코드로 작성 가능
- 여러사람 기준 만들어서 코드 포맷을 맞추기 위해 사용
- 출력길이 제한 및 특정 출력길이에 한해서 개행 가능
- 문자열 내 큰따옴표 작은 따옴표 정의 가능
- .eslintrc.js 파일에 prettier와 ESLint 동시 설정 가능
```javascript
rules: {
    "no-console": "off",
    // "no-console": process.env.NODE_ENV === "production" ? "warn" : "off",
    // "no-debugger": process.env.NODE_ENV === "production" ? "warn" : "off"
    "prettier/prettier" : ['error', {
        singleQuote: true,
        semi: true,
        useTabs: false,
        tabWidth: 2,
        trailingComma: 'all',
        printWidth: 80,
        bracketSpacing: true,
        arrowParens: 'avoid',
    }]
  },
```
참고 : 설정 파일이 변경되면 서버를 재실행한다

## 설정
윈도우 기준 -> ctrl + , (콤마) -> vscode 설정화면으로 이동

```json
{
  // ESLint
  "eslint.validate": [
    {
      "language": "vue",
      "autoFix": true
    },
    {
      "language": "javascript",
      "autoFix": true
    },
    {
      "language": "javascriptreact",
      "autoFix": true
    },
    {
      "language": "typescript",
      "autoFix": true
    },
    {
      "language": "typescriptreact",
      "autoFix": true
    }
  ],
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  // don't format on save
  "editor.formatOnSave": false
}
```



## ESLint Error  
1. 첫번째 방법 
- Replace `····` with `↹↹`
- 오류가 .eslintrc.js 에서 useTabs: true 로 설정되어 있어서 그렇습니다
- useTabs: false 로 바꾸고 npm run serve 했더니 오류가 뜨지 않습니다
2. 두번째 방법 
package.json 에서 eslint 버전 낮추고 npm install 다시 하기
- "eslint": "^6.7.2", 을   "eslint": "^5.16.0", 로 버전 설정


## 코드스프리팅과 리다이렉트
- 접속하자마자 바로 로그인 페이지로 이동
- /login 접속시 한번에 구현해놓은 20페이지가 아닌 1페이지만 import 하도록 구현
- 이를 통해 웹 페이지 접속 속도 빨라진다고 합니다.
```javascript
export default new VueRouter({
  routes: [
    {
      path: '/',
      redirect: '/login',
    },
    {
      path: '/login',
      component: () => import('@/views/LoginPage.vue'),
    },
    {
      path: '/signup',
      component: () => import('@/views/SignupPage.vue'),
    },
  ],
});
```
## 뷰 라우터 History Mode 주의사항
- 서버마다 설정방법이 다르며, 아래 링크를 참고해서 해결 가능합니다.
https://router.vuejs.org/guide/essentials/history-mode.html#example-server-configurations

Vue VSCode snippets?? 
vda 입력 후 tab ??

github.com/joshua1988/vue-til

1번과 2번은 같은 코드입니다.

```javascript
//1
mutations: {
        SET_NEWS: function() {
            
        }
    },
```

```javascript
//2
mutations: {
        SET_NEWS() {
            
        }
    },
```
## 축약문법 v-bind 
v-bind:href는 :href와 같은 코드입니다.<br>
https://github.com/tastejs/hacker-news-pwas/blob/master/docs/api.md<br>

## v-html
div에 v-html속성을 통해 본문 내용에 <p> 태그 등 여러 html 태그 등을 제거할 수 있습니다.<br>

## 라우터 트랜지션
특정 페이지로 이동할때 화면이 바뀌는데, vue 내부적으로 사용되는 트랜지션을 사용해서<br>
조금 더 부드럽게  화면 전환이 될 수 있도록 바꾸는 것이 가능합니다. <br>
관련 코드 참고 URL
https://vuejs.org/v2/guide/transitions.html



## Windows에 직접 Node.js 개발 환경 설치
- NVM은 다양한 프레임워크, 서버 등에 있어서 노드버전을 관리하기 좋음
- NVM 설치하는데 도움이 되는 Url
https://docs.microsoft.com/ko-kr/windows/nodejs/setup-on-windows

## Vue CLI의 env 파일 규칙과 실무 환경 구성 방법
https://cli.vuejs.org/guide/mode-and-env.html#modes

프로젝트 폴더에 다음과 같이 .env.production, .env.development,.env를 생성한다. <br>
.env.production은 배포했을때 도메인 주소를 넣는다<br>
.env.development는 로컬에서 개발할때 사용한다<br>
.env.production와 .env.development 없을때 공통으로 들어가야 하는 것은<br>
.env 파일안에 작성한다.<br>
서버를 껐다가 켜야지 웹팩에 있는 설정파일들이 적용된다 <br>

네이버지도 API로 구현한 지도기반 맛집 저장 서비스 실행 순서 <br>
- npm install -g nodemon<br>
- nodemon ./bin/www<br>







