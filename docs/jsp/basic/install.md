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

## Installation & Setting

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

2. **환경변수 추가하기**

    ![](https://gekdev.github.io/docs/jsp/basic/example/new.jpg)

    <div class="code-example" markdown="1">
    * 변수이름  → CATALINA_HOME
    
    * 값        → c:\tomcat-9.0.48 (톰켓이 설치된 경로로 주는것)
    </div>

3. path 변수에 추가

    ![](https://gekdev.github.io/docs/jsp/basic/example/add.jpg)

    <div class="code-example" markdown="1">
    %CATALINA_HOME%\bin
    </div>

### CMD Startup

![](https://gekdev.github.io/docs/jsp/basic/example/cmd.jpg)

1. 톰켓 경로잡기

    ```cmd
    cd..
    cd..
    cd tomcat-9.0.48
    cd dir
    ```
    
    여기 dir을 확인했을때 bin이 있는지 확인

2. startup 명령으로 톰켓 설치하기

    ```cmd
    startup
    ```

3. 창닫기

    서버가 알아서 죽음

### Change Port

0. **C:\tomcat-9.0.48\conf 경로로 가기**

1. **server.xml 파일 복사하기**
    
    ![](https://gekdev.github.io/docs/jsp/basic/example/copy.jpg)

2. **원본파일을 메모장으로 열기**

3. **Connector port를 검색한 후 8080 &#8594; 8088로 바꾸기**

    ![](https://gekdev.github.io/docs/jsp/basic/example/8088.jpg)

    오라클 데이터베이스는 1521, 8080 포트를 사용함

    WAS의 톰켓도 8080이 기본이라서 변경해주는것!

### CMD Startup

1. **cmd startup 다시 실행**

    서버를 실행한다는 의미!

2. **크롬 실행 후 http://localhost:8088/**

### index.html

C:\tomcat-9.0.48\webapps\ROOT 여기가 루트

![](https://gekdev.github.io/docs/jsp/basic/example/index.jpg)

---

## Eclipse Setting

### 

![](https://gekdev.github.io/docs/jsp/basic/example/javaee.jpg)

![](https://gekdev.github.io/docs/jsp/basic/example/project1.JPG)