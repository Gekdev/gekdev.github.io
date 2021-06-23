---
layout: default
title: Elements
parent: Basic
grand_parent : JSP
nav_order: 2
---

# Basic Elements
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

##

### JSP Code Structure

JSP코드는 HTML문서를 생성하는게 주된 목적

JSP코드는 크게 설정부분과 응답 생성부분으로 구성됨

* 설정부분 : **JSP페이지에 대한 설정 정보**

    &#9656; **page디렉티브로 생성함**

    1. JSP 페이지가 생성하는 문서의 타입(종류)
    
    2. JSP 페이지에서 사용할 커스텀 태그
    
    3. JSP 페이지에서 사용할 자바 클래스 지정 등

* 생성부분 : **HTML코드 및 JSP 스크립트**

---

## JSP Elements 

### JSP Elements Basic

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
