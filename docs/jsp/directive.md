---
layout: default
title: Directive
parent: JSP
nav_order: 3
---

# JSP Directive
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Directive

### What is Directive?

**JSP 페이지에 대한 설정 정보를 지정할 때 사용**

&#9656; JSP 페이지가 서블릿 프로그램에서 서블릿 클래스로 변환할 때 JSP 페이지와 관련된 정보를 JSP 컨테이너에 지시하는 메시지

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ 디렉티브태그 속성1="값1" 속성2="값2" ... %>
</div>
```jsp
<%@ page contentType = "text/html; charset=utf-8" %>
```

### Directive Tags

**JSP가 제공하는 디렉티브태그의 종류**

| 디렉티브  | 형식  | 설명  |
|:---------|:-----|:-----|
| page | <%@ page... %> | **JSP 페이지에 대한 정보를 지정**, JSP가 생성하는 문서타입, 버퍼크기, 에러페이지등 JSP에서 필요한 정보를 설정 |
| include | <%@ include... %> | JSP페이지 특정영역으로 다른 페이지를 포함 (ex. header, footer)
| taglib | <%@ taglib... %> | JSP에서 사용될 tag라이브러리를 지정 |

---

## Page Tag

### Page Tag Basic

**JSP 페이지에 대한 정보를 입력하는 태그**

&#9656; JSP 페이지의 어디에서든 선언할 수 있지만 일반적으로 JSP 페이지의 최상단에 선언하는 것을 권장

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ page 속성="값" 속성2="값" %>

&#9656; @와 %사이에 공백이 없어야 함
</div>
```jsp
<%@ page contentType="text/html; charset=utf-8" %>
<%@ page import="java.util.Date" %>
```

### Page Properties

**page 디렉티브의 주요 속성**

주요하게 다뤄야 할 속성들은 아래에서 더 자세하게 기술할 예정!

| 속성 | 설명 | 기본값 |
|:-----|:-----|:-------|
| contentType | JSP가 생성할 문서의 MINE타입과 캐릭터 인코딩을 지정 | text/html |
| import | JSP 페이지에서 사용할 자바 클래스를 지정 | |
| session | JSP페이지가 세션을 사용할지의 여부를 지정. ture : 세션사용 | true |
| buffer | JSP페이지의 출력 버퍼크기를 지정. none : 출력버퍼 사용X / 8kb : 8키로바이트 크기의 출력 버퍼 사용 | 최소 8kb | 
| autoFlush | 출력 버퍼가 다 찼을 경우 자동으로 버퍼에 있는 데이터를 출력 스트림에 보내고 비울지 여부 확인. true : 버퍼의 내용을 웹 브라우저에 보낸 후 비우기 / false : 에러 | true |
| info | JSP 페이지에 대한 설명 | |
| errorPage | JSP 페이지를 실행하는 도중에 에러가 발생할 때 보여줄 페이지를 지정 | | 
| isErrorPage | 현재 페이지가 에러가 발생될때 보여주는 페이지인지의 여부를 지정. true : 에러페이지 | false |
| pageEncoding | JSP 페이지 소스 코드의 캐릭터 인코딩을 지정 | |
| isELIgbored | true : 표현언어를 해석하지 않고 문자열로 처리 / false : 표현 언어를 지원 | false |
| defferedSyntaxAllowedAsLiteral | #{ 문자가 문자열 값으로 사용되는 것을 허용할지의 여부 지정 | false |
| trimDirectiveWhitespaces | 출력 결과에서 템플릿 텍스트의 공백 문자를 제거할지의 여부 지정 | false |

### contentType Property

**JSP 페이지가 생성할 문서의 타입을 지정**

&#9656; contentType은 JSP가 생성할 문서의 MIME 타입을 입력

&#9656; 주로 사용하는 MINE타입은 "text/html"(기본값), 필요에 따라 "text/xml", "application/json"도 사용함 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ page contentType="text/html" %>

<%@ page contentType="text/html; charset=utf-8" %>
</div>

Mine?
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
Multipurpose Internet Mail Extensions의 약자

이메일의 내용을 설명하기 위해 정의되었지만 **HTTP등의 프로토콜에서도 응답 데이터의 내용을 설명하기 위해 사용함**
</div>

#### charset value

&#9656; 속성의 값 중 charset=utf-8은 생략가능, 기본 캐릭터 셋인 ISO-889-1을 사용
 
&#9656; charset은 대소문자 구분하지 않음 (utf-8 / UTF-8 둘다 가능)

&#9656; 문자가 깨진다면 소스코드를 저장할 때 사용한 캐릭터 인코딩과 page디렉티브의 contentType 속성에 지정한 캐릭터 셋이 일치하지 않기 때문

