---
layout: default
title: PageContext
parent: Implicit Object
grand_parent : JSP
nav_order: 5
---

# PageContext Implicit Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## PageContext Implicit Object

PageContext 페이지는 JSP페이지와 일대일로 연결된 객체

1. 기본객체 구하기 : 직접 사용하는 경우는 드물지만 커스텀 태그를 구현할 때 사용됨

2. 속성처리하기

3. 페이지 흐름을 제어하기 

4. 에러데이터 구하기

### 기본객체 접근 메소드

| 메서드 				| 리턴타입 			| 설명 						  |
|:----------------------|:------------------|:-----------------------------|
| getRequest() 			| ServletRequest 	| request 기본 객체를 구함 	|
| getResponse() 		| ServletResponse 	| response 기본 객체를 구함 	|
| getSession() 			| HttpSession 		| session 기본 객체를 구함		|
| getServletContext() 	| ServletContext 	| application 기본 객체를 구함	|
| getServletConfig() 	| ServletConfig 	| config 기본 객체를 구함		|
| getOut() 				| JspWriter 		| out 기본 객체를 구함			|
| getException() 		| Exception 		| exception 기본 객체를 구함	|
| getPage()  			| Object 			| page 기본 객체를 구함		|

```jsp
<% HttpServletRequest req = (HttpServletRequest) pageContext.getRequest(); %>
pageContext에서 가져온 request 객체의 정보 : <%= req.getRemoteAddr() %> <br/>
request객체에서 직접 가져온 정보 : <%= request.getRemoteAddr() %> <br/>
둘이 같은 객체인가요? <%= req == request %> <br/>
<%= req %> <br/>
<%= request %> <br/>

<hr />

<% out.print("out객체에서 직접출력"); %> <br/>
<% pageContext.getOut().print("pageContext에서 가져온 out객체에서 직접출력"); %> <br/>
둘이 같은 객체인가요? <%= out == pageContext.getOut() %> <br/>
<%= out %> <br/>
<%= pageContext.getOut() %> <br/>
```

![](pagecont.jpg)
