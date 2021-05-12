---
layout: default
title: HTML DOM
parent: JavaScript
nav_order: 18
has_children: true
---

# JavaScript HTML DOM
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## HTML DOM Basic

### The HTML DOM (Document Object Model)

웹 페이지가 로드되면 브라우저는 **D**ocument **O**bject **M**odel을 만듦

![](https://www.w3schools.com/js/pic_htmltree.gif)

위 DOM 모델로 자바스크립트는 html 태그를 제어할 수 있음

### What is the DOM?

W3C DOM (Document Object Model)은 **프로그램 및 스크립트가 문서의 컨텐츠, 구조 및 스타일에 동적으로 액세스하고 업데이트 할 수 있는 플랫폼 및 언어 중립 인터페이스**

Dom은 **문서에 액세스하기위한 표준을 정의**

W3C (World Wide Web Consortium) 표준임

W3C DOM standard은 3가지 파트로 나뉨

* Core DOM : standard model for all document types

* XML DOM : standard model for XML documents

* HTML DOM : standard model for HTML documents


### What is the HTML DOM?

**HTML DOM은 HTML의 표준 객체 모델 및 프로그래밍 인터페이스**

* 객체 로서의 HTML 요소를 정의

* 모든 HTML 요소 의 속성을 정의

* 모든 HTML 요소에 액세스 하는 방법을 정의

* 이벤트 의 모든 HTML 요소를 정의

즉 , HTML DOM은 **HTML 요소를 가져 오거나 변경, 추가 또는 삭제하는 방법에 대한 표준**

---

## HTML DOM Methods

HTML DOM은 **JavaScript 및 다른 프로그래밍 언어로 액세스 할 수 있음**

DOM에서 **모든 HTML 요소는 objects**로 정의됨

### The DOM Programming Interface

**프로그래밍 인터페이스 : 각 객체의 속성과 메서드**

&#9656; property : 가져 오거나 설정할 수있는 값 (HTML 요소 내용을 변경 등)

&#9656; method : action you can do (추가 또는 HTML 요소를 삭제 등) 

예제
{: .label .label-purple .mt-3}
```js
document.getElementById("demo").innerHTML = "Hello World!";
//etElementById is a method, while innerHTML is a property
```

### The getElementById Method

**most common way to access an HTML element**

[HTML Element]() 에서 자세하게 확인가능

### The innerHTML Property

**easiest way to get the content of an element**

HTML 요소의 내용을 가져 오거나 바꾸는 데 유용

---

## The HTML DOM Document Object

**웹 페이지에있는 다른 모든 객체의 소유자**

document 객체는 웹 페이지를 나타냄

html 요소에 접근하려면 항상 문서 객체에 접근하는것에서 시작

### Finding HTML Elements

| Method                                  | Description            |
|:----------------------------------------|:-----------------------|
| document.getElementById(id)	          | 요소 id로 요소찾기       |
| document.getElementsByTagName(name)	  | 태그 이름으로 요소찾기    | 
| document.getElementsByClassName(name)	  | 클래스 이름으로 요소찾기   |

### Changing HTML Elements

| Property                                | Description            |
|:----------------------------------------|:-----------------------|
| element.innerHTML =  new html content	  | 요소의 내부 html 바꾸기   |
| element.attribute = new value	          | 요소의 attribute 바꾸기  | 
| element.style.property = new style	  | 요소의 스타일 바꾸기      |

| Method                                  | Description            |
|:----------------------------------------|:-----------------------|
| element.setAttribute(attribute, value)  | 요소의 attribute 바꾸기  |

### Adding and Deleting Elements

| Method                                  | Description            |
|:----------------------------------------|:-----------------------|
| document.createElement(element)	      | 요소 생성                |
| document.removeChild(element)	          | 요소 제거                | 
| document.appendChild(element)           | 요소 추가                |
| document.replaceChild(new, old)         | 요소 대체                |
| document.write(text)                    | HTML 출력 스트림에 쓰기   |

### Adding Events Handlers

| Method                                                  | Description                                     |
|:--------------------------------------------------------|:------------------------------------------------|
| document.getElementById(id).onclick = function(){code}  | Adding event handler code to an onclick event   |

### Finding HTML Objects

HTML objects, object collections, properties

가장 자주 보이는 속성 위주로 추렸음

| Property                   | Description                                          | DOM|
|:---------------------------|:-----------------------------------------------------|:---|
| document.anchors           | Returns all `<a>` elements that have a name attribute| 1  |
| document.baseURI	         | Returns the absolute base URI of the document        | 3  |
| document.body              | Returns the `<body>` element                         | 1  |
| document.cookie            | Returns the document's cookie                        | 2  |
| document.documentElement   | Returns the `<html>` element                         | 3  |
| document.forms	         | Returns all `<form>` elements                        | 1  |
| document.head              | Returns the `<head>` element                         | 3  |
| document.images	         | Returns all `<img>` elements                         | 1  |
| document.embeds	         | Returns all `<embed>` elements                       | 3  |
| document.scripts	         | Returns all `<script>` elements                      | 3  |
| document.title	         | Returns the `<title>` element                        | 1  |
| document.URL	             | Returns the complete URL of the document             | 1  |

