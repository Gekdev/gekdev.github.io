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

## Basic Document

### A Simple Document Shape

![](https://gekdev.github.io/assets/images/noname01.png)

* `<!DOCTYPE html>` declaration defines this document to be HTML5 <br>
	This represents the document type, and helps browsers to display web pages correctly.
    
* `<html>` element is the root element of an HTML page

* `<head>` element contains meta information about the document (contain metadata)

* `<title>` element specifies a title for the document

* `<body>` element contains the visible page content

* `<h1>` element defines a large heading

* `<p>` element defines a paragraph

---

## Attribute

### Attribute Feature

&#9656; All HTML elements can have attributes

&#9656; Attributes provide additional information about an element

&#9656; Attributes are always specified in the start tag

&#9656; Attributes usually come in name/value pairs like: name="value"

&#9656; attribute값 안에 불필요한 공백이 들어가면 오류 <br>
        &#8594; but 파일 이름 등 필수로 들어가는 경우 “”로 묶어야지 오류가 안남

### Basic Attributes

* href : link address is specified in the href attribute

* src : filename of the image source = 주소

* alt : The alt attribute specifies an alternative text to be used, if an image cannot be displayed. **can be read by screen readers**

* style : specify the styling of an element, like color, font, size etc.

* lang : **important for accessibility applications (screen readers) and search engines**

* **title** : displayed as a tooltip when you mouse over

* [view more...](https://www.w3schools.com/tags/ref_attributes.asp)


Single or Double Quotes?
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
Double quotes around attribute values are the most common in HTML, but single quotes can also be used.
</div>

---

## Comments

### Basic Comments

**주석달기**

&#8594; 여러줄도 가능

<div class="code-example" markdown="1">
<!-- This is a comment --> This is a comment
</div>
```html
<!-- This is a comment --> This is a comment
```

---

## External Sources

### Icon

* [Font Awesome](https://fontawesome.com/) 
    
    ```html
    <script src="https://kit.fontawesome.com/yourcode.js"></script>
    ```
    &#8594; 가입하면 개인별로 스크립트 코드를 부여함

* [Bootstrap Icons](https://icons.getbootstrap.com/) 

    ```html
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    ```

* [Google Icons](https://material.io/resources/icons/?style=baseline) 

    ```html
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
    ```
___

## Special Characters

### Character Entities

&#9656; 특수문자를 코드로 사용해서 작성해야 마크업 언어가 꼬이지 않음

<span class="fs-2">
[특수문자 사이트](https://dev.w3.org/html5/html-author/charref){: .btn  .btn-outline .mt-2}
</span>

### Emoji Characters

**Emojis are characters from the UTF-8 alphabet**

<div class="code-example" markdown="1">
😄 is 128516
😍 is 128525
💗 is 128151
</div>
```html
😄 is 128516
😍 is 128525
💗 is 128151
```

<span class="fs-2">
[이모지 더보기](https://www.w3schools.com/charsets/ref_emoji.asp){: .btn  .btn-outline .mt-2}
</span>
