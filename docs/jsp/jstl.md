---
layout: default
title: Custom Tag & JSTL
parent: JSP
nav_order: 9
---

# JSP Custom Tag & JSTL
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Custom Tag & JSTL

### What is Custom Tag & JSTL?

**표준라이브러리**

커스텀 태그 : JSP를 확장시켜주는 기능, 액션태그와 마찬가지로 태그 형태로 기능을 제공

액션태그와의 차이점은 커스텀 태그는 개발자가 직접 개발해주어야 함

사용목적 : JSP코드에서 중복되는 것을 모듈화하거나 스크립트 코드를 사용할 때 발생하는 소스 코드의 복잡함을 없애기 위해 사용

**JSTL(JavaServer Pages Standard Tag Library) : 커스텀 태그 중 자주 사용하는 것들을 별도로 표준화한 태그 라이브러리**

### Features of JSTL

* if-else조건문 그리고 for 구문과 같은 반복 처리를 커스텀 태그를 이용해서 구현할 수 있도록 함

* 스크립트 코드보다 이해하기 쉽기 때문에 자바 언어에 익숙하지 않더라도 JSTL을 이용해서 어느 정도 논리적인 처리를 수행할 수 있음


JSTL (JSP Standard Tag Library)

### Why Use JSTL?

JSP는 스크립트릿과 표현식등의 스크립트 코드와 HTML등의 코드가 뒤섞여서 사용하기 때문에

JSP코드는 가독성이 떨어지고 코딩하기가 매우 복잡하게 되어있어서 개발이 편리하지 않게 되었음

그래서 JSP를 새로운 태그를 포함한 표준 라이브러리 형태로 제공하여 보다 쉽게, 가독성이 좋게 코딩할 수 있도록 제공하는데

**JSP페이지에서 많이 사용되는 논리적인 판단, 반복처리, 포맷처리 등을 쉽게 할 수 있도록 표준으로 만들어서 라이브러리형태로 제공하는 것이 JSTL**

### JSTL이 제공하는 Tag의 종류

| 라이브러리 | 주요기능 						| 접두어    | 관련 URI 								|	 
|:-----------|:---------------------------------|:----------|:--------------------------------------|
| core 		 | 변수지원, 흐름제어, URL처리 	    | c 		| http://java.sun.com/jsp/jstl/core 	|
| XML  		 | XML코어, 흐름제어, XML 변환처리  | x 		| http://java.sun.com/jsp/jstl/xml 		|
| 국제화	 | 지역, 메시지형식, 숫자/날짜 형식 | fmt 		| http://java.sun.com/jsp/jstl/fmt 		|
| DB   		 | SQL, 메시지 형식 				| sql 		| http://java.sun.com/jsp/jstl/sql 		|
| 함수 		 | 컬렉션처리, Strin 처리 			| fn  		| http://java.sun.com/jsp/jstl/functions|

### core 태그

| 기능 			 | 태그 	 | 설명 										|
|:---------------|:----------|:---------------------------------------------|
| 변수지원		 | set 		 | JSP에서 사용할 변수를 선언 					|
|				 | remove 	 | 설정변수를 삭제 								|
| 흐름제어 		 | if  		 | 조건에 따라 흐름을 제어						|
|				 | choose 	 | 다중조건을 처리								|
|				 | forEach 	 | 컬렉션이나 Map의 각 항목을 처리할 때 사용	|
|				 | forTokens | 구분자로 분리된 토큰을 처리 					|
| URL처리 		 | import	 | URL에 해당되는 자원을 삽입					|
| 				 | redirect  | 지정된 경로로 리다이렉트 실행 				|
| 				 | url 		 | URL을 재작성 								|
| 기타태그 		 | catch 	 | 익셉션처리									|
| 				 | out 		 | JspWriter에 내용을 출력 						|

### 국제화 태그

국제화 태그는 특정 지역에 따라 알맞은 메시지를 출력해야 할 때 사용

예를들어 한글 브라우저로 접속을 하면 한글 메시지로 출력하고 영문 브라우저로 접속을 하면 영문 메시지로 출력해야 할 경우 국제와 태그를 사용
  
| 기능 			 | 태그 	 		| 설명 											|
|:---------------|:-----------------|:----------------------------------------------|
| 로케일		 | setLocale 		| Locale을 지정									|
|       		 | requestEnCoding  | Locale을 지정									|
| 메시지		 | bundle 			| 사용할 번들을 지정 							|
|            	 | message  		| 지역에 알맞은 메시지를 출력					|
|            	 | setBundle  		| 리소스번들을 로딩후 특정 변수에 저장			|
| 포매팅		 | formatNumber 	| 숫자 형식을 지정								|
|        		 | formatDate 		| 날짜 형식을 지정								|
| 			 	 | parseDate 		| 문자열로 표시된 날짜를 Date객체로 파싱 		|
| 			 	 | parseNumber  	| 문자열로 구성된 자를 숫자로 파싱 				|
| 				 | setTimeZone 		| 시간대 정보를 특정 변수에 저장				|
| 				 | timeZone 		| 시간대를 저장									|

### 로케일 지정태그

* <fmt:setLocale> : 국제화 태그를 사용할 로케일을 지정

* <fmt:requestEncoding> : 요청파라미터의 문자셋 인코딩을 지정

웹 브라우저는 Accept-language헤더를 사용해서 수용가능한 언어 목록을 저장하는데 

JSTL국제화 태그들은 이 헤더값을 사용해서 언어별로 알맞은 처리를 하게 됨

예를들어 메시지를 출력해주는 message태그는 Accept-language의 값이 'ko'인 경우 한글 메시지를 우선적으로 처리하고 'en'일 경우에는 영문메시지를 우선으로 처리

국제화 태그가 Accept-language 헤더에서 지정한 언어가 아닌 다른 언어를 사용하도록 지정할 때 사용하는 태그가 <fmt:setLocale>임

### 리소스 번들

메시지 태그에서 사용할 리소스 번들 파일을 작성할 때 메시지 번들 파일은 클래스 패스에 위치해야 하기 때문에 

WEB-INF\classes폴더나 WEB-INF\lib에 포함된 jar파일에 포함시켜야 함

리소스 번들파일은 기본적으로 java.util.Properties 클래스를 사용해서 읽어오기 때문에 확장자가 .properties임

리소스번들파일에서 중요한 점은 리소스번들파일의 이름을 정해진 규칙에 의거 작성해야 함

예를들어 "번들이름_국가.properties"의 형식으로 작성해야 하고 국가코드는 생략할 수 있다

### 메시지 처리 태그

<fmt:bundle> : 태그몸체에서 사용할 리소스번들을 지정 

<fmt:message> : 메시지를 출력

<fmt:setBundle> : 특정메시지를 사용할 수 있도록 지정

### 숫자, 날짜 포메팅 태그

1. 숫자 출력과 파싱 : <fmt:formatNumber>, <fmt:parseNumber>

2. 날짜 출력과 파싱 : <fmt:formatDate>, <fmt:parseDate>

3. 시간대 설정 : <fmt:setTimeZone>, <fmt:timeZone>
