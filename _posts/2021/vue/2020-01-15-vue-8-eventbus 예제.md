---
title: Vue-(8) eventbus 예제
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

```html
<html>
<body>
    <div id="languagelistapp">
        
        <div id="header" class="header">
            <h2>Language List</h2>
            <input class="input" type="text" v-model.trim="language"
            
                    placeholder="언어 입력 후 엔터" v-on:keyup.enter="addlanguage">
                    <!-- 엔터 쳤을때 addlanguage 메서드 호출 -->
            <span class="addbutton" v-on:click="addlanguage">추 가</span> 
            <!-- 클릭시 addlanguage 메서드 호출 -->
        </div>

        <ul id="languagelist">
            <li v-for="lang in languagelist" v-bind:class="checked(lang.lang)" v-on:click="langToggle(lang.id)">
                <span>{{ lang.language }}</span>
                <span v-if="lang.lang"> (학습완료)</span>
                <span class="close" v-on:click.stop="deletelanguage(lang.id)">&#x00D7;</span>
            </li>
        </ul>
    </div>


    
    <script type="text/javascript">
        var vm = new Vue({
            el: "#languagelistapp",
            data: {
                language: "",
                languagelist: [
                    { id: 1, language: "Python", lang: false },
                    { id: 2, language: "Java", lang: true },  //lang=true인 경우 학습 완료 의미
                    { id: 3, language: "JavaScript", lang: false },
                    { id: 4, language: "SQL", lang: false }
                ]
            },
            methods: {
                /* languagelist 데이터 속성에서 lang 속성이 true인 경우 checked 클래스를 적용 여부를 결정하는 기능 */
                checked: function (lang) {  //학습완료에 대한 체크 의미
                    if (lang) {
                        return { checked: true }
                    }else{
                        return { checked: false };
                    }
                },
                //추가 버튼을 클릭하거나 입력 필드에서엔터키를 눌렀을 때 할 일을 목록에서 추가하는 기능
                //v-on:keyup.enter="addlanguage" : enter 키 입력시 호출되는 메소드
                addlanguage: function (e) {
                    if (this.language !== "") {
                        this.languagelist.push({ id: new Date().getTime(), language: this.language, lang: false });
                        this.language = "";
                    }
                },
                //할 일 목록 오른쪽 상단의 x 를 클릭하면 목록에서 삭제
                //삭제를 위해서 배열의 splice 메소드 사용
                deletelanguage: function (id) {
                    var index = this.languagelist.findIndex(function (item) {
                        return item.id === id;
                    });
                    this.languagelist.splice(index, 1);
                },

                //list에서 선택된 id값과 배열의 id값 비교
                langToggle: function (id) {
                    //https://www.w3schools.com/jsref/jsref_findindex.asp
                    //findIndex() : 배열 내의 첫번째 index 검색
                    var index = this.languagelist.findIndex(function (item) {
                        return item.id === id;
                    });
                    //true <-> false
                    this.languagelist[index].lang = !this.languagelist[index].lang;
                }
            }
        })
    </script>
</body>

</html>

```

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

    <title>Event Bus를 활용한 실전 예제</title>
    <link rel="stylesheet" href="step22_review.css">
</head>
    

<body>
    <h3>컴포넌트화 하면서 이벤트 버스를 사용하여 컴포넌트 사이의 정보 교환</h3>

    <br><hr><br>
    1. 구조 : input 과 list 컴포넌트로 구분 <br>
    2. 두개의 컴포넌트간 데이터의 상호 작용을 이벤트 버스로 처리 <br>
    
    <br><hr><br>
    
    

<!-- input component -->
<template id="input-template">
    <div>
        <!-- 입력form, 바인딩된 model 필요, enter 키 이벤트 발생 -->
        <input class="input" type="text" id="task" placeholder="언어 입력하세요" 
                v-model.trim="language" v-on:keyup.enter="addlanguage">

        <span class="addbutton" v-on:click="addlanguage">추 가</span>
    </div>
</template>


<script type="text/javascript">
    //이벤트 버스
    let eventBus = new Vue();

    Vue.component('input-component', {
        template: '#input-template',
        data: function () {
            return { language: "" }
        },
        methods: {
            /* 입력 -> 이벤트 발생 + 데이터 전송 + model용 property 초기화 */
            addlanguage: function () { //엔터키 또는 추가 버튼 클릭시 호출
                eventBus.$emit('add-language', this.language); 
                this.language="";
            }
        }
    })
</script>


<!-- list component -->
<template id="list-template">
    <ul>
        <!-- v-bind:class="checked(true or false") : 
                1. true인 경우 : <li class="checked">
                2. false인 경우 : <li class>
        -->
        <li v-for="task in languagelist" v-bind:class="checked(task.lang)" v-on:click="langToggle(task.id)">
            
            <span>{{ task.language }}</span>
            <span v-if="task.lang"> (완료)</span>

            <span class="close" v-on:click.stop="deletelanguage(task.id)">&#x00D7;</span>
            
        </li>
    </ul>
</template> 

<script type="text/javascript">
    Vue.component('list-component', {
        template: '#list-template',
        data: function () {
            return {
                languagelist: [
                    { id: 1, language: "Python", lang: false },  
                    { id: 2, language: "Java", lang: true },  
                    { id: 3, language: "JavaScript", lang: false },
                    { id: 4, language: "SQL", lang: false }
                ]
            }
        },
        created: function () {
            console.log("created");
            eventBus.$on('add-language', this.addlanguage);
        },
        methods: {
            //완료 표현을 위한 메소드 : <li class="checked"> or <li class>
            checked: function (lang) {
                if(lang){
                    return {checked: true };
                }else{
                    return { checked: false };
                }
            },
            //languagelist 데이터 옵션을 변경하는 메소드들
            /* language  : 입력된 데이터를 languagelist에 저장 */
            addlanguage: function (language) { //이벤트 버스 객체에 바인딩되어 호출
                if (language !== "") {
                    this.languagelist.push({ 
                        id: new Date().getTime(), 
                        language: language, 
                        lang: false
                    });
                }
            },
            langToggle: function (id) {
                /* 선택한 id값과 일치되는 index 반환
                1. 배열내에 저장되어 있는 javascript 리터럴 객체의 id값을 비교해서 true or false 반환
                2. 해당 index 값의 true/false값 치환해서 toogle 적용
                */
                let index = this.languagelist.findIndex(function (item) {
                    return item.id === id;
                });
                this.languagelist[index].lang = !this.languagelist[index].lang;
            },
            deletelanguage: function (id) {
                var index = this.languagelist.findIndex(function (item) {
                    return item.id === id;
                });
                /* splice() 메소드는 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경, 원본 배열 자체를 수정 */
                this.languagelist.splice(index, 1); //(start, 삭제하고자 하는 개수)
            }
        }
    })
</script>

    <div id="languagelistapp">
        <div id="header" class="header">
            <h2>language List App</h2>
            <!-- 값 입력 및 추가 버튼 영역-->
            <input-component></input-component>
        </div>

        <!-- language list 영역-->
        <list-component></list-component>
    </div>
    
    <script type="text/javascript">
        var vm = new Vue({
            el: "#languagelistapp"
        })
    </script>
</body>
```
