---
layout: default
title: Basic
parent: HTML
nav_order: 2
---

# HTML Basic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
 
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


### A Simple Document Shape

![](https://gekdev.github.io/assets/images/noname01.png)

* &#60;!DOCTYPE html&#62;

    declaration defines this document to be HTML5 <br>
    
	This represents the document type, and helps browsers to display web pages correctly<br>
    
    It must only appear once, at the top of the page (before any HTML tags)
    
* &#60;html&#62; 

    the root element of an HTML page

* &#60;head&#62;

    meta information about the document (contain metadata)

* &#60;title&#62; 
    
    specifies a title for the document

* &#60;body&#62; 

    contains the visible page content

---

## Elements

### Element Basic Form
    
HTML elements(tags) normally come in pairs

```html
<p> {start tag(opening tag)} </p>{end tag(closing tag)}
```

The end tag is written like the start tag, but with a forward slash inserted before the tag name

### Features of Elements

* can be nasted

* never skip the end tag

* not case sensitive, 하지만 소문자 권장

### Empty tag

HTML tags with no content. Empty tags do not have an end tag, such as the `<br>` element

### Basic Elements

* &#60;h1&#62; 

    defines a large heading

* &#60;p&#62; 

    defines a paragraph

* &#60;a&#62; 

    defines a link, link's destination specified in the href attribute

* &#60;img&#62; 

    defines a images, The source file (src), alternative text (alt), width, and height are provided as attributes

---

## Attribute

### Attribute Feature

&#9656; All HTML elements can have attributes

&#9656; Attributes provide additional information about an element

&#9656; Attributes are always specified in the start tag

&#9656; Attributes usually come in name/value pairs like: name="value"

&#9656; attribute값 안에 불필요한 공백이 들어가면 오류 &#8594; but 파일 이름 등 필수로 들어가는 경우 “”로 묶어야지 오류가 안남

### Basic Attributes

* href : link address is specified in the href attribute

* src : filename of the image source = 주소

* alt : The alt attribute specifies an alternative text to be used, if an image cannot be displayed. can be read by screen readers

* style : specify the styling of an element, like color, font, size etc.

* lang : important for accessibility applications (screen readers) and search engines

* title : displayed as a tooltip when you mouse over

* [view more...](https://www.w3schools.com/tags/ref_attributes.asp)

Single or Double Quotes?
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
Double quotes around attribute values are the most common in HTML, but single quotes can also be used.
</div>

---

## Comments

### Basic Comments

**주석**

&#9656; 여러줄도 가능

<div class="code-example" markdown="1">
<!-- This is a comment --> This is a comment
</div>
```html
<!-- This is a comment --> This is a comment
```

---

## Setting Environment

### Web Browser

* Chrome

    확장자 도구 : web developer, outline

### Text editor

* 대표적인 에디터 : Brackets, Atom, Visual Studio Code, Eclipse

* 확장기능 관리자

    &#9656; Emmet : html 태그 자동완성
    
    &nbsp;&nbsp;&nbsp; [Emmet 명령어 더 알아보기](https://velog.io/@aepee/Emmet-%EC%82%AC%EC%9A%A9%EB%B2%95)

    &#9656; tree icons : 아이콘 이미지

    &#9656; color highlighter : 색 표시

    &#9656; custom work : 파일 보여줌


학원에서 주로 쓰는 툴 Eclipse, 처음 설정하는 법
{: .label .mt-2}
<div class="code-example" markdown="1">

1. Window preferences > general > appearance > colors and fonts > basic > text editor... & text font 폰트를 D2Coding ligature 으로 바꾸고 (코딩할때 좋은 폰트)

2. Window preferences > general > workspace utf-8로 바꾸기

3. Window preferences > web > CSS, HTML, JSP files  encoding 모두 utf-8로 바꾸기

...

help > eclipse marketplace 에서 emmet 설치
</div>

### Web Accessibility Check

* [에이쿨첵!](https://software.naver.com/software/summary.nhn?softwareId=GWS_000915#) : 웹 접근성 솔루션 검사 프로그램
    
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

