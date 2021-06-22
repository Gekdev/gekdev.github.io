---
layout: default
title: Implicit Object
parent: Elements
grand_parent : JSP
nav_order: 2
---

# Elements Script
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Implicit Object
{: no_toc}

### What is Implicit Object

**JSP 페이지에서 사용할 수 있도록 JSP 컨테이너에 미리 정의된 객체**

&#9656; JSP는 웹애플리케이션 프로그래밍을 하는데 필요한 기능을 제공해주는 내장 객체를 제공 (객체들 마다 웹 애플리케이션에서 필요한 고유한 기능을 제공)

&#9656; JSP 페이지가 서블릿 프로그램으로 번역될 때 JSP 컨테이너가 자동으로 내장 객체를 멤버 변수, 메소드 매개변수 등의 각종 참조 변수(객체)로 포함

&#9656; JSP 페이지에 별도의 import문 없이 자유롭게 사용 가능

&#9656; 스크립틀릿 태그나 표혀문 태그에 선언을 하거나 객체를 생성하지 않고도 직접 호출하여 사용 가능

대표적인 내장 객체
{: .label .mt-2}

| 내장객체 | 반환유형 | 설명 |
|:--|:--|:--|
| request | javax.servlet.http.HttpServletRequest | 요청 파라미터 읽어오기, 웹 브라우저가 웹 서버에 요청하는 정보를 전달 |
| response | javax.servlet.http.HttpServletResponse | 응답 결과 전송하기, 웹서버에 요청된 결과를 응답하는 정보를 제공 |
| session | javax.servlet.http.HttpSession | 세션 처리하기 |
| application | javax.servlet.ServletContext | 웹어플리케이션 정보 읽어오기 |
| page | java.lang.Object | JSP 페이지를 구현한 자바 클래스로 JSP 페이지 자체를 나타냄 |
| out | javax.servlet.jsp.jspWriter | DOM 출력 |

