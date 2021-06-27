---
layout: default
title: Expression Language
parent: JSP
nav_order: 6
has_children: true
---

# JSP Expression Language
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Expression Language, EL

### What is Expression Language?

**표현언어, 값을 표현하는데 사용하는 스크립트 언어**

&#9656; JSP의 스크립트 요소를 보완하는 역할을 함

&#9656; ${와 }사이에 정해진 문법을 따르는 식을 입력

&#9656; JSP 스크립트 코드를 사용하는 것보다 표현 언어를 사용하는 것이 코드를 간결하고 이해하기 좋게 만들어주기 때문에 특별한 이유가 없는 한 표현 언어를 주로 사용함

&#9656; JSTL(JSP Standard Tag Library) 규약에 나오는 내용으로서 JSP2.0부터 EL이 JSP에 포함됨

### El's Skills

1. JSP의 네가지 기본 객체가 제공하는 영역의 속성

2. 수치 연산자, 관계 연산자, 논리 연산자를 제공

3. 자바 클래스의 메서드 호출가능

4. 쿠키, 기본객체의 속성 등 JSP를 위한 표현언어의 기본 객체를 제공

5. 람다식을 이용한 함수의 정의와 실행(ES3.0)

6. 스트림 API를 통한 컬렉션 처리(EL3.0)

7. 정적 메서드 실행가능(EL3.0)

JSP표현식을 사용하는 것보다 간결한 코드를 사용해서 값을 출력할 수 있음

차이점 
{: .label .label-red .mt-2}
```jsp
표현식
<%= member.getAddress().getZipcode() %>

표현언어
${member.address.zipcode}
```

### EL Components

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
${ 표현식 }

표현식에는 표현언어가 정의한 문법에 따라 값을 표현하는 식이 옴
</div>

&#9656; 액션태그나 JSTL의 속성값으로 사용할 수 있음

```jsp
<jsp:include page="/module/${skin.id}/header.jsp" ... />
```

&#9656; 비스크립트 요소에서도 값을 출력하기 위해 사용가능

```jsp
<b>${sessionScope.member.id}님 환영합니다</b>    
```

&#9656; JSP의 스크립트 요소(스크립트릿, 표현식, 선언부)를 제외한 나머지 부분에서 사용할 수 있음

&#9656; JSP2.1버전 부터는 ${expr}형식과 #{expr}형식의 구문을 지원하고 있는데 차이점은 실제로 EL의 값을 언제 생성하느냐에 차이가 있음

&#8594; ${expr}은 구문을 분석할 때 곧바로 값을 계산하지만 #{expr}은 실제로 값이 사용될 때 계산이 됨

&#9656; 값이 존재하지 않을 경우 아무것도 출력하지 않음

### Datatypes of EL

1. Boolean : true/false

2. 정수 : 0~9 정수 / EL에서 정수타입은 java.lang.Long 타입
    
3. 실수 : 0~9 / EL에서 실수타입은 java.lang.Double 타입

4. 문자열 : 따옴표로 둘러싼 문자열 / 작은 따옴표, 큰 따옴표, \의 문자는 이스케이프 문자로 사용해야 함 

5. null

### EL Implicit Object

**EL에서 사용할 수 있는 기본 객체**

| 기본객체          | 설명                                                                              |
|:------------------|:----------------------------------------------------------------------------------|
| pageContext       | JSP의 page 기본객체와 동일                                                        |
| pageScope         | pageContext객체에 저장된 속성의 Map객체(<속성, 값>)                               |
| requestScope      | request객체에 저장된 속성의 Map객체(<속성, 값>)                                   |
| sessionScope      | session객체에 저장된 속성의 Map객체(<속성, 값>)                                   |
| applicaionScope   | application객체에 저장된 속성의 Map객체(<속성, 값>)                               |
| param             | 요청 파라미터의 <이름, 값>의 Map객체, request.getParameter()와 동일               |
| paramValues       | 요청 파라미터의 <이름, 값배열>의 Map객체, request.getParameterValues()와 동일     |
| header            | 요청 파라미터의 <헤더이름, 값>의 Map객체, request.getHeader()와 동일              |
| headerValues      | 요청 파라미터의 <헤더이름, 값배열>의 Map객체, request.getHeaders()와 동일         |
| cookie            | <쿠키이름, Cookie>의 Map객체, request.getCookies()와 동일                         |
| initParam         | 초기화파라미터<이름,값>의 Map객체, application.getInitParameter()와 동일          |

