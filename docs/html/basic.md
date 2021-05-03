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
{: .label .label-yellow .mt-3}
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
