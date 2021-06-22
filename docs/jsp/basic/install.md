---
layout: default
title: Install
parent: Basic
grand_parent : JSP
nav_order: 1
---

# Basic Install
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Building a JSP Development Environment

### JSP Development Environment Tools

* 자바 개발환경 : JDK 

    HTML 코드 내에 자바 코드를 작성하기 때문에 자바 개발 도구인 JDK가 반드시 설치되어 있어야 함

* 웹서버 : 톰캣

    웹 프로그래밍 언어로 작성된 웹 페이지가 실행되어 웹브라우저에 나타나도록 하기위해 컨테이너가 있어야 함
    
    JSP 웹 컨테이너로 자주 사용되는 것 중 하나인 톰켓은 오픈소스 프로젝트로 무료로 누구나 사용가능

* 통합 개발 환경 : 이클립스

### Install Java and Set Preferences

* 자바 개발 키트 : JDK(Java Development Kit)

* 자바 실행 환경 : JRE(Java Runtime Environment)

![](https://gekdev.github.io/docs/jsp/basic/example/img.png)

[자바설치는 여기로~](https://gekdev.github.io/docs/java/basic/install/)

### Apache Tomcat® Install

1. **다운로드**

    <span class="fs-2">
    [Apache Tomcat®](https://tomcat.apache.org/download-90.cgi){: .btn .btn-outline .mt-2}
    </span>

    아래파일 다운로드받기

    ![](https://gekdev.github.io/docs/jsp/basic/example/apach.png)

2. **로컬디스크 C에다가 압축풀기**

### Change Environment Variable

1. **실행창 열고 `sysdm.cpl` 치기**

    ![](https://gekdev.github.io/docs/jsp/basic/example/comm.jpg) 

2. **시스템속성&#8594; 고급&#8594; 환경변수&#8594; 시스템변수 추가하기**

    ![](https://gekdev.github.io/docs/jsp/basic/example/new.jpg)

    * 변수이름  → CATALINA_HOME
    
    * 값        → c:\tomcat-9.0.48 (톰켓이 설치된 경로로 주는것)

3. **path 변수에 추가**

    **%CATALINA_HOME%\bin**

    ![](https://gekdev.github.io/docs/jsp/basic/example/add.JPG)

### CMD Startup

1. 톰켓 경로잡기

    ```java
    cd..
    cd..
    cd tomcat-9.0.48
    cd dir
    ```
    
    &#8594; 여기 dir을 확인했을때 bin이 있는지 확인

2. startup 명령으로 톰켓 설치하기

    ```java
    startup
    ```

    외장하드에다가 풀고 cmd해봤는데 안됨 (따로 연결 문제가 있는듯 함)
    {: .fs-3 .text-grey-dk-200 .fw-700 .mt-3}

3. 창닫기

    서버가 알아서 죽음

![](https://gekdev.github.io/docs/jsp/basic/example/cmd.JPG)

### Change Port

0. **C:\tomcat-9.0.48\conf 경로로 가기**

1. **server.xml 파일 복사하기**
    
    ![](https://gekdev.github.io/docs/jsp/basic/example/copy.jpg)

2. **원본파일을 메모장으로 열기**

3. **Connector port를 검색한 후 8080 &#8594; 8088로 바꾸기** (하나만)

    ![](https://gekdev.github.io/docs/jsp/basic/example/8088.JPG)

    Port?
    {: .label .label-yellow .mt-2}
    <div class="code-example" markdown="1">
    오라클 데이터베이스는 1521, 8080 포트를 사용함

    WAS의 톰켓도 8080이 기본이라서 변경해주는것!
    </div>

### CMD Startup

1. 꺼졌던 CMD창 다시 열기

2. **startup명령어 치기 (경로 상관 X)**

    서버를 실행한다는 의미

2. **크롬 실행 후 http://localhost:8088/**

    이 화면이 나오면 성공!
    
    ![](https://gekdev.github.io/docs/jsp/basic/example/index.png)

### index.html

C:\tomcat-9.0.48\webapps\ROOT 여기가 루트

![](https://gekdev.github.io/docs/jsp/basic/example/index.jpg)

---

## Eclipse Setting

### Default Setting

Open Perspective 에서 Java EE로 세팅

![](https://gekdev.github.io/docs/jsp/basic/example/javaee.jpg)

### Dynamic Web Project 

**JSP파일은 동적 웹 프로젝트 파일로 생성해야 함**

![](https://gekdev.github.io/docs/jsp/basic/example/project1.JPG)

### Server

#### Connect Server

처음 JSP 하고 새로운 서버 생성시 

![](https://gekdev.github.io/docs/jsp/basic/example/3.server.jpg)

![](https://gekdev.github.io/docs/jsp/basic/example/4.cntserver.JPG)

#### Check Server

1. **Preferences &#8594; Server &#8594; Runtime Environments**

    **어느 서버를 사용하는지 확인할 수 있음**

![](https://gekdev.github.io/docs/jsp/basic/example/5.chkserver.jpg)

#### Add Resources to Server

![](https://gekdev.github.io/docs/jsp/basic/example/0.server.jpg)

![](https://gekdev.github.io/docs/jsp/basic/example/1.server.JPG)

### Root

**C:\tomcat-9.0.48\webapps\ROOT경로와 eclipse의 WebContent가 같은 경로**

![](https://gekdev.github.io/docs/jsp/basic/example/2.root.jpg)

### Template

0. 템플릿 설정하기 전 먼저 해야하는것 

    1. **Build path &#8594; Configure Build path**
    
    2. **Libraries &#8594; Add Library &#8594; Server Runtime** 

        ![](https://gekdev.github.io/docs/jsp/basic/example/adlib.JPG)
    
    3. add된 모습
    
        ![](https://gekdev.github.io/docs/jsp/basic/example/adlibadd.JPG)
        
    **Apache Tomcat v9.0 라이브러리를 해놔야지 ${encoding}부분이 알아서 변경됨**

1. Preferences &#8594; Web &#8594; JSP &#8594; Files &#8594; Templates

2. New JSP File (html 5) 파일을 수정하기

    ```jsp
    <%@ page language="java" contentType="text/html; charset=${encoding}" pageEncoding="${encoding}"%>
    <!DOCTYPE html>
    <html>
    <head>
       <meta charset="${encoding}">
         <meta name="viewport" content="width=device-width, initial-scale=1">
         <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
         <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
         <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>
         <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>   
    </head>
    <body>
    ${cursor}
    </body>
    </html>
    ```

    ![](https://gekdev.github.io/docs/jsp/basic/example/6.templates.JPG)
