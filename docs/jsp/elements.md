---
layout: default
title: Elements
parent: JSP
nav_order: 16
has_children: true
---

# JSP Elements
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Filter

### What is Filter?

**JSP/Servlet에서 요청이 들어오면 요청 이전에 이 요청이 올바른지 또는 특정 장원에 접근권한의 여부를 사전에 처리 할 수 있음**

또한 응답하는 데이터를 변경하거나 취소할 수 있음

&#8594; 즉, HTTP의 request와 response를 변경할 수 있는 클래스임

필터는 객체의 형태로 클라이언트에서 오는 요청과 웹 서버(JSP, 서블릿) 사이에 존재하여 클라이언트의 요청을 제어할 수 있도록 함

또한 웹 서버와 응답 사이에 위치해 응답을 제어할 수 있게 함

필터는 요청, 응답정보를 변경할 수 있을 뿐 아니라 흐름도 제어할 수 있음. 즉, 필터는 웹 브라우저의 요청을 필터로 체인해 다음 단계로 보내 다른 결과를 웹 브라우저에 전송할 수도 있음

---

## 필터의 구현

필터를 구현하기 위해서는 3개의 핵심 클래스가 필요함

1. javax.servlet.Filter 인터페이스 : 웹브라우저와 최종자원사이에 위치하는 필터를 구현하는 객체가 상속하는 인터페이스

2. javax.servlet.ServletRequestWrapper : 필터가 요청한 결과를 저장하는 클래스

3. javax.servlet.ServletResponseWrapper : 필터가 응답한 결과를 사용하는 클래스

### Filter 인터페이스 메서드

init() : 필터를 초기화할 때 호출

doFilter() : 필터 기능을 수행, chain()메서드를 이용해서 다음 필터로 이동

destory() : 필터가 웹컨테이너에서 삭제될 때 호출

### Filter 구현절차

1. init()을 호출해서 초기화 작업을 수행

2. doFilter()

    1) request파라미터를 이용해서 요청의 필터작업을 수행

    2) chain.doFilter(req, res)를 이용해 체인의 다음 필터를 수행

    3) response를 이용해서 응답의 필터링 작업을 수행

3. destory() : 필터가 사용하는 자원들을 반납
