---
layout: default
title: Basic Elements
parent: HTML
nav_order: 3
---

# Basic Elements
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

### &#60;style&#62;

**style information for a single HTML page**

### &#60;link&#62;

**link to external style sheets**

`<link rel="stylesheet" href="mystyle.css">`

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
{: .label .mt-3}

<div class="code-example" markdown="1">
The viewport is the user's visible area of a web page. It varies with the device, and will be smaller on a mobile phone than on a computer screen.

* name="viewport" : browser instructions on how to control the page's dimensions and scaling

* width=device-width : sets the width of the page to follow the screen-width

* initial-scale=1.0 : sets the initial zoom level when the page is first loaded by the browser

</div>
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### &#60;script&#62;

**define client-side JavaScripts**
    
### &#60;base&#62;
    
**specifies the base URL and base target for all relative URLs in a page**

```html
<base href="https://www.w3schools.com/images/" target="_blank">
```

Omitting html, head and body tag?
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
According to the HTML5 standard; the <html>, the <body>, and the <head> tag can be omitted.
<br><br>
W3Schools does not recommend omitting the <html> and <body> tags. Omitting these tags can crash DOM or XML software and produce errors in older browsers (IE9).
</div>
    
## Body elements

### Headings (&#60;h1&#62;~&#60;h6&#62;)

**제목**

&#9656; `<h1>`이 제일 중요한 헤딩, `<h6>` 제일 중요하지 않은 제목

&#9656; Search engines use the headings to index the structure and content of your web pages.

&#9656; It is important to use headings to show the document structure.

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
Use HTML headings for headings only. Don't use headings to make text BIG or bold.
</div>

### Paragraphs (&#60;p&#62;)

**단락**

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
블록테그지만 다른 블록테그가 들어오면 안됨
</div>

### Horizontal Rules (&#60;hr&#62;)

**가로 구분선**

### Line breaks (&#60;br&#62;)

**single line break**

empty tag(has no end tag)

### Text Formatting

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

### Links (&#60;a&#62;)

**링크**

* target attr의 종류
    <div class="code-example" markdown="1">
    * _blank : Opens the linked document in a new window or tab

    * _self : Opens the linked document in the same window/tab as it was clicked (default)

    * _parent : Opens the linked document in the parent frame

    * _top : Opens the linked document in the full body of the window

    * framename : Opens the linked document in a named frame
    </div>

* href 링크 종류
    // 상대경로가 가장 좋은 방법!
    {: .text-blue-000}
    
    <div class="code-example" markdown="1">
    * Web pages

    * Images

    * Style sheets

    * JavaScripts

    * 북마크

        북마크 하고싶은곳의 id value로 연결할 수 있음

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

### Images (img)

**이미지**

&#9656; attr : The source file (src), alternative text (alt), width, and height

&#9656; 이미지 투명도 조절 : opacity: 0.3;

&#9656; map element 활용할 수 있음 [w3schools](https://www.w3schools.com/html/html_images_imagemap.asp)

페이지를 이동하는 이미지맵
{: .label .mt-3}
```html
<img src="workplace.jpg" alt="Workplace" usemap="#workmap">

<map name="workmap">
  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
  <area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">
</map>
```

자바스크립트를 활용한 이미지맵
{: .label .mt-3}
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

### Picture

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

## Table elements

&#9656; 기본형식 : table > tr(열) > td

&#9656; 문법 []안에는 속성값, >뒤에는 하위값, *개수, +동일 항목 더하기

```html
<table style="width:100%">
<tr>
<th>Firstname</th>
<th>Lastname</th>
<th>Age</th>
</tr>
<tr>
<td>Jill</td>
<td>Smith</td>
<td>50</td>
</tr>
<tr>
<td>Eve</td>
<td>Jackson</td>
<td>94</td>
</tr>
</table>
```

### table 

**표**

&#9656; table attr : border="" cellpadding="" cellspacing="" bgcolor="" style="margin" width="" 

### table row (tr)

**row(열)**

&#9656; tr attr : height="" bgcolor="" align="" style="font-size:"

### th

**table header**

&#9656; td attr과 동일

### td

**table data/cell**

&#9656; td attr : width="" height="" bgcolor="" **align="left center right" valign="top, middle bottom" colspan="" rowspan=""** style="color:"

### caption

**caption to a table**

Note:
{: .label .label-yellow .mt-3}
The caption tag must be inserted immediately after the table tag

## List elements

&#9656; list is block, so float attribute is possible

