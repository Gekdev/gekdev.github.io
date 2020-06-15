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
    
    &#9656; href 링크 종류
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
    
    // 상대경로가 가장 좋은 방법!
    {: .text-blue-000}
    </div>
    
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

### Media
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

### Quotations

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

### Computercode

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


### HTML Table


---

## HTML Form

### Form element
form is used to collect user input

* Form attr

action=“웹 서버 응용 프로그램의 url”
enctype=“인코딩 타입”(데이터를 전송할 때 암호과 방식 지정)
method=“GET/POST”(폼 데이터를 웹 서버에 전송하는 방식)
name=“폼 이름”
target=“윈도우 이름”(응용프로그램으로부터 받은 데이터를 출력할 윈도우 이름)

* Form Tip

input type=“hidden” name=“hide” value=“hey” -  그냥 데이터만 서버에 전송해야 할떄

When to Use GET?
	The default method when submitting form data is GET.

	However, when GET is used, the submitted form data will be visible in the page address field:

	Notes on GET:
	Appends form-data into the URL in name/value pairs
	The length of a URL is limited (2048 characters)
	Never use GET to send sensitive data! (will be visible in the URL)
	Useful for form submissions where a user wants to bookmark the result
	GET is better for non-secure data, like query strings in Google

	When to Use POST?
	Always use POST if the form data contains sensitive or personal information. The POST method does not display the submitted form data in the page address field.

	Notes on POST:
	POST has no size limitations, and can be used to send large amounts of data.
	Form submissions with POST cannot be bookmarked

웹 접근성 기준 상, 폼 입력 요소가 있다면 이에 해당하는 label 요소를 반드시 가지고 있어야 합니다. label은 폼 입력 요소에 무엇을 입력하는 지 명시해 주는 요소. 주로 해당 입력 요소의 id를 연결. 만약 label을 넣을만한 공간적인 여유가 없거나 부득이한 경우라면, 해당 폼 입력 요소에 title 속성이라도 넣도록 권장하고 있습니다.

### input element
<input type="text" title="아이디 입력" />
The Name Attribute
Each input field must have a name attribute to be submitted.

If the name attribute is omitted, the data of that input field will not be sent at all.

● The <select> Element
The <select> element defines a drop-down list:
<select name="cars">
  <option value="volvo" selected size="3">Volvo</option>
</select>

Allow Multiple Selections
Use the multiple attribute to allow the user to select more than one value.
Hold down the Ctrl (windows) / Command (Mac) button to select multiple options.

● The <textarea> Element
The <textarea> element defines a multi-line input field
사이즈를 고정하고 싶으면   resize: none;

● The <button> Element
The <button> element defines a clickable button:
<button type="button" onclick="alert('Hello World!')">Click Me!</button>
Note: Always specify the type attribute for the button element. Different browsers may use different default types for the button element.

datalist
	input type list 속성에 datalist id를 같게 만들면
	datalist 하위 option값들이 드롭다운 버튼에 나타난다 - 정답 미리보기 같은 개념

The datalist element specifies a list of pre-defined options for an input element.

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


HTML input types
HTML Input Types
Here are the different input types you can use in HTML:

● <input type="button">
<input type="button" onclick="alert('Hello World!')" value="Click Me!">
● <input type="checkbox">
● <input type="color">
● <input type="date">
● <input type="datetime-local">
● <input type="email">
● <input type="file">
	거의 모든 방식에서 method=“post” 와 enctype=“multipart/form-data”>를 씀 name이 없으면 에러가 뜸
● <input type="hidden">
● <input type="image">
● <input type="month">
● <input type="number">
● <input type="password">
● <input type="radio">
● <input type="range">
● <input type="reset">
● <input type="search">
● <input type="submit">
● <input type="tel">
● <input type="text">
● <input type="time">
● <input type="url">
● <input type="week">

new
● color
● date
	<form>
	  Enter a date before 1980-01-01:
	  <input type="date" name="bday" max="1979-12-31"><br>
	  Enter a date after 2000-01-01:
	  <input type="date" name="bday" min="2000-01-02"><br>
	</form>
● datetime-local
● email
● file
	The <input type="file"> defines a file-select field and a "Browse" button for file uploads.
● month
	The <input type="month"> allows the user to select a month and year.
● number
	The <input type="number"> defines a numeric input field.
	You can also set restrictions on what numbers are accepted.
	 <input type="number" name="quantity" min="1" max="5">
● range
● search
● tel
● time
● url
● week

* attr
attributes
The value Attribute
The value attribute specifies the initial value for an input field:
  <input type="text" name="firstname" value="John">

The readonly Attribute
The readonly attribute specifies that the input field is read only (cannot be changed):

The disabled Attribute
A disabled input field is unusable and un-clickable, and its value will not be sent when submitting the form:
<input type="text" name="firstname" value="John" disabled>

The size Attribute

The maxlength Attribute
The maxlength attribute does not provide any feedback. If you want to alert the user, you must write JavaScript code.

[w3schools](https://www.w3schools.com/html/html_form_attributes.asp)


HTML <optgroup> Tag
make it bold
<select>
  <optgroup label="Swedish Cars">
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
  </optgroup>

HTML5 <output> Element
The <output> element represents the result of a calculation (like one performed by a script).

input img에는 src필요

Grouping Form Data with <fieldset>
The <fieldset> element is used to group related data in a form.

The <legend> element defines a caption for the <fieldset> element.

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
figure	본문에 삽입된 그림을 블록화 하는 시맨틱 태그
details	상세정보 담기 summary가 제목태그

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

## HTML Layout Techniques
There are five different ways to create multicolumn layouts. Each way has its pros and cons:

● HTML tables (not recommended) - Do NOT use tables for your page layout!
● CSS float property
It is common to do entire web layouts using the CSS float property. Float is easy to learn - you just need to remember how the float and clear properties work. Disadvantages: Floating elements are tied to the document flow, which may harm the flexibility. 
	float된 요소는 내부의 float된 요소를 인식한다, 띄어진 요소는 띄어진 요소 서로간을 인식하고 그 다음으로 위치
요점 정리
블록 요소를 가로로 나란히 정렬하기 위해서는 float을 이용
float된 요소는 기본적으로 상위 요소가 영역을 파악하지 못함 (float가 요소를 띄움)
float는 띄어지기 때문에, 보통 다음 블록 요소는 float된 요소 밑에 깔리게 됨.
블록 요소는 기본적으로 float을 인식하지 못함. 텍스트, 인라인 요소, 그리고 float된 요소만 다른 float요소를 인식 함.
float된 요소를 부모 요소가 포함하기 위해, height로 임의의 높이 값을 줄 수 있지만, 내부 float 요소의 높이 바뀔 때마다 직접 바꿔줘야 함.
float된 요소들 다음에 비어있는 div에 clear:both 속성을 주어 부모가 높이를 자동으로 인식하게 할 수 있음.
float된 요소들의 부모 요소에 overflow:hidden을 줄 경우, 부모 요소는 float된 요소를 인식.
overflow:hidden은 자식 요소의 margin 값도 내부로 인식하게 함.
float된 요소의 부모가 float 될 경우, 부모 요소는 자식 요소를 인식 함.
float 될 경우, 기존 블럭 요소처럼 너비가 넓게 퍼지지 않음. 기본적으로 내부 영역 만큼의 너비를 가짐.


---

## HTML API


---

## HTML API





    

