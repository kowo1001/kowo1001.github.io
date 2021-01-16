---
title: Vue-(6) JsonObject와 JsonArray
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

## JSON 형식

JSON은 "key-value"가 쌍으로 이루어진 데이터들의 집합이다.
key와 value 사이를 : 을 이용하여 구분하는 형식을 취한다.
이런 형태의 이점은,
사용자가 value값을 기억 할 필요가 없이 여러 데이터들의 공통된 key값만 알고 있으면 데이터를 손쉽게 추출해 낼 수 있다는 점이다.
이와 관련해서는 뒤에 예를 들어보겠다.

우선 아래의 예를 보자.
 "one" : "Suwon"
위와 같은 형태에서는 "one"이 key가 되는 것이며, 그에 해당하는 "Suwon"이 value가 되어 데이터가 저장되는 것이다.

여기에서, 각 데이터는 String의 형태로 저장되어 있음을 확인할 수 있다.
하지만 꼭 문자열이 key-value값의 데이터 형식이 될 필요는 없다는 것이 핵심이다.

"name" : "동현"
"age" : 26
"etc" : ["apple", 19, "수원"]
위와 같은 형태로 문자열 뿐 아니라 숫자, 배열등의 형태로도 작성이 가능하다는 것이다.
특히, 배열은 '[ ]'의 괄호안에 그 값들을 담으며, comma(,)로 값을 분리하는 것 역시 파악 가능하다.

## JSONArray
- 배열 구조이다
- 배열 안에는 문자열, 숫자, 배열, 객체 등을 담을 수 있다.
- [ ]의 대괄호를 이용하여 값들을 담으며, comma(,)로 그 값을 구분한다.
- 후에 index를 이용하여 값을 꺼낼 수 있으므로 그 순서에 대한 고려를 해주어야 한다.

## JSONObject
- 하나 이상의 key-value 쌍을 { }의 중괄호를 이용하여 담고있는 객체 구조이다.
- key와 value 사이의 구분은 colon(:)으로 한다.
- key-value 묶음간의 구분은 comma(,)로 한다.
- 순서가 구분되지 않은 집합체이다.

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
		JSONObject obj = new JSONObject(); // 중괄호에 들어갈 속성 정의 { "a" : "1", "b" : "2" }
		String url = "showError.jsp";
		try {
			JSONArray jArray = new JSONArray(); //JSONArray 객체를 생성하여 대괄호 정의 [{ "a" : "1", "b" : "2" }]
			for (Employees e : EmployeesDAO.getAllEmployees()) { // EmployeesDAO의 getAllEmployees메소드를 통해 Employees 객체를 가져와서 반복문을 돌린다
				JSONObject s = new JSONObject(); // JSONObject 객체를 생성하여 중괄호로 감싸 대괄호의 이름을 정의함 { "c" : [{  "a" : "1", "b" : "2" }] }
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