예제
{: .label .label-purple .mt-2}
```jsp
<%
request.setAttribute("name", "소향");
%>

EL에서 사용하는 표현식 <br>

요청 URI = ${ pageContext.request.requestURI } <br>
request의 name의 값 = ${ requestScope.name }  <br>
code의 파라미터 = ${ param.code } <br>    //url에 ?code=값을 지정하면 나옴
```

![](implicitel.jpg)

### EL Object Access

EL 언어는 객체에 저장된 값에 접근할 때 dot(.) or 대괄호([])를 사용함

<표현>.<표현> or <표현>[표현]형식으로 접근

객체 접근과정
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
1. <표현>을 <값>의 형태로 변환

2. <값>이 null일 경우 null값을 리턴

3. <값1>이 null이 아닐경우 <표현2>의 <값2>를 반환

    1. <값2>가 null이면 null리턴

4. <값1>이 Map, List, 배열일 경우

    1. <값1>이 Map일 경우
    
        1. <값1>.containKey(<값2>)이 false이면 null 리턴
        
        2. 아니면 <값1>.get(<값2>) 리턴
    
    2. <값1>이 List, 배열일 경우

        1. <값2>가 정수값인지 여부를 겁사(정수가 아니면 에러 발생)

        2. <값1>.get(<값2>) or Arrays.get(<값1>, <값2>) 결과를 리턴
        
        3. 익셉션을 발생하면 에러를 발생

5. <값1>이 다른 객체일 경우

    1. <값2>를 문자열로 변환
    
    2. <값1>객체가 <값2>를 이름으로 갖는 읽기 가능한 프로퍼티를 포함하고 있다면 프로퍼티 값을 리턴
    
    3. 그렇지 않을 경우 에러발생
</div>

### EL Object Navigation

page, request, session, application 영역에 저장된 속성에 접근할 때에는 pageScope, requestScope, sessionScope, applicationScope 기본객체를 사용

page영역에 저장되어 있는 NAME 속성 참고하기
{: .label .label-purple .mt-2}
```jsp
${pageScope.NAME}
```

### Operator of EL

1. 수치 연산자 : +, -, *, /, %

    ```jsp
    ${"10" + 1} 결과는 11 (자바는 101)
    ${"일" + 1} 결과는 에러발생 (자바는 일1)
    ${null + 1} 결과는 1 // null이면 0을 리턴함
    ```
    
2. 비교 연산자 : ==, !=, <, <=, >, >=

3. 논리 연산자 : &&, ||, !

4. empty연산자 : empty<값>의 형태로 사용

    null, "", 길이 0인 배열, 빈 Map, 빈 Collection = true

5. 삼항연산자 : 수식 ? 값1 : 값2

6. 문자열 연결 : +=

    ```jsp
    ${"문자" += "열" += "연결"} //"문자열연결"
    
    <% request.setAttribute("title","JSP 프로그래밍"); %>
    ${ "제목: " += title} //제목: JSP 프로그래밍
    ```

7. 세미콜론(;) 연산자 

    ${1+1; 10+10}의 결과는 20만 출력 즉 ${A;B}의 EL결과는 B값만 출력

