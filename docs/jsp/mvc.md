---
layout: default
title: MVC Pattern
parent: JSP
nav_order: 14
---

# JSP MVC Pattern
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### 커맨드 패턴 기반의 프로그램

MVC패턴에서 컨트롤러 서블릿이 수행하는 작업은 사용자가 어떤 기능을 요청했는지를 분석하는 것

사용자의 요청을 판단하기 위해서 사용하는 방법 중 가장 일반적인 방법은 명령어를 사용하는 것

1. 사용자가 게시판 목록보기, 글쓰기 등의 명령을 서블릿에 전송하고 

2. 컨트롤러 서블릿은 사용자가 전송한 요청에 해당하는 기능을 수행한 후에

3. View를 통해 결과를 보여주는 패턴을 커맨드 패턴이라고 한다

커멘트 패턴에서 파라미터에 명령어 정보를 전달하는 두가지 방법

1. 특정 이름의 파라미터에 명령어 정보를 전달하는 방법(ControllerUsingFile.java)

	```jsp
	localhost:8088/mvc/ControllerUsingFile?cmd=hello
	```

2. 요청되는 URI자체를 명령어로 사용하는 방법(ControllerUsingURI.java)

    ```jsp
    localhost:8088/mvc/member.do
    ```
    

