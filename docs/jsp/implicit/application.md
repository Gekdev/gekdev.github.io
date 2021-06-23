---
layout: default
title: Application
parent: Implicit Object
grand_parent : JSP
nav_order: 4
---

# Application Implicit Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Application Implicit Object

### 

application 객체는 웹애플리케이션 전반에 걸쳐서 사용되는 정보를 저장할 수 있음

예를들어 application객체를 사용해 초기설정정보, 서버정보, 웹애플리케이션에서 제공하는 정보들을 읽을 수 있음

서블릿 규약에서는 웹애플리케이션 전체에 걸쳐서 사용할 수 있는 초기화 파라미터를 정의하고 있음

초기화 파라미터는 web.xml에 <context-param>태그를 사용해서 추가할 수 있음

### web.xml File

**웹 어플리케이션을 위한 설정 정보를 담고있는 파일**

&#9656; jsp프로그래밍을 할 때 꼭 필요한 파일은 아니지만 환경설정파일로서 중요한 파일

&#9656; 이 파일은 반드시 WEB-INF폴더에 위치해야 함

&#8594; 다른 폴더에 위치하게 되면 인식하지 못함

### application 객체의 초기화 메서드

| 메서드 				| 리턴타입 			| 설명 							|
|:----------------------|:------------------|:------------------------------|
| getInitParameter(String name) | String | 이름이 name인 초기화 파라미터의 값을 읽음, 존재하지 않으면 null | 
| getInitParameterNames()	| Enumeration<String> | 웹 어플리케이션 초기화 파라미터의 이름 목록을 리턴 |

### applicaiton 서버관련 메서드

| 메서드 				| 리턴타입 			| 설명 							|
|:----------------------|:------------------|:------------------------------|
| getServerInfo()		| String 			| 서버정보를 구함 				|
| getMajorVersion()		| String 			| 웹 서버가 지원하는 서블릿규약의 메이저 버전정보를 리턴 |
| getMinorVersion()		| String 			| 웹 서버가 지원하는 서블릿규약의 마이너 버전정보를 리턴 |

### 로그 메시지 기록하기

**application 객체는 웹컨테이너가 사용하는 로그파일에 로그메시지를 기록할 수 있도록 관련 메서드를 제공**