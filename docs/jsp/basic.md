---
layout: default
title: Basic
parent: JSP
nav_order: 2
has_children: true
---

# JSP Basic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Web Programming & JSP

### What is Web Programming?

**웹프로그래밍이란 웹 서버가 웹 브라우저에 응답으로 전송할 데이터를 생성해주는 프로그램을 작성하는 것**

&#9656; 웹 프로그래밍 언어는 클라이언트 측 실행 언어와 서버 측 실행 언어로 구분

&#9656; 웹 서버의 종류에 따라 웹 프로그래밍을 할 때 사용할 기술(언어)이 달라짐 

* 아파치 웹서버 : PHP

* 윈도우 IIS 웹서버 : ASP.net

* 톰켓, 제티, JBoss EAP 웹서버 : JSP

### JavaServer Pages, JSP

**동적 페이지를 작성하는데 사용되는 자바의 표준 기술로 HTML 응답을 생성하는데 필요한 기능을 제공**

&#9656; 자바를 기반으로 하는 JSP는 서버 측 웹 프로그래밍 언어 중 하나

### Why Use JSP?

원래 자바를 기반으로 하는 서버 측 프로그래밍 방식인 서블릿을 먼저 개발했으나, 서블릿 개발 방식이 쉽지 않아 **HTML 코드에 직접 삽입할 수 있도록 개발된 기술이 JSP임**

&#8594; 실제로 웹 애플리케이션 서버에서 클라이언트에게 서비스 될 때는 JSP가 서블릿으로 변경됨

### Features of JSP

1. **서블릿 기술의 확장**

    &#9656; JSP에서는 서블릿의 모든 기능을 사용 가능
    
    &#9656; 서블릿과 마찬가지로 API(JDBC, JNDI, EJB 등을 모두 포함하고 있는 강력한 엔터 프라이즈 자바)를 사용할 수 있음 

    &#9656; 쉽게 개발할 수 있도록 JSP에서는 내장 객체, 미리 정의된 태그, 표현식 언어와 사용자 정의 태그를 사용할 수 있음
    
2. **유지 관리가 용이**

    &#9656; 서블릿 기술에는 프레젠테이션 로직과 비스니스 로직이 섞여있음

    &#9656; JSP 기술의 경우 프레젠테이션 로직과 비즈니스 로직을 분리할 수 있기 때문에 관리가 쉬움

3. **빠른 개발이 가능**

    &#9656; 코드를 수정했을 때 서블릿에서는 업데이트를 하고 다시 컴파일 해야함

    &#9656; JSP의 경우 다시 컴파일하고 프로젝트를 배포할 필요가 없음

4. **코드 길이를 줄일 수 있음**

    &#9656; JSP에서는 액션 태그, JSTL(JavaServer Pages Standard Tag Library), 사용자 정의 태그 등의 다양한 태그와 표현 언어, 내장 객체 등을 사용함으로써 서블릿보다 코드를 줄일 수 있음

### JSP Code Structure

JSP코드는 HTML문서를 생성하는게 주된 목적

&#9656; 설정부분과 응답 생성부분으로 구성됨

* 설정부분 : **JSP페이지에 대한 설정 정보**

    **page디렉티브로 생성함**

    1. JSP 페이지가 생성하는 문서의 타입(종류)
    
    2. JSP 페이지에서 사용할 커스텀 태그
    
    3. JSP 페이지에서 사용할 자바 클래스 지정 등

* 생성부분 : **HTML코드 및 JSP 스크립트**

### JSP Elements 

HTML문서를 생성하기 위해 다양한 요소가 필요함

1. 디렉티브(Directive)

2. 스크립트 : 스크립틀릿(Scriptlet), 표현식(Expression), 선언부(Declaration)

3. 표현 언어(Expression Language)

4. 기본 객체(Implicit Object)

5. 정적인 데이터

6. 표준 액션 태그(Action Tag)

7. 커스텀 태그(Custom Tag)와 표준 태그 라이브러리(JSTL)

위 7가지 구성요소들을 익히는 과정이 바로 JSP를 공부하는 과정

### JSP Comment

스크립트릿과 선언부의 코드블록은 자바 코드이므로 자바의 주석을 사용할 수 있음 : `//`

JSP코드 자체를 주석처리 : `<%-- ... --%>`

---

## Representative Site

### Information

* [ruinak](https://velog.io/@ruinak_4127/%EC%9B%B9%EA%B3%BC-JSP-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)

* [ansalstmd](https://velog.io/@ansalstmd/JSP1.-%EA%B0%9C%EC%9A%94)