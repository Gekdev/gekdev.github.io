---
layout: default
title: Basic
parent: HTML
nav_order: 2
---

# Basic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## HTML Basic Elements

### Head elements

* title 

	**a title in the browser tab**
    
	&#9656; provides a title for the page when it is added to favorites
	
    &#9656; displays a title for the page in search engine results

* style 

	**style information for a single HTML page**

* link element

	**link to external style sheets**
    
	`<link rel="stylesheet" href="mystyle.css">`

* meta

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

* script
    
    **define client-side JavaScripts**
    
* base
    
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
    
### Body elements

* Headings (h1~h6)

    **제목**
    
    &#9656; `<h1>`이 제일 중요한 헤딩, `<h6>` 제일 중요하지 않은 제목
    
    &#9656; Search engines use the headings to index the structure and content of your web pages.
    
    &#9656; It is important to use headings to show the document structure.
    
    !Note
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    Use HTML headings for headings only. Don't use headings to make text BIG or bold.
    </div>

* Paragraphs (p)

    **단락**

    !Note
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    블록테그지만 다른 블록테그가 들어오면 안됨
    </div>

* Links (a)

    **링크**
    
    &#9656; href에 걸 수 있는것들 (상대경로가 제일 좋음)
    {: .mt-3}
    
    * Web pages
    
    * Images
    
    * Style sheets
    
    * JavaScripts
    
    * 북마크
    
    &#9656; 북마크 하고싶은곳의 id value로 연결할 수 있음
    
    ```html
    <a href="#a"></a>
    ...
    
    <div id="a"></div>
    ```
    
    target attr
    {: .mt-3}
    
    * _blank : Opens the linked document in a new window or tab
	* _self : Opens the linked document in the same window/tab as it was clicked (default)
    * _parent : Opens the linked document in the parent frame
    * _top : Opens the linked document in the full body of the window
    * framename : Opens the linked document in a named frame

    !Note
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    A link does not have to be text. It can be an image or any other HTML element
    </div>
    
* Images (img)
    
    **이미지**
    
    &#9656; attr : The source file (src), alternative text (alt), width, and height
    
    &#9656; 이미지 투명도 조절 : opacity: 0.3;

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

    #### Reference
    {: .no_toc}
    [w3schools](https://www.w3schools.com/html/html_images_imagemap.asp)

* Picture

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
    
* Buttons

* Lists

    &#9656; list is block, so float attribute is possible
    
    * ordered list
    * unordered list
    * dl
    
* Horizontal Rules (hr)
    
    **가로 구분선**

* Formatting Elements
    ```html
    <b>  Bold text
    <strong> - Important text
    <i> - Italic text
    <em> - Emphasized text
    <mark> - Marked text
    <small> - Small text
    <del> - Deleted text
    <ins> - Inserted text
    <sub> - Subscript text
    <sup> - Superscript text
    ```
    
* iframe

    inframe tag안에 또 들어갈 수 있음
	attribute:  src width height style="border:none;
	Use the height and width attributes to specify the size of the iframe.
	target값 name 따라서 가거나 blank, self, parent, top 등 다양하게 갈 수 있음

	Iframe - Target for a Link
	<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
	<p><a href="https://www.w3schools.com" target="iframe_a">W3Schools.com</a></p>

### HTML Media
* video audio, object, embed

<video width="320" height="240" controls autoplay loop> 
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
Your browser does not support the video tag.
</video>

<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>
<object width="400" height="50" data="bookmark.swf"></object>

<embed width="400" height="50" src="bookmark.swf">

* Canvas
What is HTML Canvas?
The HTML <canvas> element is used to draw graphics, on the fly, via JavaScript.

The <canvas> element is only a container for graphics. You must use JavaScript to actually draw the graphics.

<canvas id="myCanvas" width="200" height="100" style="border:1px solid #000000;">
</canvas>

#### Reference
{: .no_toc}
[w3schools](https://www.w3schools.com/graphics/canvas_intro.asp)

* Youtube
[w3schools](https://www.w3schools.com/html/html_youtube.asp)
[cdmanii](https://cdmanii.com/3392)

### HTML Quotations

```html
<q> for Short Quotations =" "
<blockquote> for Quotations = indent
<abbr> for Abbreviations = title, .....
<address> for Contact Information = italic
<cite> for Work Title = italic
    The HTML <cite> element defines the title of a work.
    Browsers usually display <cite> elements in italic.
<bdo> for Bi-Directional Override
<bdo> element defines bi-directional override.
```

### HTML Computercode

* code

    **Computer Code**
    The HTML <code> element defines a fragment of computer code.
    Text surrounded by <code> tags is typically displayed in a monospace font: 
    <code>
    x = 5;<br>
    y = 6;<br>
    z = x + y;
    </code>

    Notice that the <code> element does not preserve extra whitespace and line-breaks.
    To fix this, you can put the <code> element inside a <pre> element:

* kbd

    **Keyboard Input**
    
    The HTML <kbd> element represents user input, like keyboard input or voice commands.
    Text surrounded by <samp> tags is typically displayed in a monospace font:
    <p>Save the document by pressing <kbd>Ctrl + S</kbd></p>

* samp

    **Program Output**
    
    The HTML <samp> element represents output from a program or computing system.
    Text surrounded by <samp> tags is typically displayed in a monospace font:
    <p>If you input wrong value, the program will return <samp>Error!</samp></p>

* var

    **Variables**
    
    The HTML <var> element defines a variable.
    The variable could be a variable in a mathematical expression or a variable in programming context:
    Einstein wrote: <var>E</var> = <var>mc</var><sup>2</sup>.


## HTML Table
---
## HTML Form
---

## HTML Semantic

### What is Semantic?

**문서의 구조와 의미를 표현하는 태그**

### HTML Layout Elements

header	페이지나 섹션의 머리말을 표현, section이나 article 태그 내에도 사용됨
nav	하이퍼링크들을 모아논 특별한 섹션, 목차
section	문서의 장 혹은 절을 구성하는 역할, h1~6로 섹션의 주제를 기재하는 것이 바람직 
article	본문과 연결되어 있는 독립적인 콘텐츠, section의 보조적인 기사
aside	흐름에 벗어나 짤막하게 곁들이는 관련 기사.. 
footer	꼬리말 영역을 표시하는 태그 

###

---

## HTML Graphics
---
## HTML Comments

---

## HTML Attributes

### 기본특징

&#9656; Attributes provide additional information about an element
&#9656; Attributes are always specified in the start tag
&#9656; Attributes usually come in name/value pairs like: name="value"

### Basic Attributes

* href : link address is specified in the href attribute

* src : filename of the image source = 주소

* alt : The alt attribute specifies an alternative text to be used, if an image cannot be displayed. **can be read by screen readers**

* style : specify the styling of an element, like color, font, size etc.

* lang : declared in the `<html>` tag.
    **important for accessibility applications (screen readers) and search engines**

* title : displayed as a tooltip when you mouse over

* [view more...](https://www.w3schools.com/tags/ref_attributes.asp)

Single or Double Quotes?
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
Double quotes around attribute values are the most common in HTML, but single quotes can also be used.
</div>

---

## HTML API





    

