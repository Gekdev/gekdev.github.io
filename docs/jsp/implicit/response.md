---
layout: default
title: Response
parent: Implicit Object
grand_parent : JSP
nav_order: 2
---

# Response Implicit Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

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