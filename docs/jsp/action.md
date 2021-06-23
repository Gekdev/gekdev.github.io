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

**서버나 클라이언트에게 어떤 행등을 하도록 명령하는 태그**

JSP 페이지에서 페이지와 페이지 사이 제어

다른 페이지의 실행 결과 내용을 현재 페이지에 포함

자바 빈즈(JavaBeans)등의 다양한 기능 제공

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
XML 형식 <jsp: .../> 사용
</div>
```jsp

```

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


[ansalstmd.log](https://velog.io/@ansalstmd/JSP4.-%EC%95%A1%EC%85%98-%ED%83%9C%EA%B7%B8)
