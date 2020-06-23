---
layout: default
title: Introduction
parent: CSS
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


---

## CSS

### What is CSS?

CSS stands for Cascading Style Sheets
CSS describes how HTML elements are to be displayed on screen, paper, or in other media
CSS saves a lot of work. It can control the layout of multiple web pages all at once
External stylesheets are stored in CSS files
CSS html 문서에 색이나 모양, 출력 위치 등 외관을 꾸미는 언어
CSS로 작성된 코드를 스타일 시트라고 부른다


### Features of CSS

대소문자 구분 없음
 
### CSS Syntax

A CSS rule-set consists of a selector and a declaration block

![](https://gekdev.github.io/assets/images/selector.gif)

* selector : 스타일 시트의 이름이나 규칙, 같은 이름의 모든 html태그에 스타일 시트가 적용
* property: 약 200개
    

### CSS Comments

```html
/* This is a single-line comment */

/* This is
a multi-line
comment */
```

### CSS Links

* 반드시 &#60;head&#62;안 &#60;style&#62;&#60;/style&#62; 태그에 스타일 시트 작성

	&#8594; 여러번 작성 가능, 합쳐 적용됨
    
	&#8594; &#60;style&#62;에 작성된 스타일 시트는 웹 페이지 전체에서 적용됨
    
* style attribute로 스타일 시트 작성

	해당 태그에만 스타일 적용
    
* style sheet을 별도로 작성 = &#60;link&#62; tag

    ```html
    <head>
        <link href="주소/A.css" type="text/css" rel="stylesheet">  
    </head>
	```
    * href : 주소/A.css파일을 불러올 것을 지시
    
    * type : 불러오는 파일이 CSS언어로 작성된 파일임을 알려줌
    
    * rel : 불러오는 파일이 stylesheet라는걸 알려줌
	
    &#9656; 여러번 사용해 다양한 CSS파일을 불러올 수 있음
    
	&#9656; CSS파일에는 &#60;style&#62; tag 없이 저장해야함
	
* @import
    
    ```html
    <style>
		@import url('A.css');
    </style>	
    ```
		
	&#9656; 여러번 사용해 다양한 CSS파일을 불러올 수 있음

CSS규칙
{: .label .mt-3}
<div class="code-example" markdown="1">
스타일은 부모로부터 상속
스타일 우선순위 : style attribute > &#60;style&#62; tag > .css style file > default
<div>

### CSS Links