---
layout: default
title: Introduction
parent: JSP
nav_order: 1
---

# JSP Introduction
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Internet & Web

### What is Internet & Web?

인터넷(internet)과 웹(web)은 대개 동의어로 쓰이지만 서로 다른 개념임

&#9656; 인터넷의 활용에서 웹의 비중이 절대적 위치를 차지하여 흔히 인터넷과 웹을 같은 의미로 사용

&#9656; 인터넷 내부에 이메일, 웹, 파일송수신, 텔넷 등이 포함

* 인터넷 : 컴퓨터가 서로 연결되어 TCP/IP라는 통신 프로토콜을 이용하여 정보를 주고 받는 전세계의 컴퓨터 네트워크

* 웹 : 인터넷을 통해 광범위한 정보를 제공할 수 있는 서비스 중 하나

    &#9656; 인터넷에 연결된 컴퓨터들을 통해 사람들이 정보를 공유할 수 있는 정보 공간

    &#9656; 월드 와이드 웹(world wide web)의 줄임말

![](https://gekdev.github.io/docs/jsp/example/internet.png)

### How the Web Works

웹은 기본적으로 클라이언트/서버 방식으로 동작

클라이언트(웹 브라우저)가 특정 페이지를 웹 서버에 요청(request)하면 이를 처리한 후 그 결과를 클라이언트에게 보내어 응답(response)

즉 웹브라우저에 원하는 웹 서버 주소를 입력(요청)하면 웹 서버가 웹 브라우저를 통해 해당 웹 페이지를 제공(응답)

&#9656; 요청하는 쪽이 클라이언트(사용자)이고 응답하는 쪽이 서버(제공자)

&#9656; 가장 널리쓰이는 웹 서버로 아파치(Apache), 톰캣(Tomcat), IIS(Internet Information Server)등

---

## Web Pages

### Static Web Page

**컴퓨터에 저장된 텍스트 파일을 그대로 보는 것, HTML(Hyper Text Markup Language)과 같은 웹 언어로 작성**

&#8594; 가장 단순한 형태의 웹 언어

&#9656; 추가적인 처리 과정 없이 클라이언트에게 응답을 보냄

&#9656; 회사나 개인의 소개 페이지가 정적 웹 페이지의 좋은 예시

![](https://gekdev.github.io/docs/jsp/example/static.png)

#### How Static Web Pages Work

1. 클라이언트가 웹 브라우저를 통해 웹 서버에 웹 페이지(URL) 요청

2. 해당 URL의 웹 서버가 수신된 .html 파일을 검색

3. 이미 준비된 HTML 문서를 클라이언트에게 그대로 전송

4. 웹 브라우저가 HTML 문서를 보여줌

장점
{: .label .mt-2}
<div class="code-example" markdown="1">
- 동적인 요소가 없기 때문에 데이터베이스가 필요없음

- 구축하기 쉬우며, 단순 문서로만 이루어져 있어 서버 간 통신이 거의 없고 속도가 빠름

- 정적 문서로만 이루어져 있기 때문에 모든 호스팅 서버에서 동작할 수 있음
</div>

단점
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
- 미리 만들어 놓은 정보만 보여주기 때문에 고객의 취향이나 변화에 적응할 수 없음

- 새로운 것을 추가, 수정, 삭제하는 작업을 모두 수동으로 해야 하므로 관리가 어려움
</div>

### Dynamic Web Pages

**저장된 내용을 다른 변수로 가공 처리하여 보는 것**

&#9656; 기술이 발전함에 따라 사용자의 기호에 맞게 능동적으로 변화하는 웹 페이지가 필요해져서 이를 위해 동적 웹 페이지를 제공하는 PHP(Personal Home Page), ASP(Active Server Page), JSP와 같은 웹 언어가 개발됨

&#9656; 동적 페이지는 방문자와 상호작용하기 때문에 웹 페이지 상에서 특정 부분을 동적으로 바꾸는 형태로 사용해 페이지 내용은 그때그때 다름

&#9656; 댓글, 날씨, 주가 정보 등과 같이 정보 변경이 잦은 곳에 많이 사용됨 

![](https://gekdev.github.io/docs/jsp/example/dynamic.png)

#### How Dynamic Web Pages Work

사용자가 웹 페이지에 글을 작성하거나 환경 설정 등을 바꾸면 그내용이 서버에 있는 데이터베이스에 저장되고 결과가 웹 페이지에 반영되는 형태로 동작

1. 클라이언트가 웹 브라우저를 통해 웹 서버에 웹 페이지(URL) 요청

2. 해당 URL의 웹 서버가 요청을 분석하여 처리

3. 결과를 HTML 문서로 생성

4. 요청에 맞게 정제된 HTML 문서를 클라이언트에게 전달

5. 웹 브라우저가 HTML 문서를 보여줌

로그인하면 개인에 대한 정보와 개인만의 화면으로 구성되는 웹 사이트가 동적 웹 페이지의 대표적인 예

파이썬으로 동적 웹페이지 크롤링
{: .label .mt-2}
<div class="code-example" markdown="1">
requests 라이브러리를 이용해서는 나타나지 않는 데이터들을 수집하는 가장 손쉬운 방법은 코드로 브라우저를 제어하는 것

Selenium 라이브러리를 사용하면 브라우저의 동작을 파이썬 코드로 조작할 수 있음

이 라이브러리를 활용해서 원하는 페이지에 접근해서 동적 데이터가 모두 로딩된 이후의 상태를 크롤링하면 됨
</div>

---

## Representative Site

### Information

* [ruinak](https://velog.io/@ruinak_4127/%EC%9B%B9%EA%B3%BC-JSP-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0)

* [Hogni](https://hogni.tistory.com/75)
