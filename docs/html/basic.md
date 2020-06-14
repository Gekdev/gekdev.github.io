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
    블록테그지만 다른 blogtag가 들어오면 안됨
    </div>

* Links (a)

    **링크**
    
    &#9656; href에 주소나 북마크 하고싶은곳의 id value로 연결할 수 있음
    
    ```html
    <a href="#a"></a>
    ...
    
    <div id="a"></div>
    ```
    
    target attribute
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
    
* Images  (img)
    
    **이미지**
    
    Attribute : The source file (src), alternative text (alt), width, and height

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
    
    이미지 투명도 조절 : opacity: 0.3;

#### Reference
{: .no_toc}
    [w3schools](https://www.w3schools.com/html/html_images_imagemap.asp)

*

*

*

## HTML Table
---
## HTML Form
---
## HTML Media
---
## HTML Quotations
---
## HTML Computercode
---
## HTML Graphics
---
## HTML Comments

---

## HTML Attributes

---

## HTML API





    

