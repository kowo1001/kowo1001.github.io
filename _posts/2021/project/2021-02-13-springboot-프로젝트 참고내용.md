---
title: SpringBoot MidProject 참고
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
categories:
- PROJECT
toc: true
toc_sticky: true
toc_label: 목차
---
# Mid Project 진행시 참고 내용

## 구르망 프로젝트 참고 내용
- Node.js는 자바스크립트 런타임
- 런타임 : 프로그래밍 언어가 구동되는 환경
- npm : node package manager의 줄임말
- 모듈 : 애플리케이션을 구성하는 개별적 요소(= 패키지)
- 모듈을 통해 기능적으로 분리되어 개발 효율성과 유지보수성 향상
- npm은 모듈들을 패키지화하여 모아둔 저장소 역할 및 설치 ,관리해주는 툴
- node 버전은 v.14.15.0을 사용 (node --version 명령을 통해 node 버전 확인 가능)
- npm install -g nodemon을 통해 설치 
- nodemon은 서버를 껐다켰다하는 불편함을 해소시켜주는 필요한 패키지
-  -g : 글로벌 속성으로 설치 (글로벌로 설치를 해서 다른 프로젝트 경로 상관없이 모든곳에서 nodemon 패키지를 쓸수 있도록 함)
- npm install -g express 설치 
- npm install -g express-generator 를 통해 웹서버를 쉽게 만들 수 있음
- express는 웹 서버를 쉽게 만들 수 있는 프레임워크
- express --ejs gourmandmap 을 통해 gourmandmap 프로젝트 폴더 생성
- package.json에서 아래 코드를 작성하면 npm start를 하면 nodemon 서버가 돌아감(nodemon ./bin/www가 실행됨)
```json
"scripts": {
    "start": "nodemon ./bin/www"
  }
```
- npm start 또는 nodemon ./bin/www 을 통해 서버 실행 가능
- 네이버 클라우드 플랫폼 : 다양한 api 서비스를 사용할 수 있는 개발자 플랫폼
- jQuery라는 것은 클라이언트 쪽의 이벤트들을 조금더 쉽게 작성할 수 있도록 고안된 라이브러리
- jQuery cdn 구글 검색 -> 최상단 jQuery cdn 클릭 -> jQuery 3.x에서 minified script 복사
- cd '프로젝트 폴더명'
- npm install

## mongoose
- SQL : 데이터의 무결성 보장
- NoSQL : 유연하게 저장된 데이터를 조정, 추가 가능, 속도가 빠름
- NoSQL로 mongoDB 활용 가능
- DB를 더 쉽게 관리하고 입력할 수 있는 라이브러리 mongoose 사용 

## Compass 툴
- mongodb atlas 구글 검색
- MongoDB 호스팅 및 관리할 수있는 Compass 툴 설치 
- npm install mongoose 로 설치 

## Marker Clustering
- 아래 깃허브 사이트에 marker-clustering 폴더 클릭
- https://github.com/navermaps/marker-tools.js
- src 폴더 내에 MarkerClustering.js 코드 참고하기

## VScode 초기환경 셋팅
- 확장 프로그램 설치
- ejs Snippets 
- Korean Language Pack for VisualStudio

## Windows에 NVM 기반 Node.js 개발 환경 설치
- NVM은 다양한 프레임워크, 서버 등에 있어서 노드버전을 관리하기 좋음
- NVM 설치하는데 도움이 되는 Url
https://docs.microsoft.com/ko-kr/windows/nodejs/setup-on-windows

## Vue CLI의 env 파일 규칙과 실무 환경 구성 방법
https://cli.vuejs.org/guide/mode-and-env.html#modes

## 프로젝트 폴더에 다음과 같이 .env.production, .env.development,.env를 생성한다.
.env.production은 배포했을때 도메인 주소를 넣는다
.env.development는 로컬에서 개발할때 사용한다
.env.production와 .env.development 없을때 공통으로 들어가야 하는 것은
.env 파일안에 작성한다.
서버를 껐다가 켜야지 웹팩에 있는 설정파일들이 적용된다 

## 네이버지도 API로 구현한 지도기반 맛집 저장 서비스 실행 순서 
npm install -g nodemon
nodemon ./bin/www

## MYSQL Error
MYSQL Installer에서 MySQL Server 옆에 있는 Reconfigure 클릭 - Authentication Method 
기존 Use Strong Password Encryption for Authntication(RECOMMENTED) 에서 Uset Legecy Authentication Method 로 체크하기

## express-session 및 axios 설치 
npm install cores --save <br>
npm install express-session --save  <br>
npm install axios --save <br>

## frontend에서 chart를 사용하기 위한 설치
npm install --save chart.js vue-star-rating

## cookie를 사용하기 위한 설치 
npm install -s cookie

## cookie-parser를 사용하기 위한 설치
npm install cookie-parser

