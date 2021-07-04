---
layout: default
title: Action Tag
parent: JSP
nav_order: 8
has_children: true
---

# JSP Action Tag
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Action Tag

### What is Action Tag?

**서버나 클라이언트에게 어떤 행동을 하도록 명령하는 태그**

&#9656; JSP 페이지에서 페이지와 페이지 사이 제어

&#9656; 다른 페이지의 실행 결과 내용을 현재 페이지에 포함

&#9656; 자바 빈즈(JavaBeans)등의 다양한 기능 제공

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
XML 형식 <jsp: .../> 사용
</div>

### Action Tags

**액션 태그의 종류**

| 액션 태그 | 형식              | 설명           |
|:----------|:------------------|:---------------|
| forward   | <jsp:foward ... /> | 다른 페이지로의 이동과 같은 페이지 흐름을 제어 |
| include   | <jsp:include ... /> | 외부 페이지의 내용을 포함하거나 페이지를 모듈화 |
| useBean   | <jsp:useBean ... /> | JSP 페이지에 자바빈즈를 설정 |
| setProperty | <jsp:setProperty ... /> | 자바빈즈의 프로퍼티 값을 설정 |
| getProperty | <jsp:getProperty ... /> | 자바빈즈의 프로퍼티 값을 얻어옴 |
| param     | <jsp:param ... /> | <jsp:foward ... />, <jsp:include ... />, <jsp:plugin ... /> 태그에 인자를 추가 |
| plugin    | <jsp:plugin ... /> | 웹 브라우저에 자바 애플릿을 실행, 자바 플러그인에 대한 OBJECT 또는 EMBED 태그를 만드는 브라우저별 코드를 생성 |
| element   | <jsp:element ... /> | 동적 XML 요소를 설정 |
| attribute | <jsp:attribute ... /> | 동적으로 정의된 XML 요소의 속성을 설정 |
| body      | <jsp:body ... /> | 동적으로 정의된 XML 요소의 몸체를 설정 |
| text      | <jsp:text ... /> | JSP 페이지 및 문서에서 템플릿 텍스트를 작성 |

---

## forward 액션 태그의 기능과 사용법

### forward 액션 태그

**현재 JSP 페이지에서 다른 페이지로 이동하는 태그**

&#9656; JSP 컨테이너는 현재 JSP 페이지에서 forward 액션 태그를 만나면 그 전까지 출력 버퍼에 저장되어 있던 내용을 모두 삭제하고 forward 액션 태그에 설정된 페이지로 프로그램의 제어가 이동

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<jsp:forward page="파일명"/>

<jsp:forward page="파일명"></jsp:forward>
</div>

* page 속성 값

    &#9656; 현재 JSP 페이지에서 이동할 페이지의 외부 파일명

    &#9656; 외부 파일은 현재 JSP페이지와 같은 디렉터리에 있으면 파일명만 설정하고, 그렇지 않으면 전체 URL(또는 상대 경로)을 설정해야 함

### forward 액션 태그의 페이지 흐름 처리 과정