![](https://gekdev.github.io/docs/jsp/elements/example/Implicitexample.png)

---

## Request Implicit Object

### Request Implicit Object Basic

**브라우저의 요청과 관련이 있음**

&#9656; jsp에서 가장 많이 사용되는 기본객체

&#9656; 웹 브라우저에서 서버의 JSP 페이지로 전달하는 정보를 저장 폼 페이지로부터 입력된 데이터를 전달하는 요청 파라미터 값을 JSP 페이지로 가져 옴

&#9656; JSP 컨테이너는 웹 브라우저에서 서버로 전달되는 정보를 처리하기 위해 javax,servlet.http.HttpServletRequest 객체 타입의 request 내장 객체를 사용하여 사용자의 요구 사항을 얻어 냄

&#9656; 웹브라우저에서 웹사이트의 주소를 입력하면 웹브라우저는 해당 웹 서버에 연결한 후 요청정보를 전송하는데 이 요청정보를 웹 서버에 제공하는 객체가 request 

### What can Request Object do?
 
1. 클라이언트(웹브라우저)와 관련된 정보

2. 서버와 관련된 정보

3. 클라이언트가 전송한 요청파라미터 정보

4. 클라이언트가 전송한 요청헤더 정보

5. 클라이언트가 전송한 쿠키 정보

### Request Parameter Methods

**request 객체의 요청 파라미터 관련 메서드**

1. getParameter(String name) : name(이름)인 파라미터의 값을 리턴, 없으면 null

    예제
    {: .label .label-purple .mt-2}
    ```jsp
    <h2>getParameter() 메서드</h2>
	name 파라미터 : <%= request.getParameter("name") %><br>
	addr 파라미터  : <%= request.getParameter("addr") %><br>
	```

2. getParameterValues(String name) : name(이름)인 모든 파라미터의 값을 배열로 리턴, 없으면 null

	체크박스에서 자주 사용됨

    예제
    {: .label .label-purple .mt-2}
    ```jsp
    <h2>getParameterValues() 메서드</h2>
	<%
	
	String[] values = request.getParameterValues("pet");
	if(values!=null){
		for(String value:values){
	%>		
			<%= value %><br>
	<%
		}
	}
	
	%>
    ```
    
3. getParameterNames() : 웹브라우저가 전송한 파라미터의 이름목록을 리턴

    ```jsp
    <h2>getParameterNames() 메소드</h2>
	<%
		Enumeration<String> names = request.getParameterNames();
		
		while(names.hasMoreElements()){
			String name = names.nextElement();
			if(name!=null){
	%>
				요청파라미터 이름 : <%= name %> <br>
	<%
			}
		}
	
	%>
    ```
    
4. getParameterMap() : 웹브라우저가 전송한 파라미터를 Map타입으로 리턴

    ```jsp
    <h2>getParameterMap() 메소드</h2>
	<%
	
		Map map = request.getParameterMap();
		String[] param = (String[]) map.get("name");
	
		if(param != null){
	%>
			요청파라미터 이름 : <%= param[0] %> <br>
	<%
		}
		
	%>
    ```
    
### Request Header Methods

**request 객체의 요청 헤더정보 관련 메서드**

1. getHeader(String name) : 지정한 name의 헤더의 값을 리턴

2. getHeaders(String name) : 지정한 name의 헤더목록을 리턴

3. getHeaderName() : 모든 헤더이름을 리턴

4. getIntHeader(String name) : 지정한 헤더의 값을 정수값으로 리턴

5. getDateHeader(String name) : 지정한 헤더의 값을 시간값으로 리턴

### Request Basic Methods

**웹 브라우저/서버 관련 메소드**

1. getRemoteAddr() : 웹서버에 연결한 클라이언트 IP주소

2. getContentLength() : 클라이언트가 요청한 정보의 총 길이

3. getCharacterEncoding() : 클라이언트가 요청정보를 전송할 때 사용한 문자셋정보

4. getContentType() : 클라이언트가 요청정보를 전송할 때 사용한 컨텐츠(문서) 타입정보

5. getProtocol() : 클라이언트가 요청한 프로토콜 정보

6. getMethod() : 웹브라우저가 정보를 전송할 때 사용한 방식(get/post)

7. getRequestURL() : 웹브라우저가 요청한 URL 경로

8. getContextPath() : JSP페이지가 소속된 웹어플리케이션의 context정보 

9. getServerName() : 연결할 때 사용한 웹서버의 이름

10. getServerPort() : 연결할 때 사용한 웹 서버의 포트번호

예제
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/jsp/elements/example/basicrec.jpg)
</div>
```jsp
<h1>request기본객체의 정보</h1>

1. 클라이언트 IP주소 : <%= request.getRemoteAddr() %><br>

2. 요청정보의 길이 : <%= request.getContentLength() %><br>

3. 요청정보의 인코딩 : <%= request.getCharacterEncoding() %><br>

4. 요청정보의 컨텐츠타입 : <%= request.getContentType() %><br>

5. 요청정보의 프로토콜 : <%= request.getProtocol() %><br>

6. 요청정보의 전송방식 : <%= request.getMethod() %><br>

7. 요청정보의 URL : <%= request.getRequestURL() %><br>

8. 요청정보의 컨텍스트 경로 : <%= request.getContextPath() %><br> 

9. 요청정보의 서버이름 : <%= request.getServerName() %><br>

10. 요청정보의 서버포트번호 : <%= request.getServerPort() %><br>
```

---

## Response Implicit Object

### Response Implicit Object Basic

**웹 서버가 웹브라우저에 전송하는 응답정보를 가지고 있음**

&#9656; 사용자의 요청을 처리한 결과를 서버에서 웹 브라우저로 전달하는 정보를 저장하고 서버는 응답 헤더와 요청 처리 결과 데이터를 웹 브라우저로 보냄

&#9656; JSP 컨테이너는 서버에서 웹 브라우저로 응답하는 정보를 처리하기 위해 javax.servlet.http.HttpServelteResponse 객체 타입의 response 내장 객체를 사용하여 사용자의 요청에 응답

&#9656; response객체는 request객체와 반대의 기능을 가지고 있음

### Response Header Method

**응답 HTTP 헤더 관련 메소드**

1. addDateHeader(String name, long date) : name헤더에 date값을 추가

