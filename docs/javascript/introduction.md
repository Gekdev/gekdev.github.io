---
layout: default
title: Introduction
parent: JavaScript
nav_order: 1
---

# JS Introduction
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

--- 

## JavaScript

### What is Javascript?

**html과 웹의 프로그래밍 언어**

&#9656; `<script>` 태그가 client-side script(JavaScript)를 정의하는데 사용됨

&#9656; `<script>` 태그로 스크립트 내용이 들어가거나, 외부 파일을 들여올 수 있음

### Why Study JavaScript?

매우 다양하게 쓰이기 때문에 잘 알아둬야 함
 
**웹 개발자가 꼭 알아야하는 3가지 필수 언어**

1. HTML → define the content
2. CSS → specify the layout
3. JavaScript →  program the behavior

### Why Use JavaScript?

가장 많은 사용 이유 : 이미지 조작, 양식 유효성 검사, 콘텐츠의 동적 변경

### What can JavaScript do?

1. Change HTML Content = .innerHTML

2. Change HTML Attribute Values = .src

3. Change HTML Styles (CSS) = style.display or style.fontSize

4. Hide HTML Elements = .style.display = "none";

5. Show HTML Elements = .style.display = "block";

<div class="code-example" markdown="1">
<img id="myImage" src="https://www.w3schools.com/js/pic_bulboff.gif" style="width:100px">

<button onclick="document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulbon.gif'">Turn on the light</button>

<button onclick="document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulboff.gif'">Turn off the light</button>
</div>
```html
<img id="myImage" src="https://www.w3schools.com/js/pic_bulboff.gif" style="width:100px">

<button onclick="document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulbon.gif'">Turn on the light</button>

<button onclick="document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulboff.gif'">Turn off the light</button>
```

### Features of JavaScript

* 다운로드가 필요없고 모든 기기에서 돌아가는 무료언어
 
* 사용자의 입력 및 계산

* 웹페이지 내용 및 모양의 동적 제어

* 브라우저 제어

* 서버와의 통신

* 웹 애플리케이션 작성

---

## Representative Site

### Information

* [W3C Examples](https://www.w3schools.com/js/js_examples.asp)

* [모질라](https://developer.mozilla.org/ko/docs/Web/JavaScript)

### Quiz

* [W3C Exercises](https://www.w3schools.com/js/exercise_js.asp?filename=exercise_js_variables1)

* [W3C Quiz](https://www.w3schools.com/quiztest/quiztest.asp?qtest=JavaScript)
