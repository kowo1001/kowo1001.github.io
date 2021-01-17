---
title: Vue-(4) vue와 axios
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

# 튜토리얼 요약
### axios란 
- 동적으로 데이터를 가져오기 위한 라이브러리
- Promise 기반의 API 형식
- Promis란 비동기 로직 처리에 유용한 자바스크립트 객체이다

|API유형|처리결과|
|:-------------------------:|:-------------------------------:|
|axios.get('URL주소').then().catch()|해당 URL로 get방식으로 요청<br>then()안에 반환값 로직 작성<br>catch()안에는 오류발생시 로직 작성|
|axios.post('URL주소').then().catch()|해당 URL로 POST방식으로 요청<br>then()안에 반환값 로직 작성<br>catch()안에는 오류발생시 로직 작성|
|axios({옵션})| HTTP요청에 대한 자세한 속성들을 직접 정의하여 보낼 수 있음|


웹 또는 앱을 개발하다 보면 거의 대부분이 서버가 필요하게 된다. <br>
서버에 내용을 저장하고 웹이나 앱에서 서버의 저장된 내용을 불러다가 사용자에게 보여주게 된다. 이때 javascript에는 axios라는 아주 훌륭한 플러그인이 있습니다.
axios는 javascript용 플러그인으로 많이 사용하지만 Vue.js에서도 매우 요긴하게 사용되어진다.

axios는 Promise 기반의 자바스크립트 비동기 처리방식을 사용한다.<br>
그래서 요청후 .then()으로 결과값을 받아서 처리를 하는 형식으로 구성되어 있습니다.

```javascript
axios.get('/api/data').then(res => { console.log(res.data) })
```
/api/data에서 데이터를 불러온다. <br>
불러온 데이터는 .then()의 res에 담아서 처리하는 식이다. <br>
여기서는 간단하게 크롬브라우저의 Console화면에 결과값을 보여주게 처리되어 있다. <br>

### axios 별칭으로 사용하기
axios는 REST을 별칭을 이용해서 쉽게 통신을 할 수 있다.
- 불러오기 : axios.get(url,)
- 입력하기 : axios.post(url,)
- 수정하기 : axios.patch(url,)
- 삭제하기 : axios.delete(url,)

### GET (불러오기)
GET은 서버로 부터 데이터를 가져오는데 사용한다.
아마도 가장많이 사용하는 명령어 일 것이다.
서버 주소인 /api/data로 부터 값을 불러올 때 사용한다.

```javascript
axios.get('/api/data') 
	.then(res => {
	// 불러온 값을 Console에 뿌려줍니다. 
	console.log(res.data) 
	})
```
axios 요청 시 파라미터 정보(/api/todos/1)를 입력하여 정보를 얻어 올 수 있다. 위의 것이 리스트를 불러온다면 지금 아래의 요청은 하나의 상세정보를 불러온다.
```javascript
axios.get('/api/data/1') 
	.then(res => { 
		console.log(`status code: ${res.status}`); 
		console.log(`headers: ${res.headers}`) 
		console.log(`data: ${res.data}`)
	})
```
axios 요청 시 파라미터 정보가 아니라 메소드의 두 번째 인자인 config 객체로 요청값을 넘길 수 있다.

```javascript
axios.get('/api/data', {
	params: { title: 'vue.js는 조으다.' },
	headers: { 'X-Api-Key': 'my-api-key' },
	timeout: 1000 //1초 이내에 응답이 없으면 에러 처리
}).then(res => {
	console.log(res.data)
})
```
## POST (값 입력하기)
/api/data에 값을 입력 할 때 사용한다.
서버의 데이터 리스트의 마지막에 지금 넘기는 정보를 추가한다
```javascript
axios.post('/api/data', {title: "vue.js는 조으다."}) 
	.then(res => { 
		console.log(res.data) 
	})
```
## PATCH (특정 값 수정하기)
/api/data/3에 값을 입력 할 때 사용합니다.
서버의 데이터 리스트 중 3에 해당 하는 값의 title를 수정합니다.
```javascript
axios.patch('/api/data/3', {title: "vue.js는 조으다."})
 .then(res => {
	console.log(res.data)
 })
```
## DELETE (특정 값 삭제하기)
/api/data/3에 값을 삭제 할 때 사용합니다.
서버의 데이터 리스트 중 3에 해당 하는 값을 삭제 합니다.
```javascript
axios.delete('/api/data/3') 
	.then(res => { 
		console.log(res.data)
	})
```
## ELSE) axios로 파일 업로드하기
axios로 파일도 업로드 할 수 있다. <br>
먼저 HTML로 아래와 같이 form문을 작성한다.

