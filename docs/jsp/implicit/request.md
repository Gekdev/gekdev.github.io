---
layout: default
title: Request
parent: Implicit Object
grand_parent : JSP
nav_order: 1
---

# Request Implicit Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

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
