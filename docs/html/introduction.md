---
layout: default
title: Introduction
parent: HTML
nav_order: 1
---

# HTML Introduction
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background Knowledge

### Internet & Web 

인터넷 : **컴퓨터가 연결되는 네트워크 체계** (웹이 개발되기 전부터 존재)

사람들은 문서교환이 효율적으로 이루어지길 바랐고 웹문서를 쉽게 주고받는 시스템인 웹을 개발

즉 웹은 컴퓨터를 거미줄처럼 연결하여 컴퓨터들 사이에서 **웹문서를 보다 쉽게 공유하기 위해 개발**된 것

쉽게 말해 인터넷을 고속도로로 비유한다면 웹은 고속도로를 이용하는 물류산업

### WWW

![](https://gekdev.github.io/assets/images/w3c.png)

World Wide Web : 전 세계에 있는 네트워크에 연결된 시스템을 통해 **정보를 공유할 수 있는 정보 공간**

W3C(팀 버너스리)가 1989에 개발 및 배포, 1991에 HTML 표준을 제안

### URL

![](https://gekdev.github.io/assets/images/url.png)

Uniform Resource Locator : **정보가 들어있는 웹페이지의 위치를 나타내는 주소**

&#8594; 기본적으로 **'통신 규칙://인터넷 호스트 주소/경로 이름’**

* HTTP (Hyper Text Transfer Protocol)

    인터넷에서, 웹 서버와 사용자의 인터넷 브라우저 사이에 **문서를 전송하기 위해 사용되는 통신 규약**

    데이터에 대한 전송과 요구·응답에 대한 수정 등 가공된 정보를 포함하는 프로토콜

    이 통신 규약 뒤에는 콜론(:)을 붙이고, 그 뒤로 도메인 네임이나 IP 주소를 더 써야 하는 경우에는 슬래시 두 개 (//)

* 서버이름 (도메인 or IP주소)
    
    www.un.org은 **인터넷 사이트의 도메인 네임**
    
    우리가 원하는 정보가 un이라는 이름을 가진 서버(또는 컴퓨터) 안에 들어있기 때문에 그곳에 접속하겠다는 의미
    
    IP주소란?
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    **웹서버가 실행중인 컴퓨터의 주소** (웹브라우저가 웹서버에 연결하려면 알아야 함)

    &#8594; 웹브라우저와 웹서버는 IP주소를 이용해서 연결하기 때문에 도메인 이름을 IP주소로 변환할 필요가 있는데 , 이때 사용하는 것이 DNS(domain name server)
    </div>
    
* 경로, 자원이름

    **웹 페이지의 상세주소**

### Web Server & Client

![](https://gekdev.github.io/assets/images/response.png)

웹은 컴퓨터의 기능을 서버와 클라이언트 두 가지로 나눈다

* 웹 서버 : 문서나 이미지, 동영상 등을 저장
* 웹 클라이언트 : 웹브라우저를 통해 작동되며 사용자의 인터페이스 역할
    
    웹 브라우저 : 서버로부터 제공받은 데이터들을 해석하고 출력해주는 역할

### Send and Receive Operations 

![](https://gekdev.github.io/assets/images/request.png)

1. 웹브라우저에 http://www.oracle.com/index.html URL을 입력했다고 가정

2. 브라우저는 서버의 주소인 www.oracle.com을 먼저 확인하고 서버컴퓨터에 연결 요청을 한다

3. 웹 서버는 연결요청을 수락한다

4. 웹페이지 index.html을 웹 서버 소프트웨어에게 요청한다

5. 웹 서버 소프트웨어는 index.html 파일을 브라우저에게 전송한다

6. 여기 까지 과정을 HTTP세션이라 부르며 마지막으로 브라우저는 받은 파일을 해석하여 그래픽으로 화면에 출력한다.

&#8594; 한 번의 HTTP세션 동안 하나의 파일만 전송된다. 즉 10개의 이미지를 가진 페이지를 출력하기 위해서는 11번의 통신을 수행해야 한다.

### Website Structure and Construction

![](https://gekdev.github.io/assets/images/webtrans.png)

* 웹사이트 : **웹서버에 있는 데이터들의 집합체** (웹문서, 웹 응용 프로그램, 데이터, 데이터베이스 등)

* 웹 페이지의 3대 구성요소 : HTML (웹 페이지의 구조와 내용), CSS (웹 페이지의 모양), Javascipt(웹 페이지의 동적 변경 및 응용프로그램 작성)

* 웹사이트 구축 : 웹서버로 사용할 컴퓨터에 웹서버 소프트웨어를 설치하고 웹페이지(웹문서)와 데이터 저장, 데이터베이스 설치, 웹 응용프로그램을 개발하여 설치하는 행위

웹 서버 소프트웨어는 브라우저의 요청을 해석하여 요구에 따른 웹문서를 전달하거나 응용 프로그램을 작동후 실행결과를 전송한다. 주로 apache사에서 만든 apache가 많이 쓰인다

웹 서버 응용 프로그램은 웹사이트에서 로그인을 한다거나, 검색, 지도를 출력 같은 다양한 서비스를 제공하는 목적으로 개발하는 것

---

## HTML5

### What is HTML5?

**웹의 비 표준을 지양하고 지능적이고 실행 가능한 웹 구현을 위해 탄생한 차세대 웹 표준 기술**

* 문서공유, 문서표현 &#8594; **하나의 응용프로그램으로 진화**

* 기존의 html 표준의 한계를 극복하는 차세대 웹 표준 

* 추가적인 플러그인 없이 리치웹 응용을 가능하게 한다

* 시멘틱 마크업 &#8594; **더 명확한 의미표현**

* 목적: 웹 디자이너와 웹 개발자들에게 마크업 언어를 쓰기 쉽게 만드는 것

### Features of HTML5

* 웹 문서 작성을 위한 표준화된 html 태그 구성(html 문서가 구조화되게 함)

* 플러그인 없이 미디어 등을 재생할 수 있다

* 웹 페이지를 애플리케이션으로 만들 수 있도록 한 API

* 태그로 표현

* 대소문자 구분 없지만 소문자 사용 권하고 xhtml에서는 소문자만 사용해야함

---

## Setting Environment

### Web Browser

* Chrome

    확장자 도구 : web developer, outline

### Text editor

* 대표적인 에디터 : Brackets, Atom, Visual Studio Code, Eclipse

* 확장기능 관리자

    &#9656; Emmet : html 태그 자동완성
    
    > [Emmet 명령어](https://velog.io/@aepee/Emmet-%EC%82%AC%EC%9A%A9%EB%B2%95)

    &#9656; tree icons : 아이콘 이미지

    &#9656; color highlighter : 색 표시

    &#9656; custom work : 파일 보여줌


학원에서 주로 쓰는 툴 Eclipse, 처음 설정하는 법
{: .label .mt-2}
<div class="code-example" markdown="1">

1. Window preferences > general > appearance > colors and fonts > basic > text editor... & text font 폰트를 D2Coding ligature 으로 바꾸고 (코딩할때 좋은 폰트)

2. Window preferences > general > workspace utf-8로 바꾸기

3. Window preferences > web > CSS, HTML, JSP files  encoding 모두 utf-8로 바꾸기

----

help > eclipse marketplace 에서 emmet 설치
</div>

### Web Accessibility Check

* 에이쿨첵! : 웹 접근성 솔루션 검사 프로그램
    
    <span class="fs-2">
    [다운로드](https://software.naver.com/software/summary.nhn?softwareId=GWS_000915#){: .btn  .btn-outline .mt-2}
    </span>
    
---

## Representative Site

### Information

* [Codecademy](https://www.codecademy.com/)

* [W3C Examples](https://www.w3schools.com/html/html_examples.asp)

* [whatwg](https://html.spec.whatwg.org/multipage/)

* [html5doctor](http://html5doctor.com/)

* [html5gallery](http://html5gallery.com/)

* [html5test](http://html5test.com/)

* [다양한 강연자료 모음](http://channy.creation.net/lecture)

### Quiz

* [W3C Quiz](https://www.w3schools.com/quiztest/quiztest.asp?qtest=HTML)

* [W3C Exercise](https://www.w3schools.com/html/exercise.asp)
