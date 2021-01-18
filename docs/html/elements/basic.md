---
layout: default
title: Basic
parent: Elements
grand_parent: HTML
nav_order: 1
--- 

# Basic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Head elements

### &#60;title&#62;

**a title in the browser tab**

&#9656; provides a title for the page when it is added to favorites

&#9656; displays a title for the page in search engine results

```html
<title>Document</title>
```

### &#60;style&#62;

**style information for a single HTML page**

```html
<style>
    .hello{
        margin: 0;
    }
</style>
```

### &#60;link&#62;

**link to external style sheets**

```html
<link rel="stylesheet" href="mystyle.css">
```

### &#60;meta&#62;

**specify which character set is used, page description, keywords, author, and other metadata**

used by browsers (how to display content), by search engines (keywords), and other web services

```html
<meta charset="UTF-8">
<meta name=“description” content=“생활코딩의 소개자료” > 
<meta name="keywords" content="HTML, CSS, XML, JavaScript"> // 문서를 정의하는 단어들(키워드)
<meta name="author" content="John Doe">
<meta http-equiv="refresh" content="30"> // 30초 간격으로 새로고침됨
```

Setting The Viewport
{: .label .mt-2}

<div class="code-example" markdown="1">
The viewport is the user's visible area of a web page. It varies with the device, and will be smaller on a mobile phone than on a computer screen.

* name="viewport" : browser instructions on how to control the page's dimensions and scaling

* width=device-width : sets the width of the page to follow the screen-width

* initial-scale=1.0 : sets the initial zoom level when the page is first loaded by the browser

</div>
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

