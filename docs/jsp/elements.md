
JSP페이지의 구성요소

### 디렉티브 (Directive)"C:/git/gekdev.github.io/docs/jsp/elements.md"

**JSP에 대한 설정 정보를 지정할 때 사용**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<%@ 디렉티브이름 속성1="값1" 속성2="값2" ... %>
</div>

JSP가 제공하는 디렉티브
{: .label .label-red .mt-2}

| 디렉티브 | 설명 |
|:---------|:-----|
| page | **JSP 페이지에 대한 정보를 지정**, JSP가 생성하는 문서타입, 버퍼크기, 에러페이지등 JSP에서 필요한 정보를 설정 |
| taglib | JSP에서 사용될 tag라이브러리를 지정 |
| include | JSP페이지 특정영역으로 다른 페이지를 포함 (ex. header, footer)
	
### 스크립트 (Script)

**문서의 내용을 동적으로 생성하기 위해 사용되는 것**

스크립트 요소를 사용하면 사용자가 JSP페이지에 입력한 정보들을 DB에 저장할 수도 있고 DB에서 데이터를 읽어서 출력할 수도 있음

스크립트를 사용하면 자바가 제공하는 다양한 기능들을 사용할 수 있음

JSP를 스크립트 언어라고 불리는데 그 이유가 이러한 스크립트 코드를 제공하기 때문 

스크립트의 요소
{: .label .label-red .mt-2}

| 요소 | 문법 | 설명 |
|:-----|:-----|:-----|
| 표현식(Expression) | <%=%> | 값을 출력함 | 
|  스크립트릿(Scriptlet) | <%%> |  자바코드를 실행 | 
| 선언부(Declaration) | <%!%> | 자바 코드를 실행함 | 


### 기본객체 (Implicit Object)

JSP는 웹애플리케이션 프로그래밍을 하는데 필요한 기능을 제공해주는 기본객체를 제공 (객체들 마다 웹 애플리케이션에서 필요한 고유한 기능을 제공)

대표적인 기본객체
{: .label .label-red .mt-2}

* request : 요청 파라미터 읽어오기, 웹 브라우저가 웹 서버에 요청하는 정보를 전달

* response : 응답 결과 전송하기, 웹서버에 요청된 결과를 응답하는 정보를 제공

* session : 세션 처리하기

* application : 웹어플리케이션 정보 읽어오기

* pager

* out : DOM 출력


### 표현언어 (Expression Language, EL)

### 정적인 데이터

### 표준 액션 태그 (Action Tag)

### 커스텀태그 (Custom Tag)

### 표준라이브러리(JSTL)