### HTML 코드
여기에서 ref="photoimage"는 중요한 역할을 하니 빼먹으면 안된다.
```html
<form method="post" enctype="multipart/form-data" action="/contant/124/photo">
	<input type="file" name="photo" ref="photoimage"> 
	<input type="submit"> 
</form>
```
### JAVASCRIPT 코드
FormData() 객체를 생성하고 this.$refs.photoimage과 같이 
ref옵션을 이용해서 필드에 직접 참조를 하여 
이미지파일을 가져오고 업로드를 할 수 있습니다.
```javascript
var data = new FormData(); 
var file = this.$refs.photoimage.files[0]; 
data.append('photo', file); 
axios.post('/api/data/' + this.no + '/photo', data) 
.then((res) => { 
	this.result = res.data; 
}) 
.catch((ex) => { 
	console.log('사진업로드 실패', ex);
});
```

# VSCODE에 있었던 코드 (FrontEnd)
## step11_ajaxCORS.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
</head>
<body>
    
    <div id="app">
        <label for="standard">Choose a standard!: </label>
        <select name="standard" v-model="info">
            <option v-for="(value, key) in model[0]" :value="key">{{key}}</option>
        </select>
        <template v-if="standard"> <!-- standard 라는 값이 있으면 실행 -->
            <select v-model="check">
                <option v-for="value in set[standard]" :value="value">{{value}}</option>
            </select>
            <table border="1" style="border-collapse: collapse;">
                <th v-for="(value, key) in model[0]">{{key}}</th>
                <tr v-for="value in model" v-if="value[standard]==check">
                    <td v-for=" employee in value">{{employee}}</td>
                </tr>
            </table>
        </template>
    </div>


    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        printEmployee();
        let vm = new Vue({
            el: "#app",
            data: {
                standard: "",
                check: "",
                model: [],
                set: {}
            },
            computed: {
                info: {
                    set: function (v) {
                        this.standard = v;
                        this.check = "";
                    },
                    get: function (v) {
                        this.check = "";
                    }
                }
            }
        });

        function printEmployee() {
            axios.get("http://localhost/step11_BackLogic/Controller?command=getAll", { 
				//http://localhost/step11_BackLogic/Controller?command=getAll이라는 url을 입력하여 정보를 얻어올 수 있다
            }).then(resData => { 
                vm.$data.model = resData.data;

                let modelSet = {};
                for (let value of resData.data) { // for( 데이터값 of 모든 데이터)
                    for (let key in value) { // for(데이터 키값 in 데이터값)
                        if (key in modelSet) { // modelSet에 넣고 key 중복 제거
                            modelSet[key].add(value[key]); 
                        } else {
                            modelSet[key] = new Set([value[key]]);
                        }
                    }
                }
                vm.$data.set = modelSet;
            }).catch(error => console.log(error)
            );
        }
    </script>
</body>
</html>


<!--
* 구현 로직 *
1. id/pw가 hr인 오라클 계정의 employees table 검색
    - all query
2. 서비스 로직
    1. 검색된 모든 자료를 다 출력
    2. employees table의 특정 컬럼을 스스로 지정해서 필터링 하고자 하는 로직 선별
    3. 입력시 동적으로 합? 평균? 등등의 수치 연산
    ...
3. 제약
    1. db의 검색 결과는 반드시 json 포멧으로 client에게 응답 ??? json-simple?
    2. json 관련 library 사용 필수 ??? 
    3. mvc pattern 미고려 가능, 프로젝트시에는 필수
        - jsp 하나로 다 처리하셔도 됨
    4. vue.js로 화면단 처리
    5. back end는 반드시 eclipse로 별도의 server
    6. front end는 반드시 vsc로 별도의 server
        5,6번 서버가 다르다
        도메인이 다르다 
        소통의 해결책 : CORS
    7. 비동기 필수 (axios 쓰기)

    발표까지 포함
-->

```

# 자바 이클립스에 있었던 코드 (BackEnd)
## index.jsp
```jsp
<%@page import="model.EmployeesDAO"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
	pageEncoding="UTF-8"%>
<% response.setHeader("Access-Control-Allow-Origin", "*"); %>

