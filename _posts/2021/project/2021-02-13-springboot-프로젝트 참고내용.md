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

## 코로나맵 클론 프로젝트
- Node.js는 자바스크립트 런타임
- 런타임 : 프로그래밍 언어가 구동되는 환경
- npm : node package manager 
- 모듈 : 애플리케이션을 구성하는 개별적 요소(= 패키지)
- 모듈을 통해 기능적으로 분리되어 개발 효율성과 유지보수성 향상
- npm은 모듈들을 패키지화하여 모아둔 저장소 역할 및 설치 ,관리해주는 툴
- node --version 은 v.14.4.0을 사용
- npm --version은 6.14.0을 사용
- npm install -g nodemon을 통해 설치 
- 글로벌로 설치를 해서 다른 프로젝트 경로 상관없이 모든곳에서 nodemon 패키지를 쓸수 있도록 함
- nodemon은 서버를 껐다켰다하는 불편함을 해소시켜주는 필요한 패키지
- npm install -g express 설치 
- npm install -g express-generator 를 통해 웹서버를 쉽게 만들 수 있음
-  express는 웹 서버를 쉽게 만들 수 있는 프레임워크
- express --ejs gourmandmap 을 통해 gourmandmap 프로젝트 폴더 생성
- nodemon ./bin/www 을 통해 서버 실행 가능
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