[더 자세히 알아보기](https://gekdev.github.io/docs/html/advanced/meta/#meta-element)

### &#60;script&#62;

**define client-side JavaScripts**

```html
<script src="demo.js"></script>
  
or
  
<script>
    window.alert("demo")
</script>
```
    
### &#60;base&#62;
    
**specifies the base URL and base target for all relative URLs in a page**

```html
<base href="https://www.w3schools.com/images/" target="_blank">
```

Omitting html, head and body tag?
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
According to the HTML5 standard; the <html>, the <body>, and the <head> tag can be omitted.
<br><br>
W3Schools does not recommend omitting the <html> and <body> tags. Omitting these tags can crash DOM or XML software and produce errors in older browsers (IE9).
</div>
    
---

## Body elements

### &#60;h1&#62;~&#60;h6&#62;

**제목**

&#9656; `<h1>`이 제일 중요한 헤딩, `<h6>` 제일 중요하지 않은 제목

&#9656; Search engines use the headings to index the structure and content of your web pages.

&#9656; It is important to use headings to show the document structure.

<div class="code-example" markdown="1">
<h1>h1</h1>
<h2>h2</h2>
<h3>h3</h3>
<h4>h4</h4>
<h5>h5</h5>
<h6>h6</h6>
</div>
```html
<h1>h1</h1>
<h2>h2</h2>
<h3>h3</h3>
<h4>h4</h4>
<h5>h5</h5>
<h6>h6</h6>
```

!Note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
Use HTML headings for headings only. Don't use headings to make text BIG or bold.
</div>

### &#60;p&#62;

**Paragraphs**

<div class="code-example" markdown="1">
<p>This is paragraph tag</p>
</div>
```html
<p>This is paragraph tag</p>
```

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
블록테그지만 다른 블록테그가 들어오면 안됨
</div>

### &#60;hr&#62;

**Horizontal Rules**

attribute : width size color align

<div class="code-example" markdown="1">
<hr>
<img src="https://gekdev.github.io/assets/images/html_basic_hr.jpg" alt="예시">
</div>
```html
<hr>
<hr width="200" size="30" color="lightblue" align="center"/>
<hr width="200" size="30" color="lightyellow" align="left"/>
<hr width="200" size="30" color="lightgreen" align="right"/>
```

### &#60;br&#62;

**single line break**

empty tag (has no end tag)

<div class="code-example" markdown="1">
<br>
</div>
```html
<br>
```

### &#60;a&#62;

**링크**

<div class="code-example" markdown="1">
<a href="https://gekdev.github.io/" target="_blank">anchor tag</a>
</div>
```html
<a href="https://gekdev.github.io/" target="_blank">anchor tag</a>
```

대표적으로 target, href, download 속성이 있음

* target

    **페이지를 어떤 형식으로 오픈할건지** 선택
    
    value
    {: .label .label-red}
    <div class="code-example" markdown="1">
    * _blank : Opens the linked document in a new window or tab

    * _self : Opens the linked document in the same window/tab as it was clicked (default)

    * _parent : Opens the linked document in the parent frame

    * _top : Opens the linked document in the full body of the window(윈도우 페이지)

    * framename : Opens the linked document in a named frame (target="사용자 지정")
    </div>  

* href

    **어떤 데이터를 제공할지** 선택
    
    value
    {: .label .label-red}
    <div class="code-example" markdown="1">
    * Address 

        &#9656; 절대주소는 로고에 사용, 호스팅 주소부터 끌고온다

        &#9656; 상대경로가 가장 좋은 방법!
        {: .text-blue-000}
        
        <a href="../../../index.md">메인페이지</a>
        
    * mail 

        &#9656; href="mailto:moliuo@naver.com"

    * number 

        &#9656; href="tel:010-0000-0000"

    * Web pages

    * Images

    * Style sheets

    * JavaScripts

    * 북마크

        &#9656; 북마크 하고싶은곳의 id value로 연결할 수 있음

        &#9656; 다른 파일의 id는 {href="파일명(주소)#앵커이름"}으로 연결함 

        ```html
        <a href="#a"></a>
        ...

        <div id="a"></div>
        ```
    </div> 

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
A link does not have to be text. It can be an image or any other HTML element
</div>

* download 

    데이터를 다운로드 할 때 사용, href에 다운할 파일 위치

### &#60;img&#62;

**이미지**

<div class="code-example" markdown="1">
<img src="https://gekdev.github.io/assets/images/cat1.jpg" alt="고양이">
</div>
```html
<img src="주소" alt="시각장애우를 위해 꼭 써야하는 속성">
```

&#9656; attribute : The source file (src), alternative text (alt), width, and height

&#9656; 이미지 투명도 조절 : opacity: 0.3;

&#9656; map element 활용할 수 있음, [W3School Example](https://www.w3schools.com/html/html_images_imagemap.asp)

페이지를 이동하는 이미지맵
{: .label .mt-3 .mb-2}
```html
<img src="workplace.jpg" alt="Workplace" usemap="#workmap">

<map name="workmap">
  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
  <area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">
</map>
```

자바스크립트를 활용한 이미지맵
{: .label .mt-3 .mb-2}
```html
<img src="workplace.jpg" alt="Workplace" usemap="#workmap" width="400" height="379">

<map name="workmap">
  <area shape="circle" coords="337,300,44" onclick="myFunction()">
</map>

<script>
function myFunction() {
  alert("You clicked the coffee cup!");
}
</script>
```

### &#60;picture&#62;

**이미지**

add more flexibility when specifying image resources

&#9656; contains a number of `<source>` elements, each referring to different image sources. 

&#9656; browser can choose the image that best fits the current view and/or device.

```html
<picture>
  <source media="(min-width: 650px)" srcset="img_food.jpg">
  <source media="(min-width: 465px)" srcset="img_car.jpg">
  <img src="img_girl.jpg">
</picture>
```

When to use the Picture Element
{: .label .mt-3}
<div class="code-example" markdown="1">
1. Bandwidth <br>
2. Format Support (you can add images of all formats, and the browser will use the first format it recognizes and ignore any of the following.)
</div>

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
Always specify an img element as the last child element of the picture element. The img element is used by browsers that do not support the picture element, or if none of the source tags matched.
</div>

### &#60;text formattings&#62;

| description       | tag                        | shape                    |
|:------------------|:---------------------------|:-------------------------|
| Bold text         | `<b>b</b>`                 | <b>b</b>                 |
| Important text    | `<strong>strong</strong>`  | <strong>strong</strong>  |
| Italic text       | `<i>i</i>`                 | <i>i</i>                 |
| Emphasized text   | `<em>em</em>`              | <em>em</em>              |
| Deleted text      | `<del>del</del>`           | <del>del</del>           |
| Inserted text     | `<ins>ins</ins>`           | <ins>ins</ins>           |
| Subscript text    | `<sub>sub</sub>`           | <sub>sub</sub>X          |
| Superscript text  | `<sup>sup</sup>`           | <sup>sup</sup>X          |
| Marked text       | `<mark>mark</mark>`        | <mark>mark</mark>        |


    

