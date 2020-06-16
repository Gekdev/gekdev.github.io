---
layout: default
title: Semantic
parent: HTML
nav_order: 7
---

# Semantic
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

* link 

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
    
* Horizontal Rules (hr)
    
    **가로 구분선**
    
* Line breaks (br)
    
    **single line break**
    
    empty tag(has no end tag)

* Text Formatting

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
    {: .mt-3}

* Links (a)

    **링크**
    
    &#9656; target attr의 종류
    <div class="code-example" markdown="1">
    * _blank : Opens the linked document in a new window or tab

    * _self : Opens the linked document in the same window/tab as it was clicked (default)

    * _parent : Opens the linked document in the parent frame

    * _top : Opens the linked document in the full body of the window

    * framename : Opens the linked document in a named frame
    </div>
    
    href 링크 종류
    {: .label .mt-3}
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
    
    // 상대경로가 가장 좋은 방법!
    {: .text-blue-000}
    
    !Note
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    A link does not have to be text. It can be an image or any other HTML element
    </div>
    
* Images (img)
    
    **이미지**
    
    &#9656; attr : The source file (src), alternative text (alt), width, and height
    
    &#9656; 이미지 투명도 조절 : opacity: 0.3;

    &#9656; map element 활용할 수 있음

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
    
    #### 참고자료
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
    
### Table

&#9656; 기본형식 : table > tr(열) > td

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

&#9656; 문법 []안에는 속성값, >뒤에는 하위값, *개수, +동일 항목 더하기

* table tag 

    **표**
    
    &#9656; table attr : border="" cellpadding="" cellspacing="" bgcolor="" style="margin" width="" 
    
* tr 

    **row(열)**
    
    &#9656; tr attr : height="" bgcolor="" align="" style="font-size:"

* th

    **table header**
    
    &#9656; td attr과 동일

* td

    **table data/cell**
    
    &#9656; td attr : width="" height="" bgcolor="" **align="left center right" valign="top, middle bottom" colspan="" rowspan=""** style="color:"

* caption

    **caption to a table**
    
    Note:
    {: .label .label-yellow .mt-3}
    The caption tag must be inserted immediately after the table tag

### Lists

&#9656; list is block, so float attribute is possible

* Ordered list(ol)
* Unordered list(ul)
* Description Lists(dl)
    * The <dl> tag defines the description list 
    * the <dt> tag defines the term (name)
    * the <dd> tag describes each term:

### iframe

**display a web page within a web page**

&#9656; attr:  src width height style="border:none;

&#9656; inframe 서로 들어갈 수 있음
    
> &#8594; a링크로 주소를 찍거나, a 태그 타겟 없이 iframe src만으로도 다른 페이지로 이동가능

&#9656; Use the height and width attributes to specify the size of the iframe.

&#9656; target값 name 따라서 가거나 blank, self, parent, top 등 다양하게 갈 수 있음

<div class="code-example" markdown="1">
<iframe src="introduction.md" name="iframe_a"></iframe>
<p><a href="basic.md" target="iframe_a">Github</a></p>
</div>
```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="https://www.w3schools.com" target="iframe_a">W3Schools.com</a></p>
```

### Media

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


### Computercode

* code

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

* kbd

    **Keyboard Input**
    
    **user input, like keyboard input or voice commands**
    
    typically displayed in a monospace font
    <div class="code-example" markdown="1">
    <p>Save the document by pressing <kbd>Ctrl + S</kbd></p>
    </div>
    ```html
    <p>Save the document by pressing <kbd>Ctrl + S</kbd></p>
    ```
    
* samp

    **Program Output**
    
    **output from a program or computing system**
    
    typically displayed in a monospace font
    
    <div class="code-example" markdown="1">
    <p>If you input wrong value, the program will return <samp>Error!</samp></p>
    </div>
    ```html
    <p>If you input wrong value, the program will return <samp>Error!</samp></p>
    ```

* var

    **Variables**
    
    The variable could be a variable in a mathematical expression or a variable in programming context:
    <div class="code-example" markdown="1">
    Einstein wrote: <var>E</var> = <var>mc</var><sup>2</sup>
    </div>
    ```html
    Einstein wrote: <var>E</var> = <var>mc</var><sup>2</sup>
    ```
    
### Block and Inline

* Block

    **starts on a new line and takes up the full width available**
    
    (stretches out to the left and right as far as it can)

    ```html
    <address> <article> <aside> <blockquote> <canvas> <dd> <div> 
    <dl> <dt> <fieldset> <figcaption> <figure> <footer> <form> 
    <h1>-<h6> <header> <hr> <li> <main> <nav> <noscript> <ol> 
    <p> <pre> <section> <table> <tfoot> <ul> <video>
    ```

