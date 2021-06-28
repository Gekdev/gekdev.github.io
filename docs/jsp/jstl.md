---
layout: default
title: JSTL
parent: JSP
nav_order: 9
---

# JSP JSTL
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSTL

### What is JSTL?

**JSTL(JavaServer Pages Standard Tag Library) : 커스텀 태그 중 자주 사용하는 것들을 별도로 표준화한 태그 라이브러리**

커스텀 태그 : JSP를 확장시켜주는 기능, 액션태그와 마찬가지로 태그 형태로 기능을 제공

액션태그와의 차이점은 커스텀 태그는 개발자가 직접 개발해주어야 함

### Features of JSTL

* if-else조건문 그리고 for 구문과 같은 반복 처리를 커스텀 태그를 이용해서 구현할 수 있도록 함

* 스크립트 코드보다 이해하기 쉽기 때문에 자바 언어에 익숙하지 않더라도 JSTL을 이용해서 어느 정도 논리적인 처리를 수행할 수 있음

### Why Use JSTL?

사용목적 : JSP코드에서 중복되는 것을 모듈화하거나 스크립트 코드를 사용할 때 발생하는 소스 코드의 복잡함을 없애기 위해 사용

JSP는 스크립트릿과 표현식등의 스크립트 코드와 HTML등의 코드가 뒤섞여서 사용하기 때문에

JSP코드는 가독성이 떨어지고 코딩하기가 매우 복잡하게 되어있어서 개발이 편리하지 않게 되었음

그래서 JSP를 새로운 태그를 포함한 표준 라이브러리 형태로 제공하여 보다 쉽게, 가독성이 좋게 코딩할 수 있도록 제공하는데

**JSP페이지에서 많이 사용되는 논리적인 판단, 반복처리, 포맷처리 등을 쉽게 할 수 있도록 표준으로 만들어서 라이브러리형태로 제공하는 것이 JSTL**

### JSTL Tags

JSTL은 다섯가지 태그를 제공하고 있음

코어, 국제화, 함수를 가장 많이 사용함

| 라이브러리 | 주요기능 						   | 접두어    | 관련 URI 								  |	 
|:-----------|:---------------------------------|:----------|:------------------------------------------|
| core 		 | 변수지원, 흐름제어, URL처리 	  | c 		  | http://java.sun.com/jsp/jstl/core 	      |
| XML  		 | XML코어, 흐름제어, XML 변환처리  | x 		  | http://java.sun.com/jsp/jstl/xml          |
| 국제화	  | 지역, 메시지형식, 숫자/날짜 형식 | fmt 		| http://java.sun.com/jsp/jstl/fmt 		    |
| DB   		 | SQL, 메시지 형식 				   | sql 	   | http://java.sun.com/jsp/jstl/sql 		   |
| 함수 	   | 컬렉션처리, Strin 처리 		   | fn  	   | http://java.sun.com/jsp/jstl/functions    |

### Download JSTL Library

jstl-1.2.jar 파일을 클릭해서 다운로드 하면 됨

