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

### What Can Request Object Do?
 
1. 클라이언트(웹브라우저)와 관련된 정보

2. 서버와 관련된 정보

3. 클라이언트가 전송한 요청파라미터 정보

4. 클라이언트가 전송한 요청헤더 정보

5. 클라이언트가 전송한 쿠키 정보

6. 속성처리 기능

### Request Basic Methods

**웹 브라우저/서버 관련 메소드**

몇가지 정보는 웹 브라우저에 입력한 URL로부터 추출되는 것을 확인할 수 있음

| 메서드 | 리턴타입 | 설명 |
|:-------|:---------|:-----|
| getRemoteAddr() | String | 웹서버에 연결한 클라이언트 IP주소 |
| getContentLength() | long | 클라이언트가 요청한 정보의 총 길이 |
| getCharacterEncoding() | String | 클라이언트가 요청정보를 전송할 때 사용한 문자셋정보 |
| getContentType() | String | 클라이언트가 요청정보를 전송할 때 사용한 컨텐츠(문서) 타입정보 |
| getProtocol() | String | 클라이언트가 요청한 프로토콜 정보 |
| getMethod() | String | 웹브라우저가 정보를 전송할 때 사용한 방식(get/post) |
| getRequestURL() | String | 웹브라우저가 요청한 URL 경로 |
| getContextPath() | String | JSP페이지가 소속된 웹어플리케이션의 context정보  |
| getServerName() | String | 연결할 때 사용한 웹서버의 이름 |
| getServerPort() | int | 연결할 때 사용한 웹 서버의 포트번호 |

예제
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/jsp/example/basicrec.jpg)
</div>
```jsp
<h1>request기본객체의 정보</h1>

1. 클라이언트 IP주소 : <%= request.getRemoteAddr() %> : request.getRemoteAddr()<br> 

2. 요청정보의 길이 : <%= request.getContentLength() %> : request.getContentLength()<br>

3. 요청정보의 인코딩 : <%= request.getCharacterEncoding() %> : request.getCharacterEncoding()<br>

4. 요청정보의 컨텐츠타입 : <%= request.getContentType() %> : request.getContentType()<br>

5. 요청정보의 프로토콜 : <%= request.getProtocol() %> : request.getProtocol()<br>

6. 요청정보의 전송방식 : <%= request.getMethod() %> : request.getMethod()<br>

7. 요청정보의 URL : <%= request.getRequestURL() %> : request.getRequestURL()<br>

8. 요청정보의 컨텍스트 경로 : <%= request.getContextPath() %> : request.getContextPath()<br> 

9. 요청정보의 서버이름 : <%= request.getServerName() %> : request.getServerName()<br>

10. 요청정보의 서버포트번호 : <%= request.getServerPort() %> : request.getServerPort()<br>
```

### Request Parameter Methods

**request 객체의 요청 파라미터 관련 메서드**

입력한 데이터는 요청 파라미터로 전송되며 request기본 객체의 메서드를 사용해서 요청 파라미터를 읽어올 수 있음

1. **getParameter(String name) : name(이름)인 파라미터의 값을 리턴, 없으면 null**

    예제
    {: .label .label-purple .mt-2}
    ```jsp
    <h2>getParameter() 메서드</h2>
	name 파라미터 : <%= request.getParameter("name") %><br>
	addr 파라미터  : <%= request.getParameter("addr") %><br>
	```

2. **getParameterValues(String name) : name(이름)인 모든 파라미터의 값을 배열로 리턴, 없으면 null**

	&#9656; 체크박스에서 자주 사용됨

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
    
3. **getParameterNames() : 웹브라우저가 전송한 파라미터의 이름목록을 리턴**

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
    
4. **getParameterMap() : 웹브라우저가 전송한 파라미터를 Map타입으로 리턴**

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

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
체크박스나 라디오버튼은 선택하지 않으면 파라미터 자체가 전송되지 않음

하지만 텍스트를 위한 입력요소들은 값을 입력하지 않아도 빈 문자열이 파라미터값으로 전달됨
</div>

### Method GET & POST 