2. addHeader(String name, String value) : name 헤더에 value값을 추가

3. addIntHeader(String name, int value) : name 헤더에 int값을 추가

4. setHeader(String name, String value) : name 헤더에 value값을 지정

5. setIntHeader(String name, int value) : name 헤더에 정수값을 지정

6. setDateHeader(String name, long date) : name 헤더에 date값을 지정

### Cache Control Response Header on Web Browser

**웹브라우저에 캐쉬 제어관련 응답헤더**

jsp를 비롯한 웹어플리케이션을 개발할 경우 새로운 내용을 DB에 추가했음에도 웹브라우저에 출력되는 내용이 변경되지 않는 경우가 있는데 그 이유중 하나는 웹브라우저가 서버가 생성한 결과를 출력하지 않고 캐시에 저장된 데이터를 출력하기 때문

웹 브라우저는 첫 번째 요청시에 응답결과를 로컬피씨의 임시저장소인 캐시에 저장

이후 동일한 URL에 대한 요청이 있을 경우에 WAS에 접근하지 않고 로컬피씨에 저장된 응답결과를 사용함

캐시에 보관된 데이터를 사용할 경우 서버에 접근하지 않기 때문에 훨씬 빠른결과를 웹브라우저에 출력할 수 있음

따라서 변경이 발생하지 않은 경우에 JSP 응답결과나 이미지, 정적인 html 등은 캐시에 보관함으로써 웹 브라우저의 응답속도를 향상시킬 수 있음

캐시(Cash)란?
{: .label .mt-2}
<div class="code-example" markdown="1">
웹 브라우저가 WAS에 jsp실행을 요청하고 잠시 뒤에 동일한 jsp실행을 요청한 경우 첫 번째 요청과 두 번째 요청사이에 결과 차이가 없을 경우에 불필요한 응답결과를 반복해서 요청한 셈이 됨

캐시는 이렇게 동일한 데이터를 중복해서 로딩하지 않도록 할 경우에 사용됨
</div>

### Add Header Method

헤더 추가 메서드

1. Cache-Control : 이 헤더값을 "no-cache"로 지정하면 웹브라우저는 응답결과를 캐시에 사용하지 않음

2. Pragma : 이 헤더값을 "no-cache"로 지정하면 웹브라우저는 응답결과를 캐시에 사용하지 않음

3. Expires : 응답결과의 만료시간을 지정한다

### Moving Pages Method

**페이지 이동 = 리다이렉션(redirection), 사용자가 새로운 페이지를 요청할 때와 같이 페이지를 강제로 이동하는 것**

&#9656; 반환유형 void

&#9656; 페이지 이동 시에는 문자 인코딩을 알맞게 설정해야 함

&#9656; response 객체에서 가장 많이 사용되는 기능 중 하나임

syntax
{: .label .label-purple .mt-2}
{: .label .mt-2}
<div class="code-example" markdown="1">
<% response.sendRedirect("String url"); %>
</div>
```jsp
<%
String id = request.getParameter("id");
if(id!=null && id.equals("sohyang")){
	response.sendRedirect("jsp02_09_parameters.jsp");
}else{
%>
```

![](https://gekdev.github.io/docs/jsp/elements/example/redi.png)

forward와의 차이
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
요청을해서 A라는 페이지로 이동해주세요, 하는데 요청자에게 block이 되서 정보를 제한적으로 이동(내가 갖고 있는 페이지에서만 이동이 가능)

redirect를 하게되면 내가 갖고 있지 않더라도 요청자에게 정보를 공개적으로 제공(내가 갖고 있지 않더라도 페이지 이동 가능)
</div>

---

## Out Implicit Object

### Out Implicit Object Basic

**웹 브라우저에 데이터를 전송하는 출력 스트림 객체**

&#9656; JSP 컨테이너는 JSP 페이지에 사용되는 모든 표현문 태그와 HTML, 일반텍스트 등을 out 내장 객체를 통해 웹 브라우저에 그대로 전달

&#9656; 스크립틀릿 태그에 사용하여 단순히 값을 출려가는 표현문 태그(<%= ...%>)와 같은 결과를 얻을 수 있음
