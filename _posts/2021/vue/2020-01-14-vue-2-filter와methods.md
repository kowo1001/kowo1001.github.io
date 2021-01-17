---
title: Vue-(2) vue methods,filter
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

# 과제 내용
1. 제시된 데이터를 기반으로 해서 화면에는 filtering으로 이상형만 출력 (이상형 - 유진초이)
2. 모든 캐릭터들의 평균 나이 구하기
3. 여성 몇 명? 
{ "name": "유진초이", "age": 50, "sex": "male", "birthdate": 1871 },
{ "name": "고애신", "age": 34, "sex": "female", "birthdate": 1887 },
{ "name": "구동매", "age": 35, "sex": "male", "birthdate": 1886 },
{ "name": "김희성", "age": 36, "sex": "male", "birthdate": 1875 },
{ "name": "쿠도히나", "age": 41, "sex": "female", "birthdate": 1880 }

# methods, computed, filters의 차이점

## methods
    구현 후 호출시 () 표기 필수, 호출 시에 무조건 실행

## computed
    구현 후 호출 시에 속성명 호출하듯 호출, 첫 호출 시 브라우저 캐시에 실행 결과 저장,
    두번째 호출 시 값 변경이 안 되어 있을 경우 캐시 메모리 데이터 활용

### computed 사용 예시
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <div id="app">
        <dl>
            <dt> 1. 제시된 데이터를 기반으로 해서 화면에는 filtering으로 이상형만 출력 <br>
            <dd>
                이상형 : {{choice}}
            </dd>
            </dt>
        </dl>

        <dl>
            <dt>2. 모든 캐릭터들의 평균 나이 구하기 <br>
            <dd>
                평균 나이 : {{average}}
            </dd>
            </dt>
        </dl>

        <dl>
            <dt> 3. 여성 몇 명? <br>
            <dd>
                여성 : {{femalecount}} 명
            </dd>
            </dt>
        </dl>
    </div>
    
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
       
        //model
        let model = {
            sunshine: [
                { "name": "유진초이", "age": 50, "sex": "male", "birthdate": 1871 },
                { "name": "고애신", "age": 34, "sex": "female", "birthdate": 1887 },
                { "name": "구동매", "age": 35, "sex": "male", "birthdate": 1886 },
                { "name": "김희성", "age": 36, "sex": "male", "birthdate": 1875 },
                { "name": "쿠도히나", "age": 41, "sex": "female", "birthdate": 1880 }
            ]
        }

        //ViewModel
        let vm = new Vue({
            el: "#app",
            data: model,
            computed: {
                femalecount: function () {
                    let count = 0;
                    for (let i = 0; i < this.sunshine.length; i++) {
                        if (this.sunshine[i].sex === "female") {
                            count++;
                        }
                    }
                    return count;
                },
                choice: function () {
                    for (let i = 0; i < this.sunshine.length; i++) {
                        if (this.sunshine[i].age === 50 && this.sunshine[i].sex === "male" && this.sunshine[i].birthdate === 1871) {
                            return this.sunshine[i].name;
                        }
                    }
                },
                average: function () {
                    let sum = 0;
                    for (let i = 0; i < this.sunshine.length; i++) {
                        sum += this.sunshine[i].age;
                    }
                    return sum / this.sunshine.length;
                }
            }
        });
    </script>
</body>
</html>    
```

## filters
    호출 문법 자체가 | 연산자로 호출
    {{데이터|필터함수1|필터함수..}}
    메소드 체이닝 기법으로 다수의 메소드를 순차적으로 호출하고하 한다면 filters 활용 권장

### filters 사용 예시

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="app">
        이상형 : {{people | dream}} <br>
        평균 : {{people | sum | avg}} <br>
        여성 수 : {{people | women}}
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        let s = 0;
        let num = 0;
        let vm = new Vue({
            el : "#app",
            data : {
                people : [
                            {
                                "name": "유진초이",
                                "age": 50,
                                "sex": "male",
                                "birthdate": 1871
                            },
                            {
                                "name": "고애신",
                                "age": 34,
                                "sex": "female",
                                "birthdate": 1887
                            },
                            {
                                "name": "구동매",
                                "age": 35,
                                "sex": "male",
                                "birthdate": 1886
                            },
                            {
                                "name": "김희성",
                                "age": 36,
                                "sex": "male",
                                "birthdate": 1875
                            },
                            {
                                "name": "쿠도히나",
                                "age": 41,
                                "sex": "female",
                                "birthdate": 1880
                            }
        ]
            },
            filters : {
                dream : function(v){
                    for(let i =0; i <5;i++)
                    if(v[i].name == "유진초이")
                    return v[i].name;
                },
                sum : function(v){
                    for(let i =0; i <5;i++)
                    s += v[i].age
                    return s;
                },
                avg : function(v){
                    return v/5;
                },
                women : function(v){
                    for(let i =0; i <5;i++){
                        if(v[i].sex == "female")
                        num++;
                        if(i==4)
                        return num;
                    }
                }
            }
        })
    </script>
</body>
</html>
```