* Inline

    **does not start on a new line and only takes up as much width as necessary**
    
    ```html
    <a> <abbr> <acronym> <b> <bdo> <big> <br> <button> <cite> <code> 
    <dfn> <em> <i> <img> <input> <kbd> <label> <map> <object> <output> 
    <q> <samp> script <select> <small> <span> <strong> <sub> <sup> 
    <textarea> <time> <tt> <var>
    ```
    
---

## HTML Form elements

### Form 

**collect user input**

그냥 데이터만 서버에 전송해야 할때 : input type=“hidden” name=“hide” value=“hey”

* form attribute

    &#9656; action : 웹 서버 응용 프로그램의 url
    
    &#9656; enctype : 인코딩 타입 (데이터를 전송할 때 암호과 방식 지정)
        
    &#9656; name : 폼 이름
    
    &#9656; target : 윈도우 이름 (응용프로그램으로부터 받은 데이터를 출력할 윈도우 이름)
    
    &#9656; method : GET/POST (폼 데이터를 웹 서버에 전송하는 방식, default= get)

    Notes on GET
    {: .label .mt-3}
    <div class="code-example" markdown="1">
	**the submitted form data will be visible in the page address field**

	&#9656; Appends form-data into the URL in name/value pairs
    
	&#9656; The length of a URL is limited (2048 characters)
    
	&#9656; Never use GET to send sensitive data! (will be visible in the URL)
    
	&#9656; Useful for form submissions where a user wants to bookmark the result
    
	&#9656; GET is better for non-secure data, like query strings in Google
    </div>

	Notes on POST
    {: .label .mt-3}
    <div class="code-example" markdown="1">
    **Always use POST if the form data contains sensitive or personal information. 
    
    The POST method does not display the submitted form data in the page address field**
    
	&#9656; POST has no size limitations, and can be used to send large amounts of data.
    
	&#9656; Form submissions with POST cannot be bookmarked
    </div>

### input

**값을 입력받는 요소**

&#9656; 기본형식
```html
<input type="text" title="아이디 입력" />
```
&#9656; 거의 모든 방식에서 method=“post” 와 enctype=“multipart/form-data”>를 씀 name이 없으면 에러가 뜸

* Name Attr : Each input field must have a name attribute to be submitted.
    
    > 생략될경우 submit 했을때 값을 받을수가 없음(not be sent at all)

* Type Attr : Each input field must have a name attribute to be submitted.(default= text)

    <div class="code-example" markdown="1">
    <input type="button">

    <input type="checkbox">

    <input type="color">

    <input type="date">

    <input type="datetime-local">

    <input type="email">

    <input type="file">

    <input type="hidden">

    <input type="image" src="">

    <input type="month">

    <input type="number">

    <input type="password">

    <input type="radio">

    <input type="range">

    <input type="reset">

    <input type="search">

    <input type="submit">

    <input type="tel">

    <input type="text">

    <input type="time">

    <input type="url">

    <input type="week">
    </div>
    ```html
    <input type="button">

    <input type="checkbox">

    <input type="color">

    <input type="date">

    <input type="datetime-local">

    <input type="email">

    <input type="file">

    <input type="hidden">

    <input type="image" src="">

    <input type="month">

    <input type="number">

    <input type="password">

    <input type="radio">

    <input type="range">

    <input type="reset">

    <input type="search">

    <input type="submit">

    <input type="tel">

    <input type="text">

    <input type="time">

    <input type="url">

    <input type="week">
    ```

    새로 생긴것
    {: .label .mt-3}
    <div class="code-example" markdown="1">
    <input type="color">
    
    Enter a date before 1980-01-01:
    <input type="date" name="bday" max="1979-12-31"><br>
    
    Enter a date after 2000-01-01:
    <input type="date" name="bday" min="2000-01-02"><br>
    
    <input type="datetime-local">
    
    <input type="email">
    
    <input type="file"> : file-select field and a "Browse" button for file uploads
    
    <input type="month"> : the user to select a month and year
    <input type="number"> : numeric input field,
    
    You can also set restrictions on what numbers are accepted.
    
    <input type="number" name="quantity" min="1" max="5">
    
    <input type="range">
    
    <input type="search">
    
    <input type="tel">
    
    <input type="time">
    
    <input type="url">
    
    <input type="week">
    </div>
    ```html
    <input type="color">
    
    Enter a date before 1980-01-01:
    <input type="date" name="bday" max="1979-12-31"><br>
    
    Enter a date after 2000-01-01:
    <input type="date" name="bday" min="2000-01-02"><br>
    
    <input type="datetime-local">
    
    <input type="email">
    
    <input type="file"> : file-select field and a "Browse" button for file uploads
    
    <input type="month"> : the user to select a month and year
    <input type="number"> : numeric input field,
    
    You can also set restrictions on what numbers are accepted.
    
    <input type="number" name="quantity" min="1" max="5">
    
    <input type="range">
    
    <input type="search">
    
    <input type="tel">
    
    <input type="time">
    
    <input type="url">
    
    <input type="week">
    ```