## 세션쿠키
사용자가 사이트 탐색 시에 관련한 설정들과 선호사항을 저장하는 임시 쿠키. 브라우저를 닫는 순간 삭제

## 지속쿠키
키속쿠키는 세션쿠키와 다르게 삭제되지 않고 더 길게 유지가 가능. 지속 쿠키는 디스크에 저장되며, 브라우저를 닫거나 컴퓨터를 재시작해도 남아있다. <br>
사용자 로그인 향상 유지와 같은 곳에 사용


## 토큰 기반 시스템이 제공해주는것은?
토큰 기반 시스템은 stateless 합니다. 이 용어의 의미는 '무상태' 라는 뜻 인데요. 서버시스템측에서 더 이상 유저의 정보를 유지하지 않고, 유저가 회원 인증을 하게 될 때 토큰 을 발급해줌으로서 유저가 자기 자신임을 인증 할 수 있게 해줍니다. 발급이 된 토큰은, 토큰의 유효기간, 그리고 정보를 담고 있으며, 해싱 알고리즘을 통해 인증이 되어있어서 서버에서 검증을 통하여 처음 서버가 발급해주었던 정보가 변조되지 않았음을 보장 해 줄 수 있습니다.

토큰을 사용함으로서, 서버를 확장하게 될 때에 매우 용이해지게 됩니다. 서버 시스템이 분산이 되어있어도, 유저는 같은 토큰으로 서버에 요청을 하면 되고, 서버는 그저 그 토큰이 위조되지 않았는지만 검증을 하고 데이터베이스 조회도 할 필요 없이 바로 유저임을 신뢰하고 처리를 하면 되기 때문이죠.

추가적으로, 토큰을 사용하면 플랫폼간 권한을 공유 할 수 있습니다. 예를들어서, 우리가 다음 강의에서 페이스북 / 구글 계정을 통한 소셜 로그인을 구현하게 될 텐데, 이게 가능한 이유도 구글과 페이스북에서 토큰기반인증 시스템을 사용하기 때문입니다. 소셜 로그인 과정에서, 구글/페이스북 플랫폼에서 로그인을 하고, 해당 플랫폼이 토큰을 발급을 해주면 우리의 백엔드 서버에서 이를 통하여 회원정보를 가져오고 우리의 서비스에 계정 생성을 하게 됩니다.

마지막으로, 토큰 기반 시스템은 모바일 어플리케이션에서 사용하기에 편해집니다. 만약에 세션 기반 인증을 사용한다면, 쿠키를 사용해야 하기 때문에, 쿠키 매니저를 따로 관리해줘야 하지만, 토큰을 사용한다면 웹 요청 API 에 헤더에 넣어서 사용해주면 되기때문에 더이상 쿠키 매니저를 사용 할 필요가 없어지죠.

## 토큰 저장 위치
서버가 토큰을 발급해주면, 브라우저에서 사용자 / 서버간에 토큰이 전달되는 방식은 크게 두가지로 나뉩니다. 첫번째는, 로그인에 성공하게 되었을 때 서버가 토큰을 응답정보에 토큰을 넣어서 전달하도록 하고, 해당 값을 웹 스토리지 (localStorage 혹은 sessionStorage) 에 넣고, 그 다음부터 웹 요청을 할 때마다 HTTP 헤더 값에 넣어서 요청하는 방법이 있습니다.

이 방법은, 구현하기 쉽고, 하나의 도메인에 제한되어있지 않다는 장점이 있지만, XSS 해킹 공격을 통하여 해커의 악성스크립트에 노출이 되는 경우 매우 쉽게 토큰이 탈취 될 수 있습니다. 그냥 localStorage 에 접근하면 바로 토큰에 접근 할 수 있기 때문이죠.

이에 대한 대안, 두번째 방식은 이 토큰을 쿠키에 넣는 것 입니다. 쿠키를 쓰지 않으려고 토큰을 쓰는 줄 알았는데, 갑자기 이렇게 설명을 하니 헷갈릴 수도 있습니다. 쿠키를 사용한다고해서 세션을 관리하는것은 아니고, 그저 쿠키를 정보 전송수단으로 사용 할 뿐입니다. 이 과정에서, 서버측에서 응답을 하면서 쿠키를 설정 해 줄 때 httpOnly 값을 활성화를 해주면, 네트워크 통신 상에서만 해당 쿠키가 붙게 됩니다. 따라서, 브라우저상에서는, 자바스크립트로 토큰값에 접근하는것이 불가능해지죠.

만약에 모바일 어플리케이션도 개발을 하게 된다면, 서버측에서 JWT 를 헤더 값으로도 받을 수 있게 하여 쿠키 혹은 헤더 둘 중 존재하는것을 토큰으로 인식하여 사용하도록 구현을 하면 됩니다.