8. 할당연산자

    할당 연산자 자체도 출력 결과를 생성하기 때문에 세미콜론 연산자와 같이 활용해서 사용함

    ```jsp
    ${var = 10} //10으로 출력
    
    ${hangul = ['가','나','다']; "} //응답결과에 빈 문자열 출력
    ${hangul[0]}  //['가','나','다'] 사용가능
    ```

9. 특수문자 처리하기

    역슬래쉬 뒤에 문자를 위치시키면 됨
    
---

## EL's Method Call

### Thermometer.java

섭씨를 화씨로변경하는 온도계 객체 생성
{: .label .label-purple .mt-2}
```java
package com.lec.el;

import java.util.HashMap;
import java.util.Map;

public class 온도계 {
	
	private Map<String, Double> map = new HashMap<>();
	
	public String getInfo() {
		return "섭씨/화씨온도 변환기";
	}
	
	public void setCelsius(String city, Double val) {
		map.put(city, val);
	}
	
	public Double getCelsius(String city) {
		return map.get(city);
	}
	
	public Double getFahrenheit(String city) {
		Double celsius = getCelsius(city);
		if(celsius==null) return null;
		return celsius.doubleValue() * 1.8 + 32.0;
	}
}
```

생성한 온도계 자바클래스 사용하기 
{: .label .label-purple .mt-2}
```jsp
<%@page import="com.lec.el.온도계"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<% 
	온도계 thermometer = new 온도계(); 
	request.setAttribute("t", thermometer);	
%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>

	<h3>온도변환기(v1.0)</h3>
	${ t.getInfo() } <br/>
	${ t.setCelsius("서울", 28.0) } <br>
	${ t.getCelsius("서울") } <br>
	서울의 온도 (화씨) = ${ t.getFahrenheit("서울") } <br>

</body>
</html>
```

![](ther.jpg)

### Call Static Method 1

정적 메서드를 호출하는 방법 1 : EL의 함수로 지정하는 방법

TLD 파일작성, web.xml파일설정, taglib 디렉티브도 설정, 호출 TLD파일에 설정한 이름을 사용 등...

### Call Static Method 2

정적 메서드를 호출하는 방법 2 : EL 3.0이후 추가됨

static 메서드 생성하기
{: .label .label-purple .mt-2}
```java
package com.lec.el;

import java.text.DecimalFormat;

public class FormatUtil {

	public static String number(long number, String pattern) {
		DecimalFormat ptrn = new DecimalFormat(pattern);
		return ptrn.format(number);
	}
	
}
```

메서드를 호출하기 위한 JSP 코드 작성
{: .label .label-purple .mt-2}
```jsp
<%@page import="com.lec.el.FormatUtil"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<% 
	request.setAttribute("price", 1230l);
%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>

	<h3>정적메서드 호출하기</h3>
	가격은 <b>${ FormatUtil.number(price, '#,##0')}</b> 원입니다

</body>
</html>
```

![](staticmethod.jpg)

---

## Disable EL

EL을 비활성화 시키는 방법

### web.xml

web.xml파일에서 EL을 비활성화 시켜주는 옵션을 추가하기

web.xml파일: EL을 비활성화
{: .label .label-purple .mt-2}
```xml
<jsp-config>
    <jsp-property-group>
        <url-pattern>/oldversion/*</url-pattern>
        <el-ignored>true</el-ignored>
    </jsp-property-group>
</jsp-config>    
```
web.xml파일: #{expr}만 비활성화
{: .label .label-purple .mt-2}
```xml
<jsp-config>
    <jsp-property-group>
        <url-pattern>/oldversion/*</url-pattern>
        <el-ignored>true</el-ignored>
    </jsp-property-group>
</jsp-config>  

<jsp-property-group>
    <url-pattern>/oldversion2_4/*</url-pattern>
    <deffered-syntax-allowed-as-literal>
        true
    </deffered-syntax-allowed-as-literal>
</jsp-property-group>
```

### Specify deactivation options in JSP Page

1. isELIgnored : ture일 경우 EL을 일반 문자열로 처리

2. deff