* Value attr

    The value attribute specifies the initial value for an input field:
    <input type="text" name="firstname" value="John">

* Readonly attr

    The readonly attribute specifies that the input field is read only (cannot be changed):

* Disabled Attribute

    A disabled input field is unusable and un-clickable, and its value will not be sent when submitting the form:
    <input type="text" name="firstname" value="John" disabled>

* Size attr

    The maxlength Attribute
    The maxlength attribute does not provide any feedback. If you want to alert the user, you must write JavaScript code.

    [w3schools](https://www.w3schools.com/html/html_form_attributes.asp)

Note:
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
웹 접근성 기준 상, 폼 입력 요소가 있다면 이에 해당하는 **label 요소**를 반드시 가지고 있어야 합니다. 
label은 폼 입력 요소에 무엇을 입력하는 지 명시해 주는 요소. 주로 해당 입력 요소의 id를 연결. 

**만약 label을 넣을만한 공간적인 여유가 없거나 부득이한 경우라면, 해당 폼 입력 요소에 title 속성이라도 넣도록 권장하고 있습니다**
</div>

### select

**select element defines a drop-down list**

```html
<select name="cars">
  <option value="volvo" selected size="3">Volvo</option>
</select>
```

Allow Multiple Selections
{: .label .mt-3}
<div class="code-example" markdown="1">
Use the multiple attribute to allow the user to select more than one value.
Hold down the Ctrl (windows) / Command (Mac) button to select multiple options.
</div>

* optgroup

    **소제목 달기, make it bold**
    
    ```html
    <select>
      <optgroup label="Swedish Cars">
        <option value="volvo">Volvo</option>
        <option value="saab">Saab</option>
      </optgroup>
    <select>
    ```

### textarea

**a multi-line input field**

&#9656; 사이즈를 고정하고 싶으면 resize: none;

### button

**a clickable button**

Note:
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
Always specify the type attribute for the button element. 
Different browsers may use different default types for the button element.
</div>

### fieldset

**Grouping Form Data**

* legend : caption for the fieldset element

### datalist

**pre-defined options for an input element**

&#9656; input type list 속성에 datalist id를 같게 만들면, datalist 하위 option값들이 드롭다운 버튼에 나타난다

<div class="code-example" markdown="1">
    <form action="/action_page.php">
      <input list="browsers">
      <datalist id="browsers">
        <option value="Internet Explorer">
        <option value="Firefox">
        <option value="Chrome">
        <option value="Opera">
        <option value="Safari">
      </datalist>
    </form>
</div>
```html
<form action="/action_page.php">
  <input list="browsers">
  <datalist id="browsers">
    <option value="Internet Explorer">
    <option value="Firefox">
    <option value="Chrome">
    <option value="Opera">
    <option value="Safari">
  </datalist>
</form>
```

### output

represents the **result of a calculation** (like one performed by a script).

<div class="code-example" markdown="1">
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" id="a" value="50">
    +<input type="number" id="b" value="25">
    =<output name="x" for="a b"></output>
</form>    
</div>
```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" id="a" value="50">
    +<input type="number" id="b" value="25">
    =<output name="x" for="a b"></output>
</form>
```

---

## HTML Attributes

### 기본특징

&#9656; All HTML elements can have attributes

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

## HTML Semantic

### What is Semantic?

**문서의 구조와 의미를 표현하는 태그**

웹 접근성을 위해 꼭 필요함, 검색 엔진이 시멘틱 태그 기반으로 움직임

### HTML Layout Elements

* header : 페이지나 섹션의 머리말을 표현, section이나 article 태그 내에도 사용됨
* nav : 하이퍼링크들을 모아논 특별한 섹션, 목차
* section : 문서의 장 혹은 절을 구성하는 역할, h1~6로 섹션의 주제를 기재하는 것이 바람직 
* article : 본문과 연결되어 있는 독립적인 콘텐츠, section의 보조적인 기사
* aside : 흐름에 벗어나 짤막하게 곁들이는 관련 기사.. 
* footer : 꼬리말 영역을 표시하는 태그 
* figure : 본문에 삽입된 그림을 블록화 하는 시맨틱 태그
* details : 상세정보 담기 summary가 제목태그

### Features of Semantic Elements

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
IE9에서는 시멘틱 의미를 해석못해서, head태그 안에 HTML5Shiv라는 구문을 추가 해줘야함 
</div>
```html
<!--[if lt IE 9]>
    <script src="/js/html5shiv.js"></script>
<![endif]-->
```

### New Elements

스스로 html 테그를 만들어서 사용할 수 있음

---

## HTML Graphics

### Canvas Graphics

**used to draw graphics, on the fly, via JavaScript.**

&#9656; only a container for graphics, You must use JavaScript to actually draw the graphics.

#### Reference
{: .no_toc}
[w3schools](https://www.w3schools.com/graphics/canvas_intro.asp)
    
### SVG Graphics

**vector-based graphics in XML format**

* svg element is a container for SVG graphics

<div class="code-example" markdown="1">
* 원형
    <svg width="100" height="100">
      <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
    </svg>

* 네모
    <svg width="400" height="100">
      <rect width="400" height="100" style="fill:rgb(0,0,255);stroke-width:10;stroke:rgb(0,0,0)" />
    </svg>

* Rounded Rectangle
    <svg width="400" height="180">
      <rect x="50" y="20" rx="20" ry="20" width="150" height="150"
      style="fill:red;stroke:black;stroke-width:5;opacity:0.5" />
    </svg>

* SVG Star
<svg width="300" height="200">
  <polygon points="100,10 40,198 190,78 10,78 160,198"
  style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;" />
</svg>

* SVG Logo
<svg height="130" width="500">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <ellipse cx="100" cy="70" rx="85" ry="55" fill="url(#grad1)" />
  <text fill="#ffffff" font-size="45" font-family="Verdana" x="50" y="86">SVG</text>
  Sorry, your browser does not support inline SVG.
</svg>
</div>
```html
* 원형
    <svg width="100" height="100">
      <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
    </svg>

* 네모
    <svg width="400" height="100">
      <rect width="400" height="100" style="fill:rgb(0,0,255);stroke-width:10;stroke:rgb(0,0,0)" />
    </svg>

* Rounded Rectangle
    <svg width="400" height="180">
      <rect x="50" y="20" rx="20" ry="20" width="150" height="150"
      style="fill:red;stroke:black;stroke-width:5;opacity:0.5" />
    </svg>

* SVG Star
<svg width="300" height="200">
  <polygon points="100,10 40,198 190,78 10,78 160,198"
  style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;" />
</svg>

* SVG Logo
<svg height="130" width="500">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <ellipse cx="100" cy="70" rx="85" ry="55" fill="url(#grad1)" />
  <text fill="#ffffff" font-size="45" font-family="Verdana" x="50" y="86">SVG</text>
  Sorry, your browser does not support inline SVG.
</svg>
```

**Differences Between SVG and Canvas**
{: .text-blue-000}

SVG is a language for describing 2D graphics in XML.

Canvas draws 2D graphics, on the fly (with a JavaScript).

SVG is XML based, which means that every element is available within the SVG DOM. You can attach JavaScript event handlers for an element.

In SVG, each drawn shape is remembered as an object. If attributes of an SVG object are changed, the browser can automatically re-render the shape.

Canvas is rendered pixel by pixel. In canvas, once the graphic is drawn, it is forgotten by the browser. If its position should be changed, the entire scene needs to be redrawn, including any objects that might have been covered by the graphic

Comparison of Canvas and SVG
{: .label .mt-3}

| Canvas                                            | SVG                                                                           | 
|:--------------------------------------------------|:------------------------------------------------------------------------------|
| Resolution dependent                              | Resolution independent                                                        |
| No support for event handlers                     | Support for event handlers                                                    | 
| Poor text rendering capabilities                  | Best suited for applications with large rendering areas (Google Maps)         | 
| You can save the resulting image as .png or .jpg  | Slow rendering if complex (anything that uses the DOM a lot will be slow)     | 
| Well suited for graphic-intensive games           | Not suited for game applications                                              |
{: .mt-3}

---

## HTML Add

### Comments

**주석달기**

<div class="code-example" markdown="1">
<!-- This is a comment --> This is a comment
</div>
```html
<!-- This is a comment --> This is a comment
```

### Character Entities

[특수문자](https://dev.w3.org/html5/html-author/charref)

### Emoji Characters
**Emojis are also characters from the UTF-8 alphabet**

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

[viewmore...](https://www.w3schools.com/charsets/ref_emoji.asp)





    

