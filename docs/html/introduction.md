---
layout: default
title: Introduction
parent: HTML
nav_order: 1
---

# Introduction
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background Knowledge

### Internet & Web 

인터넷은 웹이 개발되기 전부터 존재했던 **컴퓨터가 연결되는 네트워크 체계**를 일컫는 말

사람들은 문서교환이 효율적으로 이루어지길 바랐고 웹문서를 쉽게 주고받는 시스템인 웹을 개발

즉 웹은 컴퓨터를 거미줄처럼 연결하여 컴퓨터들 사이에서 웹문서를 보다 쉽게 공유하기 위해 개발된 것

쉽게 말해 **인터넷을 고속도로로 비유한다면 웹은 고속도로를 이용하는 물류산업**

### WWW

**World Wide Web : 전 세계에 있는 네트워크에 연결된 시스템을 통해 정보를 공유할 수 있는 정보 공간**

![](https://gekdev.github.io/assets/images/w3c.png)

W3C는 월드 와이드 웹을 개발 및 배포, HTML 표준을 제안

1989 Tim Berners-Lee invented www (Tim Berners-Lee also invented HTML in 1991)

### URL

**URL(uniform resource locator) : 정보가 들어있는 웹페이지의 위치를 나타내는 주소**

URL은 기본적으로 '통신 규칙://인터넷 호스트 주소/경로 이름’

![](https://gekdev.github.io/assets/images/url.png)

* HTTP(Hyper Text Transfer Protocol)

    **인터넷에서, 웹 서버와 사용자의 인터넷 브라우저 사이에 문서를 전송하기 위해 사용되는 통신 규약**

    데이터에 대한 전송과 요구·응답에 대한 수정 등 가공된 정보를 포함하는 프로토콜

    이 통신 규약 뒤에는 콜론(:)을 붙이고 도메인 네임이나 IP 주소를 더 써야 하는 경우에는 슬래시 두 개 //

* 서버이름 (도메인 or IP주소)
    
    **www.un.org은 인터넷 사이트의 도메인 네임**
    
    우리가 원하는 정보가 un이라는 이름을 가진 서버(또는 컴퓨터) 안에 들어있기 때문에 그곳에 접속하겠다는 의미

* 경로, 자원이름

    **웹 페이지의 상세주소**

### Web Server & Client

웹은 컴퓨터의 기능을 서버와 클라이언트 두 가지로 나눈다

* 웹서버 : 문서나 이미지, 동영상 등을 저장
* 웹 클라이언트 : 웹브라우저를 통해 작동되며 사용자의 인터페이스 역할

![](https://gekdev.github.io/assets/images/response.png)

웹브라우저가 웹서버에 연결하려면 웹서버가 실행중인 컴퓨터의 주소를 알아야하는데 이 주소를 IP주소라 한다

웹브라우저와 웹서버는 IP주소를 이용해서 연결하기 때문에 도메인 이름을 IP주소로 변환할 필요가 있는데 , 이때 사용하는 것이 DNS(domain name server)

### Send and Receive Operations 

![](https://gekdev.github.io/assets/images/request.png)

a. 웹브라우저에 http://www.oracle.com/index.html URL을 입력했다고 가정

b. 브라우저는 서버의 주소인 www.oracle.com을 먼저 확인하고 서버컴퓨터에 연결 요청을 한다

c. 웹 서버는 연결요청을 수락한다

d. 웹페이지 index.html을 웹 서버 소프트웨어에게 요청한다

e. 웹 서버 소프트웨어는 index.html 파일을 브라우저에게 전송한다

f. 여기 까지 과정을 HTTP세션이라 부르며 마지막으로 브라우저는 받은 파일을 해석하여 그래픽으로 화면에 출력한다.

&#8594; 한 번의 HTTP세션 동안 하나의 파일만 전송된다. 즉 10개의 이미지를 가진 페이지를 출력하기 위해서는 11번의 통신을 수행해야 한다.

### Website structure and construction

![](https://gekdev.github.io/assets/images/webtrans.png)

웹사이트 : **웹서버에 있는 데이터들의 집합체** (웹문서, 웹 응용 프로그램, 데이터, 데이터베이스 등)

웹사이트 구축 : 웹서버로 사용할 컴퓨터에 웹서버 소프트웨어를 설치하고 웹페이지(웹문서)와 데이터 저장, 데이터베이스 설치, 웹 응용프로그램을 개발하여 설치하는 행위

웹 서버 소프트웨어는 브라우저의 요청을 해석하여 요구에 따른 웹문서를 전달하거나 응용 프로그램을 작동후 실행결과를 전송한다. 주로 apache사에서 만든 apache가 많이 쓰인다

웹 서버 응용 프로그램은 웹사이트에서 로그인을 한다거나, 검색, 지도를 출력 같은 다양한 서비스를 제공하는 목적으로 개발하는 것

---

## HTML5

### What is HTML5?

**웹의 비 표준을 지양하고 지능적이고 실행 가능한 웹 구현을 위해 탄생한 차세대 웹 표준 기술**

* 문서공유, 문서표현 &#8594; 하나의 응용프로그램으로 진화

* 기존의 html 표준의 한계를 극복하는 차세대 웹 표준 

* 추가적인 플러그인 없이 리치웹 응용을 가능하게 한다

* 시멘틱 마크업 &#8594; 더 명확한 의미표현

* 목적: 웹 디자이너와 웹 개발자들에게 마크업 언어를 쓰기 쉽게 만드는 것

### Features of HTML5

* 웹 문서 작성을 위한 표준화된 html 태그 셋(html 문서가 구조화되게 함)

* 플러그인 없이 미디어 등을 재생할 수 있다

* 웹 페이지를 애플리케이션으로 만들 수 있도록 한 API

* 태그로 표현됨

* 대소문자 구분 없음<br>

    **W3C recommends lowercase in HTML, and demands lowercase for stricter document types like XHTML.**

### A Simple HTML Document

![](https://gekdev.github.io/assets/images/noname01.png)

* `<!DOCTYPE html>` declaration defines this document to be HTML5 <br>
	This represents the document type, and helps browsers to display web pages correctly.
    
* `<html>` element is the root element of an HTML page

* `<head>` element contains meta information about the document (contain metadata)

* `<title>` element specifies a title for the document

* `<body>` element contains the visible page content

* `<h1>` element defines a large heading

* `<p>` element defines a paragraph

### HTML Tags
* HTML Elements
    
    HTML tags normally come in pairs like
    
    ```html
    <p> {start tag(opening tag)} </p>{end tag(closing tag)}
    ```
    The end tag is written like the start tag, but with a forward slash inserted before the tag name

* Empty HTML Elements

    Empty elements : HTML elements with no content. Empty elements do not have an end tag, such as the `<br>` element

### HTML5 Representative site
[W3C](https://html.spec.whatwg.org/multipage/)<br>
[마크업 관련 자료](http://html5doctor.com/)<br>
[쇼케이스 사이트](http://html5gallery.com/)<br>
[html5 테스트](http://html5test.com/)<br>