두번째 대안에 대한 단점은, 쿠키가 한정된 도메인에서만 사용이 된다는 점 입니다. 이 부분은, 토큰이 필요해질 때 현재 쿠키에 있는 토큰을 사용하여 새 토큰을 문자열로 받아올 수 있게 하는 API를 구현하여 해결하면 됩니다.

또 다른 단점은, XSS의 위험에서 완벽히 해방되는 대신, CSRF 공격의 위험성이 생긴다는 점 입니다. CSRF은, 계정정보를 탈취하는것은 아니지만, 스크립트를 통하여 사이트의 외부에서 사이트의 API 를 사용하는것 처럼 모방하는 것 입니다. 혹은, 사이트 내부에서 스크립트가 실행되어 원하지 않는 작업이 수행되게 할 수도 있습니다.

CSRF 공격의 예제는 다음과 같은 항목들이 있습니다.

- 스크립트에 노출되는 순간...

- 유저도 모르는사이 탈퇴해버리기
- 댓글을 자동으로 작성
- 포스트를 자동으로 작성
- 회원정보 변경
하지만, 너무 걱정하지는 마세요, CSRF의 경우엔 HTTP 요청 레퍼러 체크, 그리고 CSRF 토큰의 사용을 통하여 방지 할 수 있습니다.

정리를 하자면, 웹스토리지에 토큰을 담으면 XSS 에 취약하고, 쿠키에 담으면 CSRF 에 취약해집니다. 하지만, CSRF는 보안에 신경을 쓰면 차단 할 수 있습니다.

우리는 앞으로 인증시스템을 구현 하면서, 토큰을 httpOnly 속성이 활성화된 쿠키에 담아서 구현을 하도록 하겠습니다.

## Json Web Tokens란?
JWT는 사용자 정보를 JSON 객체에 담아 이를 암호화하고 해싱 작업을 거쳐 문자열 토큰을 생성하는 기술<br>

## Json Web Tokens 설치 
JWT를 사용하기 위해서 jsonwebtoken 모듈을 설치합니다.<br>
npm install jsonwebtoken

## Json Web Tokens Decoding을 위한 라이브러리 설치
jwt-decode는 Base64URL로 인코딩되어있는(encoded) JWT 토큰을 디코딩(decoding)을 하는데 도움을 주는 라이브러리 입니다.  <br>
npm install jwt-decode


```javascript

//routes 폴더에서 index.js에서 jsonwebtoken을 가져와서 사용하고 싶을때 사용한다
var jwt = require('jsonwebtoken');

//쿠키에서 accessToken 라는 쿠키이름을 가져와서 token 변수에 저장한다
const token = req.cookies['accessToken'];

//토큰과 jwtSecret을 통해 검증
tokenResult = jwt.verify(token, jwtSecret)

//get으로 index 페이지를 불러올 때 사용한다
router.get("/mymap", (req, res, rows) => {               
  res.render("index", { title: "Express" });
});

// 쿠키를 출력해서 확인해보고 싶을때 사용한다
console.log(req.cookies);
// 쿠키이름이 accessToken인 값을 token 변수에 넣고 jwt_decode를 통해 토큰을 디코딩한다
var token = req.cookies['accessToken'];
var decoded = jwt_decode(token);

//헤더에 있는 쿠키값을 가져와서 jwtSecret 비밀키와 검증을 해서 인증을 한다 ? 
const token = req.headers.cookies.user
const tokenResult = jwt.verify(token, jwtSecret)
console.log(tokenResult)

// 헤더에 있는 토큰을 디코딩해서 출력한다 ?
var decodedHeader = jwt_decode(token, { header: true });
console.log(decodedHeader); 

//토큰을 디코딩해서 값을 확인한다
var token = "eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX251bSI6MSwidXNlcl9pZCI6ImVlIiwibmFtZSI6ImVlIn0.HEURm4BIXp6YogTzNPIAKu5tcHrFB9hQVhKKV157xnw";
var decoded = jwt-decode(token);
console.log(decoded);

```


## 토큰 데이터에서 USERNAME 가져오는 예제
```html
<a href="/mymap" id="name"></a>
```

```javascript
window.onload = function () {
  $.ajax({
      url: "/mymap/printname",
      type: "GET", 
  })
  .done((response) => {
      document.getElementById('name').innerHTML = `${response.data}님의 맛집지도 입니다`;
      console.log("토큰 데이터 입력 성공");
  })
  .fail((error) => {
      console.log("토큰 데이터 입력 실패");
  });
}
```
## 향후 사용 예정
쿠키에 있는 토큰 데이터를 mysql DB에 저장하기 위해 사용된다. <br>
프로젝트 끝나고 사용해볼 예정이다.
npm install -s express-mysql-session

## 참고 링크
https://crispypotato.tistory.com/58
https://www.npmjs.com/package/jwt-decode
https://victorydntmd.tistory.com/116  ----> 비밀키 모듈 생성하는 거 나와있음. 
https://www.npmjs.com/package/express-jwt