<span class="fs-2">
[다운로드](https://mvnrepository.com/artifact/javax.servlet/jstl/1.2){: .btn .btn-outline .mt-2}
</span>

---

## Core Tag

## Core Tag Basic

**변수설정이나 if-else와같은 논리 처리에 사용되는 스크립트 코드를 대체하는 태그를 제공**

아래 디렉티브를 추가해야지 사용할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>

&#9656; prefix : JSP코드에서 코어 태그 라이브러리를 호출할 때 사용할 접두어
</div>

### core Tag Library

| 기능 		   | 태그 	 | 설명 										|
|:---------------|:----------|:-------------------------------------------|
| 변수지원		 | set 		 | JSP에서 사용할 변수를 선언 				|
|				 | remove 	 | 설정변수를 삭제 						   |
| 흐름제어 		 | if  		 | 조건에 따라 흐름을 제어					|
|				 | choose 	 | 다중조건을 처리							   |
|				 | forEach 	 | 컬렉션이나 Map의 각 항목을 처리할 때 사용  |
|				 | forTokens | 구분자로 분리된 토큰을 처리 				  |
| URL처리 	   | import	   | URL에 해당되는 자원을 삽입				  |
| 				 | redirect  | 지정된 경로로 리다이렉트 실행 			 |
| 				 | url 		 | URL을 재작성 							  |
| 기타태그 		 | catch 	 | 익셉션처리								 |
| 				 | out 		 | JspWriter에 내용을 출력 					|

### <c:set> tag

**EL 변수의 값이나 EL변수의 프로퍼티 값을 지정할 때 사용**

1. EL변수를 생성할 때

    scope 속성에서 지정한 영역에 값을 저장

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    <c:set var="변수명" value="값" [scope="영역"] />

    <c:set var="변수명" [scope="영역"] /></c:set>

    &#9656; var : 값을 저장할 EL변수의 이름을 지정

    &#9656; value : 변수의 값을 지정. 표현식, EL, 정적인 텍스트를 사용해서 값을 지정

    &#9656; scope : 변수를 저장할 영역을 지정. page(기본값), request, session, application중 하나가 옴
    </div>
    
    예제
    {: .label .label-purple .mt-2}
    ```jsp
    <!--value 속성 사용의 예-->
    <c:set var="name" value="가은" />
    <c:set var="name" value="<%= m.getFirstName() %>" scope="request" />
    <c:set var="name" value="${m.lastName} ${m.firstName}" />
    
    <!--태그의 몸체를 값으로 사용하는 예-->
    <c:set var="name">가은</c:set>
    <c:set var="name"><%= m.getLastName() %> <%= m.getFirstName() %></c:set>
    <c:set var="name">${m.lastName} ${m.firstName}</c:set>

2. 객체의 프로퍼티 값을 설정할 때

    target대상이 EL변수인 경우 target속성의 값을 ${member}와 같이 EL을 이용해서 설정해야 함

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    <c:set target="대상" property="프로퍼티이름" value="값" />

    <c:set target="대상" property="프로퍼티이름" />값</c:set>

    &#9656; target : 프로퍼티 값을 설정할 대상 객체를 지정(자바빈 객체나 Map). 표현식이나 EL변수를 사용할 수 있음

    &#9656; property : 설정할 프로퍼티 이름을 지정

    &#9656; value : 프로퍼티의 값을 지정
    </div>
    
    예제
    {: .label .label-purple .mt-2}
    ```jsp
    <% Member member = new Member(); %>
    <!--member.setName("가은1")과 동일-->
    <c:set target="<%= member" property="name" value="가은1" />
    <%= member.getName() %> <!--값 가은1 출력-->
    
    <c:set var="m" value="<%= member %>" /> 
    <!--member.setName("가은2")과 동일-->
    <c:set target ="%{m} property="name" value="가은2" />
    ${m.name} <!--값 가은2 출력-->
    ```

c:set태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| var | 사용불가 | String | EL 변수 이름 |
| value | 사용가능 | Object | 변수에 할당할 값 |
| scope | 사용불가 | String | 변수를 생성할 영역, 기본값은 page |
| target | 사용가능 | Object | 프로퍼티 값을 설정할 객체 지정 |
| property | 사용가능 | String | 프로퍼티 이름 |
    
### <c:remove> tag

**set 태그로 지정한 변수를 삭제할 때 사용**

var속성과 scope 속성은 set태그의 두 속성과 동일한 의미를 갖음

주의할 점은 삭제할 변수의 scope를 지정하지 않으면 동일한 이름으로 저장된 모든 영역의 변수를 삭제함

따라서 서로 다른 영역에 동일한 이름을 갖는 변수가 존재하고 특정 영역에 속한 변수만 제거하고 싶다면 scope속성으로 명확하게 영역을 지정해줘야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<c:remove var="varName" [scope="영역"] />
</div>

c:remove태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| var | 사용불가 | String | 삭제할 EL 변수 이름 |
| scope | 사용불가 | String | 삭제할 변수가 포함된 영역 |

### <c:if> tag

**자바의 if블록과 비슷한 기능을 제공**

if-else블럭과 같은 효과를 낼 순 없지만 쉽게 대체하기 때문에 많이 사용

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<c:if test="조건" [var="testResult"]/>

...

</c:if>

${testResult}

var : 계산 결과를 EL변수에 저장할 수 있음
</div>

test 속성으로 올 수 있는것들
{: .label .label-purple .mt-2}
```jsp
<c:if test="true">
    <p>항상 true</p> 
</c:if>

<c:if test="some txt">
    <p>항상 false</p> 
</c:if>

<c:if test="${expr}"> EL의 결과값이 true인 경우 몸체 내용 실행 </c:if>

<c:if test="<%= expr %>"> 표현식의 결과 값이 true인 경우 몸체 내용 실행</c:if>
```

c:if태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| test | 사용가능 | Boolean | 검사 조건 |
| var | 사용불가 | String | 검사 조건의 계산 결과값을 저장할 EL변수 |
| scope | 사용불가 | String | 삭제할 변수가 포함된 영역 |

### <c:choose> / <c:when> / <c:otherwise> tag

<c:choose> tag : **자바의 switch구문과 if-else블록을 혼합한 형태로서 다수의 조건문을 하나의 블록에서 수행할 때 사용**
    
<c:when> test속성이 true일 때 내부 블록을 수행, 첫번째 true만 수행하고 나머지는 실행되지 않음

<c:when> test속성이 모두 false라면 c:otherwise가 실행됨, c:otherwise 태그는 필수는 아니고 필요한 경우에만 추가함

```jsp
<ul>
    <c:choose>
        <c:when test="${param.id == 'sohyang'}">
            <li>아이디는 ${param.id} 입니다 (JSTL / EL)</li> 
        </c:when>
        <c:when test="${param.age > 18}">
            <li>나이는 성인, ${param.age} 입니다 (JSTL / EL)</li> 
        </c:when>
        <c:otherwise>
            <li>당신의 아이디와 나이에 대한 정보가 없습니다</li>
        </c:otherwise>
    </c:choose>
</ul>
```

### <c:forEach> tag

**배열, Collection 또는 Map에 저장되어 있는 값들을 순차적으로 처리할 때 사용**

&#9656; for나 do-while을 대신해서 사용할 수 있음

&#9656; items 속성에는 Map, 배열, Collection이 올 수 있음

&#9656; 배열의 경우는 객체의 배열 뿐만 아니라 기본 데이터 타입의 배열에 댕해서도 알맞게 처리를 함 

&#8594; 기본 데이터 타입은 Integer나 Double과 같은 래퍼 클래스를 사용하여 처리

&#8594; begin, end, step 속성을 사용해서 조건을 변경할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<c:forEach var="변수" items="아이템">
    
${변수사용}
    
</c:forEach>
</div>

Map 사용하기
{: .label .label-purple .mt-2}
```jsp
<%@page import="java.util.Map"%>
<%@page import="java.util.HashMap"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%
	Map<String, Object> map = new HashMap<>();
	map.put("id", "sohyang");
	map.put("pw", "12345");
	map.put("name", "소향");
	map.put("addr", "경기 성남");
%>
<c:set var="data" value="<%= map %>"/>
...

<h3>Collection(Map) 계열</h3>
<c:forEach var="i" items="${data}">
    ${i.key} = ${i.value} <br>
</c:forEach>
```

Array 사용하기 : 기본
{: .label .label-purple .mt-2}
```jsp
<h3>Array</h3>
<c:set var="arr" value="<%= new int[]{1,2,3,4,5} %>"/>
<c:forEach var="i" items="${arr}">
    ${i}, 
</c:forEach>
```

Array 사용하기 : begin, end
{: .label .label-purple .mt-2}
```jsp
<h3>1~100까지의 홀수의 합</h3>
<c:forEach var="i" begin="1" end="100" step="2">
    <c:set var="sum" value="${sum + i}"/>
</c:forEach>
<p>1~100까지 홀수의 합 = ${sum}</p>
```

Array 사용하기 : varStatus
{: .label .label-purple .mt-2}
```jsp
<h3>Array</h3>
<c:set var="arr" value="<%= new int[]{1,2,3,4,5} %>"/>
<c:forEach var="i" items="${arr}" begin="2" end="4" varStatus="status">
    ${status.index} - ${status.count} - [${i}] <br>
</c:forEach>
```

![](https://gekdev.github.io/docs/jsp/foreach.jpg)

c:forEach태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| var | 사용불가 | String | 몸체에서 사용할 EL변수 이름 |
| items | 사용가능 | Collection, Iterator, Enumeration, Map, 배열 | 반복처리할 데이터 |
| varStatus | 사용불가 | String | 루프 상태를 저장할 EL변수 이름 |
| begin | 사용가능 | int | 시작 인덱스 값 |
| end | 사용가능 | int | 끝 인덱스 값 |
| step | 사용가능 | int | 인덱스 증분 값 |

#### varStatus property

루프 정보를 담는 객체를 저장할 변수 명을 값으로 갖음

c:forEach 태그 몸체에서는 varStatus 속성에 명시한 변수를 이용해서 현재 처리중인 인덱스, begin 속성값, end 속성값 등을 구할 수 있음

* index : 루프 실행에서 현재 인덱스

* count : 루프 실행 횟수

* begin : begin 속성 값

* end : end 속성값

* step : step 속성 값

* first : 현재 실행이 첫번 째 실행인 경우 true

* last : 현재 실행이 루프의 마지막 실행인 경우 true

* current : 컬렉션 중 현재 루프에서 사용할 객체

#### Example

**구구단 출력하기**

```jsp
<h3>구구단 출력하기</h3>
<c:forEach var="i" begin="2" end="9" step="1">
    <p>구구단 ${i}단 출력</p>
    <c:forEach var="j" begin="2" end="9" step="1">
    <ul>
        <li>
            ${i} * ${j} = ${i*j}
        </li>
    </ul>
    </c:forEach>
</c:forEach>
```

### <c:forTokens> tag

&#9656; java.util.StringTokenizer 클래스와 같은 기능을 제공하는 태그

&#9656; forEach 태그와 동일하게 begin, end, step, varStatus 속성을 제공

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<c:forTokens var="token" items="문자열" delims="구분자">

${value}
    
</c:forTokens>
</div>
```jsp
<h3>forTokens - 컴마(,)와 점(.)을 구분자로 사용</h3>
<c:forTokens var="value" items="빨,주,노,초.파,남.보" delims=",.">
    ${value}
</c:forTokens>
```

![](https://gekdev.github.io/docs/jsp/fortoken.jpg)

### <c:url> tag

**URL을 생성해주는 기능**

&#9656; var 속성을 지정하지 않으면 현재 위치에 생성한 URL을 출력, 지정하면 해당 변수에 생성한 URL을 저장

&#9656; param태그를 이용해서 파라미터를 URL에 추가할 수 있음

&#9656; value 속성은 절대URL(http://...)와 상대URL(/view...)로 지정함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<c:url value="URL" [var="varName"] [scope="영역"]>

<c:param name="이름" value="값" />
    
</c:url>
</div>
```jsp
<c:url value="http://search.daum.net/search" var="searchUrl">
	<c:param name="w" value="blog" />
	<c:param name="q" value="공원" />
</c:url>

<ul>
	<li>${searchUrl}</li>
	<li><c:url value="jsp11_01_if.jsp" /></li>
	<li><c:url value="/jsp11_01_if.jsp" /></li>
</ul>
```

![](https://gekdev.github.io/docs/jsp/urltag.jpg)

c:url태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| value | 사용 가능 | String | 읽어올 URL |
| var | 사용불가 | String | 읽어온 결과를 저장할 변수 이름 |
| scope | 사용 불가 | String | 변수를 저장할 영역 |

### <c:redirect> tag

**response.sendRedirect()처럼 지정한 페이지로 리다이렉트 시켜주는 기능을 제공**

&#9656; url속성 값이 슬래시로 시작할 경우 리다이렉트 URL에 컨텍스트 경로가 추가됨 (/a.jsp = chap12/a.jsp)

&#9656; 다른 컨텍스트 경로에 포함된 URL로 리다이렉트 하고 싶다면 context 속성에 다른 컨텍스트의 경로를 적어주면 됨 (context="/chap15")

&#9656; redirect 태그를 실행하면 그 이후 코드는 실행되지 않음

&#9656; param 태그를 이용해서 파라미터를 설정할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<c:redirect value="URL" [context="컨텍스트경로"]>

<c:param name="이름" value="값" />
    
</c:redirect>
</div>
```jsp
<c:redirect url="http://www.google.com" />
```

c:redirect태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| url | 사용가능 | String | 리다이렉트할 URL |
| context | 사용가능 | String | 컨텍스트 경로 |

### <c:out> tag

**JspWriter에 데이터를 출력할 때 사용되는 태그**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<c:out value="value" [escapeXml="(true|false)"] [default="기본값"] />
    
<c:out value="value" [escapeXml="(true|false)"] > 기본값 </c:out>
</div>
```jsp
<c:redirect url="http://www.google.com" />
```

1. value : JspWriter에 출력할 값을 지정, 일반적으로 value의 속성타입은 String

2. escapeXML : 이 속성값이 true일 경우 아래와 같이 문자를 변경

    ```jsp
	< : &lt;
	> : &gt;
	& : &amp;
	' : &#039;
	" : &#034;
    ```

3. default : value속성에 값을 지정하지 않았을 경우 default에 지정한 값이 출력

c:out태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| value | 사용가능 | Object | 출력할 값 |
| escapeXml | 사용가능 | boolean | 특수 문자를 변환할지의 여부 |
| default | 사용가능 | Object | value의 결과값이 null인 경우 출력할 값 |

### <c:catch> tag

**<c:catch var="exName" />의 형태로 exception이 발생하면 해당 익셉션 객체를 exName에 저장하는 태그**

그 이후 exName객체가 있을 경우에는 익셉션 처리를 할 수가 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<c:catch var="exName">

익셉션이 발생할 수 있는 코드
    
</c:catch>

${exName} 사용
</div>
```jsp
<h3>c:catch</h3>
<c:catch var="e">
    name 파라미터의 값 = <%= request.getParameter("name") %> <br>
    <%
        if(request.getParameter("name").equals("test")){
    %>
            ${param.name}은 test입니다 <br>
    <%		
        }
    %>
</c:catch>
<c:if test="${e!=null}">
    익셉션이 발생했습니다<br>
    ${e}
</c:if>
```

![](https://gekdev.github.io/docs/jsp/catch.jpg)

---

## Internationalization Tag

## Internationalization Tag Basic

**국제화 태그는 특정 지역에 따라 알맞은 메시지를 출력해야 할 때 사용**

예를들어 한글 브라우저로 접속을 하면 한글 메시지로 출력하고 영문 브라우저로 접속을 하면 영문 메시지로 출력해야 할 경우 국제와 태그를 사용

웹 브라우저는 Accept-Language 헤더를 사용해서 수용 가능한 언어 목록을 전송하는데 국제화 테그들은 이 헤더의 값을 사용해서 언어별로 알맞은 처리를 하게 됨

예를들어 메시지를 출력해주는 message태그는 Accept-language의 값이 'ko'인 경우 한글 메시지를 우선적으로 처리하고 'en'일 경우에는 영문메시지를 우선으로 처리

국제화 태그 라이브러리
{: .label .label-red .mt-2}

| 기능 		   | 태그 	 		| 설명 										  |
|:---------------|:-----------------|:----------------------------------------------|
| 로케일		  | setLocale 		 | Locale을 지정								  |
|       		 | requestEnCoding  | Locale을 지정								 |
| 메시지		  | bundle 			 | 사용할 번들을 지정 							 |
|            	 | message  		| 지역에 알맞은 메시지를 출력					|
|            	 | setBundle  		| 리소스번들을 로딩후 특정 변수에 저장			|
| 포매팅		  | formatNumber 	 | 숫자 형식을 지정							  |
|        		 | formatDate 		| 날짜 형식을 지정								 |
| 			 	 | parseDate 		| 문자열로 표시된 날짜를 Date객체로 파싱 		 |
| 			 	 | parseNumber  	| 문자열로 구성된 자를 숫자로 파싱 			  |
| 				 | setTimeZone 		| 시간대 정보를 특정 변수에 저장				   |
| 				 | timeZone 		| 시간대를 저장								  |

### <fmt:setLocale>

**국제화 태그를 사용할 로케일을 지정**

Accept-Language 헤더에서 지정한 언어가 아닌 다른 언어를 사용하도록 지정할 때 사용하는 테그

일반적으로 웹 브라우저가 전송한 Accept-Language 헤더값에 맞게 메시지를 출력하기 때문에 사용하는경우는 드뭄

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>

<fmt:setLocale value="ko" scope="request" />
</div>

* value : locale을 "언어코드_국가코드" 형식으로 지정
    
    두 글자 언어코드는 반드시 지정해야 하며, 두글자로 된 국가 코드를 추가로 지정할 수 있음
    
    언어코드와 국가코드는 하이픈이나 밑줄로 구문해야 함 (ko_kr)
    
    null이면 기본로케일을 사용함 (JVM의 기본 로케일 또는 web.xml파일에서 설정한 로케일을 기본 로케일로 사용함)

* scope : 지정한 Locale이 영향을 미치는 범위를 지정, 기본값 page

### <fmt:requestEncoding>

**요청파라미터의 문자셋 인코딩을 지정**

요청 파라미터의 인코딩을 utf-8로 하고싶다면 다음과 같이 하면됨

예제
{: .label .label-purple .mt-2}
```jsp
<fmt:requestEncoding value="utf-8" />

<% request.setCharacterEncoding("utf-8"); %> //위 코드는 아래 코드와 동일함
```

### Resource Bundle

메시지 번들 파일은 클래스 패스에 위치해야 하기 때문에 WEB-INF\classes폴더나 WEB-INF\lib에 포함된 jar파일에 포함해야 함

리소스 번들파일은 기본적으로 java.util.Properties 클래스를 사용해서 읽어오기 때문에 확장자가 .properties임

리소스번들파일에서 중요한 점은 리소스번들파일의 이름을 정해진 규칙에 의거 작성해야 함

예를들어 "번들이름_국가.properties"의 형식으로 작성해야 하고 국가코드는 생략할 수 있음

1. 영문 메시지를 보여줄 때 사용할 리소스 번들 파일

    message.properties
    {: .label .label-purple .mt-2}
    ```properties
    TITLE=Learning JSP/Servlet
    GRETTING=Hello JSP/Servlet?
    USER=Your Id is {0} ! 
    ```

2. 한글 메시지를 보여줄 때 사용할 리소스 번들 파일

    message.properties.src
    {: .label .label-purple .mt-2}
    ```properties
    TTILE=최범균의 JSP배우기
    GREETING=안녕하세요 최범균입니다
    VISITOR= 당신의 아이디는{0}입니다
    ```

    리소스 번들 파일은 직접 작성하지 못함, 유니코드로 변경한 형태로 변환한 파일을 사용할 수 있음
    
    JDK가 제공하는 native2ascii.exe를 사용해야 함
    
    위 파일 생성 후 명령프롬프트 경로잡기 아래명령어 치기
    
    ```java
    C:\> e:
    E:\> cd lec\05.jsp\jsp01_basic\WebContent\WEB-INF\classes\resource
    E:\...> native2ascii message_ko.properties.src message_ko.properties
    ```
    
    **마지막 명령어를 사용하면 한국어가 유니코드로 변경된 properties파일이 생성됨**

### <fmt:bundle>

**태그몸체에서 사용할 리소스 메세지 번들을 지정, message태그와 함께 사용함**

fmt:bundle태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| basename | 사용가능 | String | 사용할 리소스 번들의 이름 |
| prefix | 사용가능 | String | bundle 태그의 내부에서 사용되는 message태그의 key 속성의 값 앞에 자동으로 붙게 될 문자열 |

예제
{: .label .label-purple .mt-2}
```jsp
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>

<fmt:bundle basename="resource.message">
	<fmt:message key="TITLE" var="title"></fmt:message>
</fmt:bundle>

<h3>${title}</h3>
```

![](bundle.jpg)

### <fmt:message> 

**지정한 리소스 번들로부터 메시지를 읽어와 출력 메시지를 출력**

fmt:bundle태그의 속성 설명요약
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
* key : 읽어올 메세지의 키값

* var : 메시지를 저장할 변수 명, 속성을 지정하면 메시지를 출력하지 않고 var속성으로 지정한 변수에 저장함

* scope : 변수가 저장되는 영역 지정

* bundle : <fmt:setBundle> 태그를 사용해서 로딩한 번들로부터 메시지를 읽어올 때 사용
</div>

리소스 번들이 제공하는 메시지 중에는 [위와같이]() {0}, {1}, {2}와 같이 변경 가능한 요소를 제공하는 메시지가 존재할 때

그 값을 지정하려면 fmt:messate 태그에 fmt:param 태그를 사용해야함

1개 존재할 때
{: .label .label-purple .mt-2}
```jsp
<fmt:message key="VISITOR">
    <fmt:param value="${id}" />
</fmt:message>
```

여러개 존재할 때
{: .label .label-purple .mt-2}
```jsp
<fmt:message key="VISITOR">
    <fmt:param value="${id}" />      // 0에 들어감
    <fmt:param value="${name}" />    // 1에 들어감
    <fmt:param value="${email}" />   // 2에 들어감
</fmt:message>
```

#### 리소스 번들 검색 순서

다음과 같은 순서로 리소스 번들을 검색함

1. bungle 속성에 지정한 리소스 번들을 사용

2. <fmt:bundle> 태그에 중첩된 경우 <fmt:bundle> 태그에서 설정한 리소스 번들 사용

3. 1이나 2가 아닐 경우 기본 리소스 번들 사용

    기본 리소스 번들은 web.xml파일에서 javax.servlet.jsp.jstl.fmt.localizationContext 속성을 통해서 설정

### <fmt:setBundle>

<fmt:setBundle> : **특정메시지를 사용할 수 있도록 지정**

bundle은 태그 안에서 사용될 리소스 번들을 지정하는 반면 setBundle은 리소스 번들을 변수로 저장한 후 어디서나 사용할 수 있게 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<fmt:setBundle var="message" basename="resource.message" />

...

<fmt:message bundle="${message}" key="GREETING" />
</div>

fmt:setBundle태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| basename | 사용가능 | String | 읽어올 리소스 번들의 이름 |
| var | 사용불가 | String | 리소스 번들을 저장할 변수 명 |
| scope | 사용불가 | String | 변수를 저장할 영역 |

### <fmt:formatNumber>

**숫자를 양식에 맞춰 출력**

syntax
{: .label .mt-2}
```jsp
<fmt:formatNumber value="숫자값" [type="값타입"] [pattern="패턴"]
        [currentCode="통화코드"] [currencySymbol="통화심볼"]
        [groupingUsed="(true/false)"] [var="변수명"] [scope="영역"] />
```

fmt:formatNumber태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| value | 사용가능 | String / Number | 양식에 맞춰 출력할 숫자를 지정 |
| type | 사용가능 | String | 어떤 양식으로 출력할지 정함. number → 숫자(기본값), percent → %, currency → 통화 |
| pattern | 사용가능 | String | 직접 숫자가 출력되는 양식을 지정 |
| currencyCode | 사용가능 | String | 통화 코드를 지정 | 
| currentSymbol | 사용가능 | String | 통화를 표현할 때 사용할 기호를 표시 |
| groupingUsed | 사용가능 | Boolean | 콤마와 같이 단위를 구분할 때 사용되는 기호를 사용할 지의 여부를 결정.
| var | 사용불가 | String | 포멧팅한 결과를 저장할 변수명을 지정 |
| scope | 사용불가 | String | 변수를 저장할 영역 지정, 기본값 page | 

### <fmt:parseNumber>

**문자열을 숫자 타입으로 변환해주는 기능**

syntax
{: .label .mt-2}
```jsp
<fmt:parseNumber value="값" [type="값타입"] [pattern="패턴"]
        [parseLocale="통화코드"] [integerOnly="true/false"]
        [var="변수명"] [scope="영역"] />
```

fmt:parseNumber태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| value | 사용가능 | String | 파싱할 문자열을 지정 |
| type | 사용가능 | String | value 속성의 문자열 타입을 지정 number → 숫자(기본값), percent → %, currency → 통화 |
| pattern | 사용가능 | String | 직접 파싱할 때 사용할 양식을 지정 |
| parseLocale | 사용가능 | String | 파싱할 때 사용할 로케일을 지정 |
| integerOnly | 사용가능 | String | 정수 부분만 파싱할 지의 여부를 지정. 기본값 false |
| var | 사용불가 | String | 포멧팅한 결과를 저장할 변수명을 지정 |
| scope | 사용불가 | String | 변수를 저장할 영역 지정, 기본값 page | 

예제
{: .label .label-purple .mt-2}
```jsp
<fmt:parseNumber value="1,100.12" pattern="0,000,00" var="num" />

${sum}
```

### <fmt:formatDate>

**날짜 정보를 담고 있는 객체를 포메팅하여 출력할 때 사용**

syntax
{: .label .mt-2}
```jsp
<fmt:formatDate value="날짜값" [type="타입"] [dateStyle="날짜스타일"] 
        [timeStyle="시간스타일"] [pattern="패턴"] [timeZone="타임존"]
        [var="변수명"] [scope="영역"] />
```

fmt:parseNumber태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| value | 사용가능 | java.util.Date | 포메팅할 시간 값을 지정 |
| type | 사용가능 | String | 날찌, 시간 또는 둘 다 포맷팅할 지 여부를 지정. time, date(기본값), both중 한 가지 값을 가질 수 있음 |
| dateStyle | 사용가능 | String | 날짜에 대해 미리 정의된 포멧팅 스타일을 지정 |
| timeStyle | 사용가능 | 시간에 대해 미리 정의된 포멧팅 스타일을 사용 |
| pattern | 사용가능 | 직접 파싱할 때 사용할 양식을 지정 |
| timeZone | 사용불가 | 시간대를 변경하고 싶을 때 사용 |
| var | 사용불가 | 파싱한 결과를 저장할 변수명을 지정 |
| scope | 사용불가 | 변수를 저장할 영역을 지정, 기본값은 page |

### <fmt:parseDate>

**문자열로 표시된 날짜와 시간 값을 java.util.Date로 파싱해주는 기능**

syntax
{: .label .mt-2}
```jsp
<fmt:parseDate value="날짜값" [type="타입"] [dateStyle="날짜스타일"] 
        [timeStyle="시간스타일"] [pattern="패턴"] [timeZone="타임존"] [parseLocale="로케일"]
        [var="변수명"] [scope="영역"] />
```

fmt:parseDate태그의 속성 설명요약
{: .label .label-red .mt-2}

| 속성 | 표현식/EL | 타입 | 설명 |
|:-----|:----------|:-----|:-----|
| value | 사용가능 | java.util.Date | 포메팅할 시간 값을 지정 |
| type | 사용가능 | String | 날자, 시간 또는 둘 다 포맷팅할 지 여부를 지정. time, date(기본값), both중 한 가지 값을 가질 수 있음 |
| dateStyle | 사용가능 | String | 날짜에 대해 미리 정의된 포멧팅 스타일을 지정 |
| timeStyle | 사용가능 | 시간에 대해 미리 정의된 포멧팅 스타일을 사용 |
| pattern | 사용가능 | 직접 파싱할 때 사용할 양식을 지정 |
| timeZone | 사용불가 | 시간대를 변경하고 싶을 때 사용 |
| parseLocale | 사용가능 | String 또는 java.util.Locale | 파싱할 때 사용할 로케일을 지정 |
| var | 사용불가 | 파싱한 결과를 저장할 변수명을 지정 |
| scope | 사용불가 | 변수를 저장할 영역을 지정, 기본값은 page |

### <fmt:setTimeZone> / <fmt:timeZone>

**포메팅 태그도 시간대별로 시간을 처리할 수 있는 기능을 제공**

--- 

## Function



---

## Custom Tag

### What is Custom Tag?

프로그램을 개발하다보면 JSP액션태그나 JSTL태그만으로 부족할 때가 있는데 이를 지원하기 위해서

**사용자가 원하는 목적에 맞게 새로운 태그를 만들어서 사용할 수 있도록 하는 태그**

### Advantage of Custom Tag

1. 재사용: 한번 작성한 커스텀 태그는 어떤 JSP 컨테이너에서도 사용이 가능함

2. 쉽고 단순한 JSP 코드를 작성 : 자바코드에 익숙하지 않은 개발자들도 커스텀 태그를 사용하면 보다 쉽게 JSP 페이지를 작성가능

3. 코드의 가독성 향상 : 커스텀 태그를 사용하면 스크립트 코드를 줄일 수 있기 때문에 JSP의 가독성을 높일 수 있음

### 

태그 파일에서 사용가능한 디렉티브

| 디렉티브 | 설명 |
|:---------|:-----|
| tag | JSP 페이지의 page디렉티브와 동일, 태그 파일의 정보를 명시 |
| taglib | 태그파일에서 사용할 태그라이브러리를 정의 |
| include | 태그파일에 특정 파일을 포함시킬 때 사용 |
| attribute | 태그파일을 커스텀태그로 사용할 때 입력받을 속성을 명시 |
| variable | EL 변수로 사용할 변수에 대한 정보를 정의 |


### 태그디렉티브의 속성

| 속성 | 설명 |
|:-----|:-----|
| display-name | 태그파일을 사용될 이름을 지정. 기본값은 확장자 ".tag"를 제외한 나머지 파일이름  |
| body-content | body 내용의 종류를 정의 empty, tagdependent, scriptless의 세가지값 중 하나를 사용할 수 있음 | 
| dynamic-attributes | 동적속성을 정의 속성<key, value>를 저장하는 Map객체를 page범위의 속성에 저장할 때 사용할 이름을 정의 |
| description | 태그에 대한 설명 |
| import | page 디렉티브의 import 속성과 동일 |
| pageEncoding | page 디렉티브의 pageEncoding 속성과 동일 
| defferedSyntaxAllowedAsLiteral | page 디렉티브의 defferedSyntaxAllowedAsLiteral 속성과 동일, 이 값이 true일 경우 ${expr} or #{expr}형식의 값은 문자열로 처리하는 옵션 |
| trimDirectiveWhitespaces | page 디렉티브의 trimDirectiveWhitespaces 속성과 동일 |


### 태그파일에서 사용가능한 기본 객체

* jspContext : pageContext가 제공하는 setAttribute(), getAttribute() 메서드를 그대로 제공하며 각 속성과 관련된 작업을 처리

* request : JSP 페이지의 request 기본객체와 동일함

* response : JSP 페이지의 response 기본 객체와 동일

* session : JSP 페이지의 session 기본 객체와 동일

* application : JSP 페이지의 application 기본 객체와 동일

* out : JSP 페이지 out 기본객체와 동일

### 태그파일의 위치

WEB-INF/tags 폴더나 그 하위폴더에 위치. 이폴더에 위치한 파일중에서 ~.tag, ~tagx확장자 파일만 태그파일로 인식함
