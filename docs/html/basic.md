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
    