### import Property

자바에서 자바클래스의 full name 대신 단순이름을 사용할 수 있도록 하기 위해 import구문을 사용하는 것처럼

**jsp는 페이지 디렉티브에 import속성을 사용해서 jsp코드에서 클래스이름을 단순하게 사용할 수 있도록 함**

&#9656; import속성에는 여러개의 값을 동시에 지정할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
< %@ page import = "java.util.Date" %>

< %@ page import = "java.util.Date, java.util.Calendar" %> : 여러개 지정

< %@ page import = "java.util.*" %> : 해당 패키지의 모든타입 
</div>
```jsp
< %@ page import = "java.util.Calendar" %>

<% Calendar cal = Calendar.getInstance(); %>
<%= cal.get(Calendar.YEAR) %> 년
<%= cal.get(Calendar.MONTH) + 1 %> 월
<%= cal.get(Calendar.DATE) %> 일
<hr/>

<!-- IMPORT속성을 사용하지 않는 경우는 풀네임으로 지정해야 함 -->
<% java.util.Date now = new java.util.Date(); %>
현재시간은 <%= now %>
```

#### trimDirectiveWhitespaces Property

페이지 디렉티브가 있던 위치 때문에 웹브라우저에서 html 소스를 보면 공백이 있음

**그 공백을 지우기 위해 사용함, false가 기본값**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ page trimDirectiveWhitespaces="true" %>
</div>

#### pageEncoding Property

**JSP 페이지의 인코딩과 pageEncoding 속성**

jsp파일에서 문자셋을 잘못 지정할 경우 응답결과 페이지의 문자들이 깨져서 출력이 됨 

톰캣과 같은 컨테이너는 jsp를 분석하는 과정에서 어떤 인코딩을 이용해서 코드를 작성했는지를 검사 

그 결과를 선택한 캐릭터셋을 이용해서 jsp페이지의 문자를 읽어오게 된다 

웹컨테이너가 jsp페이지를 읽을 때 사용할 문자셋을 결정하는 과정은 아래와 같음

1. 파일이 BOM으로 시작하지 않을경우

	기본 인코딩을 이용해서 파일을 처음부터 읽고 page디렉티브의 pageEncoding속성을 검색
	
	* pageEncoding속성이 값을 가지고 있을 경우, jsp파일을 읽을 때 해당 속성값을 문자셋으로 사용함

	* pageEncoding속성에 값이 없을 경우, contentType의 charset속성값을 사용 

	* 상기 모두 해당되지 않을 경우 iso-8859-1 문자셋을 사용

2. 파일이 BOM으로 시작할 경우

	1. BOM을 이용해서 결정된 인코딩을 이용해서 파일을 읽고 page디렉티브의 pageEncoding속성을 검색
	
	2. 만약 pageEncoding 속성값과 BOM을 이용해서 결정된 인코딩이 다를 경우에 에러 발생

1 or 2번 과정을 통해서 결정된 문자셋으로 jsp소스코드를 읽음

#### Page Directive Tag Properties

![](https://gekdev.github.io/docs/jsp/elements/example/pdtprop.png)

[속성정리](https://velog.io/@ansalstmd/JSP3.-%EB%94%94%EB%A0%89%ED%8B%B0%EB%B8%8C-%ED%83%9C%EA%B7%B8)

---

## Include Tag

**현재 JSP 페이지의 특정 영역에 외부 파일의 내용을 포함하는 태그**

&#9656; 현재 JSP 페이지에 포함할 수 있는 외부 파일

&#9656; HTML, JSP, 텍스트 파일

&#9656; include 디렉티브 태그는 JSP 페이지 어디에서든 선언 가능

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ include file="파일명" %>

&#9656; 파일명 : 현재 JSP 페이지에 포함할 내용을 가진 외부 파일명

&#8594; 이때 외부 파일이 현재 JSP 페이지와 같은 디렉터리에 있으면 파일명만 설정하고, 그렇지 않으면 전체 URL(또는 상대 경로)을 설정
</div>

예시
{: .label .label-purple .mt-2}

![](https://gekdev.github.io/docs/jsp/elements/example/incex.png)

---

## taglib Tag

## taglib Tag Basic

**현재 JSP 페이지에 표현 언어, JSLT, 사용자 정의 태그(custom tag) 등 태그 라이브러리를 설정하는 태그**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ taglib uri="경로" prefix="태그 식별자" %>
</div>

예시
{: .label .label-purple .mt-2}

![](https://gekdev.github.io/docs/jsp/elements/example/taglib.png)
