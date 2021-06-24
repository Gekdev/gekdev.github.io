---
layout: default
title: Implicit Object
parent: JSP
nav_order: 5
has_children : true
---

# JSP Script
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Implicit Object
{: no_toc}

### What is Implicit Object

**웹 어플리케이션 프로그래밍을 하는데 JSP 페이지에서 사용할 수 있도록 필요한 기능을 제공해주는 JSP 컨테이너에 미리 정의된 객체**

&#9656; JSP는 웹애플리케이션 프로그래밍을 하는데 필요한 기능을 제공해주는 내장 객체를 제공 (객체들 마다 웹 애플리케이션에서 필요한 고유한 기능을 제공)

&#9656; JSP 페이지가 서블릿 프로그램으로 번역될 때 JSP 컨테이너가 자동으로 내장 객체를 멤버 변수, 메소드 매개변수 등의 각종 참조 변수(객체)로 포함

&#9656; JSP 페이지에 별도의 import문 없이 자유롭게 사용 가능

&#9656; 스크립틀릿 태그나 표현문 태그에 선언을 하거나 객체를 생성하지 않고도 직접 호출하여 사용 가능

### Implicit Objects

**대표적인 내장 객체**

exception 기본 객체를 제외한 나머지 객체들은 모든 JSP 페이지에 사용할 수 있음 (exception은 오직 에러페이지에서만 사용가능)

page 기본 객체는 JSP를 변환한 자바 클래스의 인스턴스를 나타냄 (거의사용 X)

config 기본 객체도 거의사용 X

| 내장객체 	   | 실제 타입 		     				    | 설명 															      |
|:-------------|:---------------------------------------|:----------------------------------------------------------------------|
| request 	   | javax.servlet.http.HttpServletRequest 	| 요청 파라미터 읽어오기, 웹 브라우저가 웹 서버에 요청하는 정보를 전달  |
| response     | javax.servlet.http.HttpServletResponse | 응답 결과 전송하기, 웹서버에 요청된 결과를 응답하는 정보를 제공       |
| session      | javax.servlet.http.HttpSession 		| HTTP 세션 정보를 저장한다                                             |
| application  | javax.servlet.ServletContext 			| 웹어플리케이션 정보를 저장하고 읽기                                   |
| pageContext  | java.servlet.jsp.PageContext 			| JSP 페이지에 대한 정보를 저장                                         |
| page         | java.lang.Object 						| JSP 페이지를 구현한 자바 클래스로 JSP 페이지 자체를 나타냄            |
| out          | javax.servlet.jsp.jspWriter 			| DOM 출력, JSP 페이지가 생성하는 결과를 출력할 때 사용하는 출력스트림  |
| config 	   | javax.servlet.ServletConfig			| JSP 페이지에 대한 설정정보를 저장                                     | 
| exception    | java.lang.Throwable 					| 익셉션객체, 에러페이지에서만 사용                                     |

![](https://gekdev.github.io/docs/jsp/elements/example/Implicitexample.png)