### Ordered list(ol)
### Unordered list(ul)
### Description Lists(dl)
* the `<dl>` tag defines the description list 
* the `<dt>` tag defines the term (name)
* the `<dd>` tag describes each term

## iframe

**display a web page within a web page**

&#9656; attribute: src width height style="border:none;

&#9656; Use the height and width attributes to specify the size of the iframe.

&#9656; target값 name 따라서 가거나 blank, self, parent, top 등 다양하게 갈 수 있음

&#9656; inframe 서로 들어갈 수 있음

> &#8594; a링크로 주소를 찍거나, a 태그 타겟 없이 iframe src만으로도 다른 페이지로 이동가능

```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="https://www.w3schools.com" target="iframe_a">W3Schools.com</a></p>
```

## Media elements

* video 

**show a video on a web page**

&#9656; attr : autoplay, controls, loop

```html
<video width="320" height="240" controls autoplay loop> 
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
Your browser does not support the video tag.
</video>
```

* audio 

**play an audio file on a web page**

```html
<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>
```

* object, embed

**embedded object within an HTML document**

&#9656; supported by all browsers.

&#9656; It was designed to embed plug-ins

```html
<object width="400" height="50" data="bookmark.html"></object>
<object data="audi.jpeg"></object>
---
<embed width="400" height="50" src="bookmark.swf">
```

* Youtube

#### Reference
[w3schools](https://www.w3schools.com/html/html_youtube.asp)<br>
[cdmanii](https://cdmanii.com/3392)

### Quotation and Citation

| description                   | tag                                    | shape                                |
|:------------------------------|:---------------------------------------|:-------------------------------------|
| Short Quotations (" ")        | `<q>q</q>`                             | <q>q</q>                             |
| Quotations (indent)           | `<blockquote>blockquote</blockquote>`  | <blockquote>blockquote</blockquote>  |
| Abbreviations (.....)         | `<abbr title="abbr">abbr</abbr>`       | <abbr title="abbr">abbr</abbr>       |
| Contact Information (italic)  | `<address>address</address>`           | <address>address</address>           |
| Work Title (italic)           | `<cite>cite</cite>`                    | <cite>cite</cite>                    |
| bi-directional override       | `<bdo dir="rtl">bdo</bdo>`             | <bdo dir="rtl">bdo</bdo>             |
{: .mt-3}


## Computercode

### code

**a fragment of computer code**

typically displayed in a monospace font
<div class="code-example" markdown="1">
<code>
x = 5;<br>
y = 6;<br>
z = x + y;
</code>
</div>

Notice
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
that the <code> element does not preserve extra whitespace and line-breaks.
To fix this, you can put the <code> element inside a <pre> element
</div>
```html
that the <code> element does not preserve extra whitespace and line-breaks.
To fix this, you can put the <code> element inside a <pre> element
```

### kbd

**Keyboard Input**

**user input, like keyboard input or voice commands**

typically displayed in a monospace font
<div class="code-example" markdown="1">
<p>Save the document by pressing <kbd>Ctrl + S</kbd></p>
</div>
```html
<p>Save the document by pressing <kbd>Ctrl + S</kbd></p>
```

### samp

**Program Output**

**output from a program or computing system**

typically displayed in a monospace font

<div class="code-example" markdown="1">
<p>If you input wrong value, the program will return <samp>Error!</samp></p>
</div>
```html
<p>If you input wrong value, the program will return <samp>Error!</samp></p>
```

### var

**Variables**

The variable could be a variable in a mathematical expression or a variable in programming context:
<div class="code-example" markdown="1">
Einstein wrote: <var>E</var> = <var>mc</var><sup>2</sup>
</div>
```html
Einstein wrote: <var>E</var> = <var>mc</var><sup>2</sup>
```

## Block and Inline

### Block

**starts on a new line and takes up the full width available**

(stretches out to the left and right as far as it can)

```html
<address> <article> <aside> <blockquote> <canvas> <dd> <div> 
<dl> <dt> <fieldset> <figcaption> <figure> <footer> <form> 
<h1>-<h6> <header> <hr> <li> <main> <nav> <noscript> <ol> 
<p> <pre> <section> <table> <tfoot> <ul> <video>
```

### Inline

**does not start on a new line and only takes up as much width as necessary**

```html
<a> <abbr> <acronym> <b> <bdo> <big> <br> <button> <cite> <code> 
<dfn> <em> <i> <img> <input> <kbd> <label> <map> <object> <output> 
<q> <samp> script <select> <small> <span> <strong> <sub> <sup> 
<textarea> <time> <tt> <var>
```



    