${requestScope.employeesAll.allEmployees}
```
<% response.setHeader("Access-Control-Allow-Origin", "*"); %>를 주석처리하면 다음과 같은 에러가 뜬다
### 에러 내용
![XMLHttpRequest CORS위반](https://user-images.githubusercontent.com/37354978/104808130-83045480-5827-11eb-87c2-79216448fa97.PNG)
XMLHttpRequest가 http://localhost/step11_BackLogic/Controller?command=getAll 쪽으로의 요청에 접근할 수 없다
이 요청은 http://127.0.0.1:5500 으로부터 왔는데, CORS 정책에 의해서 막혔어
'Access-Control-Allow-Origin 헤더가 존재하지 않으니까
"나는 SOP의 기본 정책에 따라서 네가 이걸 읽는 것을 허가하지 않을거야" 라는 의미이다

### SOP(Same Origin Policy)란?
한 origin으로부터 로드된 document 또는 script가 다른 origin의 리소스와 
상호작용할 수 있는 방법을 제한하는 중요한 보안 메커니즘.
-document가 외부리소스들과 상호작용 할 때 리소스의 origin이 document의 origin과 다른 경우에
뭔가 제한을 두겠다는게 Same Origin Policy이다.
-document가 외부리소스들과 상호작용 할 때 SOP가 적용된다고 했는데
어떤 상호작용들을 할때 SOP가 적용될까 
03:11 참고 (https://coding-groot.tistory.com/91)

### Origin이 무엇인지?
브라우저가 origin을 따질때, 딱 세가지인 Scheme, Host, Port 섹지만 보고선 origin을 판단한다
![Origin](https://user-images.githubusercontent.com/37354978/104808141-96172480-5827-11eb-89f9-00e0c3f4d3e2.jpg)
아래 그림에서 첫번째 , 두번째만이 Same-Origin임을 알 수 있다.
![12번이 origin](https://user-images.githubusercontent.com/37354978/104808152-a8915e00-5827-11eb-9ade-100a3278260e.PNG)

### SOP가 왜 중요한지?
SOP가 없으면 어떤 상황들이 발생할 수 있는지 - XMLHttpRequest에서 CSRF 공격을 당할 수 있다.
09:30 참고 (https://coding-groot.tistory.com/91)

### Cross-origin script API
Cross-origin network access
Cross-origin간의 통신이 필요할 경우
- Same-Origin : 상호간의 document에 자유롭게 접근 가능
- Cross-Origin : 상호간의 document 접근 불가, 매우 제한적인 객체에만 접근 가능



### CORS 정책이란
지금 같은 상황에서 cross-origin 간에 API를 요청하고 읽어드릴 필요가 있을 때가 있다
그럴 때에는 'Access-Control_Allow-Origin' 헤더에 이 데이터를 읽을 수 있는 origin을
따로 넣어줘야 한다.

예를 들어서, http://localhost/step11_BackLogic/Controller?command=getAll에서 데이터를 리턴해줄 때
'Access-Control-Allow-Origin' 헤더에 이 http://127.0.0.1:5500/step11_ajaxCORS.html 이라는 거를 넣어놓는다
그러면 읽을 때, origin은 다르지만 허용 origin 목록에 있네 ? 하고서 데이터를 읽을 수 있게 된다.
이게 CORS 정책이다.

### Cross-Origin이 필요한 경우
#### CORS 방식 사용
- 사용가능
- 반드시 허용할 origin만을 Access-Control-Allow-Origin에 추가
- 서버에서 리스폰스(response)를 줄 때, 리스폰스 헤더에 허용할 origin 만을 
Access-Control-Allow-Origin에 추가해주면 cross-origin인 경우에도 데이터를 읽을 수 있다.
- 주의할 점 : origin을 모든 origin 대상으로 열어놓는 경우들은 공격을 당할 수 있다 

#### JSONP 방식 사용
- 사용하지 않는 것을 추천
- JSONP를 이용해서 cross-origin간의 네트워크 엑세스를 할 수 있다.
- 그러나, 해당 API는 모든 origin 대상으로 SOP 정책을 다 열어 놓는다. 
- 만약에, JSONP 리스폰스(response)에 민감한 정보가 포함되어 있는 경우가 있다면 공격을 당할 수 있다.

## Controller.java
```java
package controller;

import java.io.IOException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import model.EmployeesDAO;
import model.dto.Employees;
import net.sf.json.JSONArray;
import net.sf.json.JSONException;
import net.sf.json.JSONObject;