![](https://gekdev.github.io/docs/jsp/example/for.png)

---

## include 액션 태그의 기능과 사용법

### include 액션 태그

**include 디렉티브 태그처럼 혀재 JSP 페이지의 특정 영역에 외부 파일의 내용을 포함하는 태그**

&#9656; 현재 JSP페이지에 포함할 수 있는 외부 파일은 HTML, JSP, 서블릿 페이지 등

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<jsp:include page="파일명" flush="false"/>
</div>

* page 속성 값

    &#9656; 현재 JSP 페이지에서 이동할 페이지의 외부 파일명

    &#9656; 외부 파일은 현재 JSP페이지와 같은 디렉터리에 있으면 파일명만 설정하고, 그렇지 않으면 전체 URL(또는 상대 경로)을 설정해야 함
    
* flush 속성 값

    &#9656; 설정한 외부 파일로 제어가 이동할 때 현재 JSP 페이지가 지금까지 출력 버퍼에 저장한 결과를 처리, 기본 값은 false

    &#9656; true로 설정하면 외부 파일로 제어가 이동할 때 현재 JSP 페이지가 지금까지 출력 버퍼에 저장된 내용을 웹 브라우저에 출력하고 버퍼를 비움

### include 액션 태그의 처리 과정

![](https://gekdev.github.io/docs/jsp/example/inc.png)

include 액션태그와 디렉티브 태그의 차이점
{: .label .label-yellow .mt-2}

| 구분 | include 액션태그 | include 디렉티브 태그 |
|:-----|:-----------------|:----------------------|
| 처리시간 | 요청시 자원을 포함 | 번역시 자원을 포함 | 
| 기능 | 별도의 파일로 요청 처리 흐름을 이동 | 현재 페이지에 삽입 |
| 데이터 전달방법 | request 기본 내장 객체나 param 액션태그를 이용해 파라미터를 전달 | 페이지 내의 변수를 선언한 후 변수에 값을 저장 |
| 용도 | 화면 레이아웃의 일부분을 모듈화할 때 주로 사용 | 다수의 JSP 웹페이지에서 공통으로 사용되는 코드나 저작권 같은 문장을 포함하는 경우 사용 | 
| 기타 | 동적페이지에 사용 | 정적페이지에 사용 |

---

## param 액션 태그의 기능과 사용법

### param 액션 태그

**현재 JSP 페이지에서 다른 페이지에 정보를 전달하는 태그**

&#9656; 이 태그는 단독으로 사용되지 못하며 <jsp:forward>나 <jsp:include>태그의 내부에 사용

&#9656; 다른 페이지에 여러 개의 정보를 전송해야할 때는 다중의 param 액션 태그 사용

syntax
{: .label .mt-2}
```jsp
<jsp:forward page="파일명">
    <jsp:param name="매개변수명1" value="매개변수값1" />
    [<jsp:param name="매개변수명2" value="매개변수값2" /> ... ]
</jsp:forward>
```

---

## 자바빈즈 액션 태그의 기능과 사용법

### 자바 빈즈

**동적 콘텐츠 개발을 하기 위해 자바 코드를 사용하여 자바 클래스로 로직을 작성하는 방법**

**JSP 페이지에서 화면을 표현하기 위한 계산식이나 자료의 처리를 담당하는 자바코드를 따로 분리하여 작성하는 것**

&#9656; JSP 페이지가 HTML과 같이 쉽고 간단한 코드만으로 구성

![](https://gekdev.github.io/docs/jsp/example/beans.png)

### 자바반즈를 작성할 때 규칙

1. 자바 클래스는 java.io.Serializable 인터페이스를 구현해야 함

2. 인수가 없는 기본 생성자가 있어야 함

3. 모든 멤버 변수인 프로퍼티는 private 접근 지정자로 설정해야 함

4. 모든 멤버 변수인 프로퍼티는 getter/setter() 메소드가 존재해야 함

    getter() 메소드는 멤버 변수에 저장된 값을 가져올 수 있는 메소드이고,
    
    setter() 메소드는 멤버 변수에 값을 저장할 수 있는 메소드임

자바빈즈 예제
{: .label .label-purple .mt-2}
```java

```

### useBean 액션 태그

**JSP 페이지에서 자바빈즈를 사용하기 위해 실제 자바 클래스를 선언하고 초기화하는 태그**

&#9656; id 속성과 scope 속성을 바탕으로 자바빈즈의 객체를 검색하고, 객체가 발견되지 않으면 빈 객체를 생성

syntax
{: .label .mt-2}
```jsp
<jsp:useBean id="자바빈즈 식별이름" class="자바빈즈 이름" scope="범위" />
```

* id : 자바빈즈를 식별하기 위한 이름

* class : 패키지 이름을 포함한 자바빈즈 이름. 자바빈즈는 인수가 없는 기존 생성자가 있어야 하며 추상클래스를 사용할 수 없음

* scope : 자바빈즈가 저장되는 영역을 설정. page, requset, session, application중 하나의 값을 사용

### serProperty 액션 태그

**useBean 액션 태그와 함께 자바빈즈의 setter()메소드에 접근하여 자바빈즈의 멤버 변수인 프로퍼티의 값을 저장하는 태그**

&#9656; 폼 페이지로부터 전달되는 요청 파라미터의 값을 직접 저장하거나 자바빈즈의 프로퍼티로 변경하여 값을 저장할 수 있음

&#9656; 모든 자바빈즈 프로퍼티 이름과 동일하게 요청 파라미터를 설정할 수 있음

syntax
{: .label .mt-2}
```jsp
<jsp:setProperty name="자바빈즈 식별이름" property="프로퍼티 이름" vlaue="값" />
```

* name : useBean 태그에 id속성값으로 설정된 자바빈즈를 식별하기 위한 이름

* property : 자바빈즈의 프로퍼티 이름. 만약 프로퍼티 이름에 *를 사용하면 모든 요청 파라미터가 자바빈즈 프로러티의 setter() 메소드에 전달됨을 의미

* value : 변경할 자바빈즈의 프로퍼티 값. 만약 프로퍼티 값이 null 이거나 존재하지 않는 요청 파라미터인 경우에 setProperty 액션태그가 무시됨

* param : 자바빈즈의 프로퍼티 값을 전달하는 요청파라미터의 이름. prarm과 value를 동시에 모두 사용할 수 없으며 하나를 선택해 사용하는거는 가능

### getProperty 액션 태그

**useBean 액션 태그와 함께 자바빈즈의 getter() 메소드에 접근하여 자바빈즈의 멤버 변수인 프로퍼티의 값을 가져오는 태그**

syntax
{: .label .mt-2}
```jsp
<jsp:getProperty name="자바빈즈 식별이름" property="프로퍼티 이름"/>
```

* name : useBean 태그에 id속성값으로 설정된 자바빈즈를 식별하기 위한 이름

* property : 자바빈즈의 프로퍼티 이름. 만약 프로퍼티 이름에 *를 사용하면 모든 요청 파라미터가 자바빈즈 프로러티의 getter() 메소드에 전달됨을 의미

---

## Representative Site

### Information

* [ansalstmd.log](https://velog.io/@ansalstmd/JSP4.-%EC%95%A1%EC%85%98-%ED%83%9C%EA%B7%B8)
