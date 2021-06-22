---
layout: default
title: Script
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

## Script
{: no_toc}

### What is Script?

**문서의 내용을 동적으로 생성하기 위해 사용되는 것**

&#9656; 스크립트 요소를 사용하면 사용자가 JSP페이지에 입력한 정보들을 DB에 저장할 수도 있고 DB에서 데이터를 읽어서 출력할 수도 있음

&#9656; 스크립트를 사용하면 자바가 제공하는 다양한 기능들을 사용할 수 있음

&#9656; JSP를 스크립트 언어라고 불리는데 그 이유가 이러한 스크립트 코드를 제공하기 때문 

&#9656; JSP 페이지가 서블릿 프로그램에서 서블릿 클래스로 변환할 때, JSP 컨테이너가 자바 코드가 삽입되어 있는 스크립트 태그를 처리하고 나머지는 HTML 코드나 일반 텍스트로 간주

### Script Tags

**스크립트의 요소**

| 스크립트 태그 | 형식  | 설명 |
|:------------|:-----|:-----|
| 선언부(Declaration) | <%! ... %> | 자바 변수나 메소드를 정의하는데 사용 | 
| 스크립트릿(Scriptlet) | <% ... %> |  자바로직 코드를 작성하는데 사용 | 
| 표현식(Expression) | <%= ... %> | 결과를 문자열 형태로 출력하는데 사용 | 

![](https://gekdev.github.io/docs/jsp/elements/example/scriptex.png)

### Eclipse Server

**이클립스에서 서버를 같이 관리해줘서 아래 경로에서도 파일을 확인할 수 있음**

경로 : E:\lec\05.jsp\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\work\Catalina\localhost\basic\org\apache\jsp

![](https://gekdev.github.io/docs/jsp/elements/example/ecex.png)

### Declaration Tag

**변수나 메소드를 선언할 때 사용**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%! ... %>

&#9656; %와 !사이에 공백이 없어야 함
</div>

* 변수 : 전역변수로 사용

    ![](https://gekdev.github.io/docs/jsp/elements/example/loc.png)

* 메소드 : 전역메소드로 사용

    ![](https://gekdev.github.io/docs/jsp/elements/example/loc_m.png)

&#9656; 각 행이 세미콜론으로 끝나야 함

![](https://gekdev.github.io/docs/jsp/elements/example/image.png)

### Scriptlet Tag

**자바 코드로 이루어진 로직 부분을 표현**

&#9656; out 객체를 사용하지 않고도 쉽게 HTML 응답을 만들어냄

&#9656; 각 행이 세미콜론으로 끝나야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<% ... %>
</div>

선언문 태그와 스크립틀릿 태그의 차이점
{: .label .mt-2}

| 선언문태그  | 스크립틀릿 태그 |
|:----------|:--------------|
| 변수뿐만 아니라 메소드를 선언할 수 있음 | 스크립틀릿 태그는 메소드 없이 변수만을 선언할 수 있음 |
| 서블릿 프로그램으로 변환할 때 _jspService() 메소드 외부에 배치됨 | 서블릿 프로그램으로 변환될 때 _jspService() 메소드 내부에 배치됨 |

![](https://gekdev.github.io/docs/jsp/elements/example/scriptvar.png)

### Expression Tag

**웹 브라우저에 출력할 부분을 표현**

&#9656; 표현문 태그에 숫자, 문자, 불린(boolean) 등의 기본 데이터 타입과 자바 객체 타입도 사용 가능

&#9656; 세미콜론으로 종료할 수 없음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%= ... %>

&#9656; %와 =사이에 공백이 없어야 함
</div>

![](https://gekdev.github.io/docs/jsp/elements/example/exptag.png)