@WebServlet("/Controller")
public class Controller extends HttpServlet {
	protected void service(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {
		request.setCharacterEncoding("utf-8");
		String command = request.getParameter("command");

		try {
			if (command.equals("getAll")) {
				getAllEmployees(request, response);
			}
		} catch (Exception s) {
			request.setAttribute("errorMsg", s.getMessage());
			request.getRequestDispatcher("showError.jsp").forward(request, response);
			s.printStackTrace();
		}
	}

	public void getAllEmployees(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException, JSONException {
		JSONObject obj = new JSONObject();
		String url = "showError.jsp";
		try {
			JSONArray jArray = new JSONArray();
			for (Employees e : EmployeesDAO.getAllEmployees()) {
				JSONObject s = new JSONObject();
				s.put("employee_id", e.getEmployee_id());
				s.put("first_name", e.getFirst_name());
				s.put("last_name", e.getLast_name());
				s.put("email", e.getEmail());
				s.put("phone_number", e.getPhone_number());
				s.put("hire_date", e.getHire_date());
				s.put("job_id", e.getJob_id());
				s.put("salar", e.getSalary());
				s.put("commisson_pct", e.getCommisson_pct());
				s.put("manager_id", e.getManager_id());
				s.put("department_id", e.getDepartment_id());
				jArray.add(s);
			}
			obj.put("allEmployees", jArray);
			request.setAttribute("employeesAll", obj);
			url = "index.jsp";
		} catch (Exception s) {
			request.setAttribute("errorMsg", s.getMessage());
		}
		request.getRequestDispatcher(url).forward(request, response);
	}
}

```
## EmployeesDAO.java
```java
package model;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;

import model.dto.Employees;
import model.util.DBUtil;

/*
 	private int employee_id;
	private String first_name;
	private String last_name;
	private String email;
	private String phone_number;
	private Date hire_date;
	private String job_id;
	private int salary;
	private int commisson_pct;
	private int manager_id;
	private int department_id;
 */

public class EmployeesDAO {
	public static ArrayList<Employees> getAllEmployees() throws SQLException{
		Connection con = null;
		PreparedStatement pstmt = null;
		ResultSet rset = null;
		ArrayList<Employees> list = null;
		try{
			con = DBUtil.getConnection();
			pstmt = con.prepareStatement("select * from employees");
			rset = pstmt.executeQuery();
			
			list = new ArrayList<Employees>();
			while(rset.next()){
				list.add(new Employees(
						rset.getInt(1),
						rset.getString(2),
						rset.getString(3),
						rset.getString(4),
						rset.getString(5),
						rset.getString(6),
						rset.getString(7),
						rset.getInt(8),
						rset.getInt(9),
						rset.getInt(10),
						rset.getInt(11)));
			}
		}finally{
			DBUtil.close(con, pstmt, rset);
		}
		return list;
	}
}	

```
## Employees.java
```java
package model.dto;

import java.util.Date;

import lombok.AllArgsConstructor;
import lombok.Getter;
import lombok.NoArgsConstructor;
import lombok.Setter;
import lombok.ToString;

@NoArgsConstructor
@AllArgsConstructor
@Setter
@Getter
@ToString
public class Employees {
	private int employee_id;
	private String first_name;
	private String last_name;
	private String email;
	private String phone_number;
	private String hire_date;
	private String job_id;
	private int salary;
	private int commisson_pct;
	private int manager_id;
	private int department_id;
}

```
## DBUtil.java
```java
package model.util;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.sql.DataSource;

public class DBUtil {
	
	private static DataSource source = null;

	//DataSource 객체에 server 내부에 설정된 정보를 기반으로 생성하는 코드
	static {
		try {
			Context ctx = new InitialContext();
			source = (DataSource) ctx.lookup("java:comp/env/jdbc/myoracle");
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	public static Connection getConnection() throws SQLException{
		return source.getConnection();
	}

	// DML용
	public static void close(Connection con, Statement stmt) {
		try {
			if (stmt != null) {
				stmt.close();
				stmt = null;
			}
			if (con != null) {
				con.close();
				con = null;
			}
		} catch (SQLException s) {
			s.printStackTrace();
		}
	}

	// SELECT용
	public static void close(Connection con, Statement stmt, ResultSet rset) {
		try {
			if (rset != null) {
				rset.close();
				rset = null;
			}
			if (stmt != null) {
				stmt.close();
				stmt = null;
			}
			if (con != null) {
				con.close();
				con = null;
			}
		} catch (SQLException s) {
			s.printStackTrace();
		}
	}
}

```
참고자료 
- Vue.js에서 axios를 사용하여 서버통신하는 방법(https://uxgjs.tistory.com/138)