* **GET 방식 : 쿼리 문자열의 형식으로 파라미터가 전송됨 (이름1=값1&이름2=값2&...이름n=값n)**
    
    &#9656; 파라미터 전송시, 요청 헤더에도 파라미터가 포함됨
    
    &#9656; 웹 브라우저, 웹 서버 또는 웹 컨테이너에 따라 전송할 수 있는 파라미터 값의 길이에 제한이 있을 수 있음
    
    ![](https://gekdev.github.io/docs/jsp/implicit/example/get.jpg)

* **POST 방식 : 데이터 영역을 이용해서 파라미터를 전송**

    &#9656; 파라미터 전송시, 요청 헤더에는 포함되지 않고 데이터 영역에 전송됨

    &#9656; 데이터 영역을 이용해서 데이터를 전송하기 때문에 웹 브라우저나 웹 서버 등에 상관없이 전송할 수 있는 파라미터의 길이에 제한없음

    ![](https://gekdev.github.io/docs/jsp/implicit/example/post.jpg)

### Encoding Request Parameters

웹 브라우저는 웹 서버에 파라미터를 전송할 때 알맞은 캐릭터 셋을 이용해서 파라미터값을 인코딩함

반대로 웹 서버는 알맞은 캐릭터 셋을 사용해서 웹 브라우저가 전송한 파라미터 데이터를 디코딩함

![](https://gekdev.github.io/docs/jsp/implicit/example/enco.png)

만약 인코딩, 디코딩 시 서로 사용한 캐릭터 셋이 다르다면 웹 서버는 잘못된 파라미터 값을 사용하게 됨

* POST 방식이용 시 파라미터 전송 방법 : 입력 폼을 보여주는 응답 화면이 사용하는 캐릭터 셋을 사용

    **서버에서 파라미터 값을 알맞게 사용하려면 웹 브라우저가 파라미터 값을 인코딩할때 사용한 캐릭터 셋을 이용해서 디코딩 해야 함**

    request 기본객체의 setCharacterEncoding 메서드를 이용해 파라미터 값을 디코딩 할 때 사용할 캐릭터 셋을 지정할 수 있음 

    ```jsp
    <%
    request.setCharacterEncoding("utf-8")
    %>
    ...
    <!-- name 파라미터 값을 utf-8로 디코딩해서 가져옴 -->
    <%= request.getParameter("name") %>
    ```

    request.getParameter() 메서드나 request.getParameterValues() 메서드는 요청 파라미터의 값을 읽어올 때 request.setCharacterEncoding() 메서드로 지정한 캐릭터 셋을 이용해서 디코딩함

    request.setCharacterEncoding() 메서드를 사용해서 캐릭터 셋을 지정하지 않았을 경우 ISO-8859-1 셋을 기본으로 사용

    request.setCharacterEncoding()는 getParameter()를 사용하기 전에 사용해야 함

* GET 방식이용 시 파라미터 전송 방법

    * a태그의 링크 태그에 쿼리 문자열 추가 : 웹페이지 인코딩 사용 
    
    * html폼의 method 속성값을 get으로 지정해서 폼을 전송 : 웹페이지 인코딩 사용 
    
    * 웹 브라우저에 주소에 직접 쿼리 문자열을 포함하는 URL 입력 : 웹브라우저마다 다름
    
    get방식으로 전송된 파라미터에 대해서는 request.setCharacterEncoding()메서드로 지정한 캐릭터 셋이 저장되지 않음
    
    톰켓에서 get방식 파라미터를 위한 인코딩 처리하기
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    server.xml파일에서 <Connector>의 useBodyEncoingForURI = "true"로 지정하면 request.setCharacterEncoding() 메서드로 지정한 캐릭터 셋을 사용함
    </div>

[JSP2.3 웹 프로그래밍 기초부터 중급까지 83 ~ 88p까지 내용]
{: .mt-3}

### Request Header Methods

**request 객체의 요청 헤더정보 관련 메서드**

| 메서드 | 리턴타입 | 설명 |
|:-------|:---------|:-----|
| getHeader(String name) | String | 지정한 name의 헤더의 값을 리턴 |
| getHeaders(String name) | java.util.Enumeration | 지정한 name의 헤더목록을 리턴 |
| getHeaderName() | java.util.Enumeration | 모든 헤더이름을 리턴 |
| getIntHeader(String name) | int | 지정한 헤더의 값을 정수값으로 리턴 |
| getDateHeader(String name) | long | 지정한 헤더의 값을 시간값으로 리턴 |

배운 코드 추가하기