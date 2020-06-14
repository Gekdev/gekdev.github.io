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

## HTML Basic Element

### Head elements

* The `<title>` element

	defines a title in the browser tab
    
	&#9656; provides a title for the page when it is added to favorites
	
    &#9656; displays a title for the page in search engine results

* The HTML `<style>` Element

	define style information for a single HTML page

* The HTML `<link>` Element

	link to external style sheets
    
	`<link rel="stylesheet" href="mystyle.css">`

* The HTML `<meta>` Element

    specify which character set is used, page description, keywords, author, and other metadata.
    
    used by browsers (how to display content), by search engines (keywords), and other web services.
    
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
    HTML5 introduced a method to let web designers take control over the viewport, through the <meta> tag.
    The viewport is the user's visible area of a web page. It varies with the device, and will be smaller on a mobile phone than on a computer screen.
    </div>
    ```html
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
      // viewport element gives the browser instructions on how to control the page's dimensions and scaling.
      // The width=device-width part sets the width of the page to follow the screen-width of the device (which will vary depending on the device).
      // The initial-scale=1.0 part sets the initial zoom level when the page is first loaded by the browser.
    ```

* The HTML `<script>` Element
    
    define client-side JavaScripts.
    
* The HTML `<base>` Element
    
    specifies the base URL and base target for all relative URLs in a page
    
    ```html
    <base href="https://www.w3schools.com/images/" target="_blank">
    ```

    Omitting html, head and body tag?
    {: .label .lable-orange .mt-3}
    <div class="code-example" markdown="1">
    According to the HTML5 standard; the <html>, the <body>, and the <head> tag can be omitted.
    
    Note:
    W3Schools does not recommend omitting the <html> and <body> tags. Omitting these tags can crash DOM or XML software and produce errors in older browsers (IE9).
    </div>
    
    
### Body elements

●  HTML Headings (defined with h1~h6)
<h1> defines the most important heading. <h6> defines the least important heading: 
Search engines use the headings to index the structure and content of your web pages.
It is important to use headings to show the document structure.
Note: Use HTML headings for headings only. Don't use headings to make text BIG or bold.

●  HTML Paragraphs (defined with p)
  white-space: nowrap; - 하면 가로 스크롤 생김
안에 다른 block태그가 들어가면 안됑

●  HTML Links (defined with a)
Note: A link does not have to be text. It can be an image or any other HTML element.

	HTML Links - The target Attribute
	The target attribute specifies where to open the linked document.

	The target attribute can have one of the following values:

	_blank - Opens the linked document in a new window or tab
	_self - Opens the linked document in the same window/tab as it was clicked (this is default)
	_parent - Opens the linked document in the parent frame
	_top - Opens the linked document in the full body of the window
	framename - Opens the linked document in a named frame

	Link Bookmarks
	Use the id attribute (id="value") to define bookmarks in a page
	Use the href attribute (href="#value") to link to the bookmark

●  HTML Images (defined with img)
	attributes: The source file (src), alternative text (alt), width, and height

	HTML Image Maps - An image-map is an image with clickable areas.
	<img src="workplace.jpg" alt="Workplace" usemap="#workmap">

	<map name="workmap">
	  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
	  <area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">
	</map>

	Image Map and JavaScript
	https://www.w3schools.com/html/tryit.asp?filename=tryhtml_images_map5

img align - style attribute
● 	vertical-align: text-top;
● 	vertical-align: text-bottom;

img transparency :  opacity: 0.3;


cf) The HTML <picture> Element
	<picture> element to add more flexibility when specifying image resources.
<picture> element contains a number of <source> elements, each referring to different image sources. This way the browser can choose the image that best fits the current view and/or device.

<picture>
  <source media="(min-width: 650px)" srcset="img_food.jpg">
  <source media="(min-width: 465px)" srcset="img_car.jpg">
  <img src="img_girl.jpg">
</picture>

Note: Always specify an <img> element as the last child element of the <picture> element. The <img> element is used by browsers that do not support the <picture> element, or if none of the <source> tags matched.

When to use the Picture Element
1. Bandwidth
2. Format Support (you can add images of all formats, and the browser will use the first format it recognizes and ignore any of the following.)

●  HTML Buttons
<button>Click me</button>

●  HTML Lists
list is block, so float attribute is possible
HTML lists are defined with the <ul> (unordered/bullet list) or the <ol> (ordered/numbered list) tag, followed by <li> tags (list items):

●  HTML Horizontal Rules (hr)

●  The HTML <pre> Element
<pre> element is displayed in a fixed-width font (usually Courier), and it preserves both spaces and line breaks:

●  HTML Formatting Elements
● 	<b> - Bold text
● 	<strong> - Important text
● 	<i> - Italic text
● 	<em> - Emphasized text
● 	<mark> - Marked text
● 	<small> - Small text
● 	<del> - Deleted text
● 	<ins> - Inserted text
● 	<sub> - Subscript text
● 	<sup> - Superscript text

●  HTML Quotation and Citation Elements
HTML <q> for Short Quotations =" "
HTML <blockquote> for Quotations = indent
HTML <abbr> for Abbreviations = title, .....
HTML <address> for Contact Information = italic
HTML <cite> for Work Title = italic
	The HTML <cite> element defines the title of a work.
	Browsers usually display <cite> elements in italic.
HTML <bdo> for Bi-Directional Override
The HTML <bdo> element defines bi-directional override.

---

## HTML Attributes

### Features of Attribute

● All HTML elements can have attributes
● Attributes provide additional information about an element
● Attributes are always specified in the start tag
● Attributes usually come in name/value pairs like: name="value"

### Attribute


B. The href Attribute
The link address is specified in the href attribute:

C. The src Attribute
The filename of the image source is specified in the src attribute:

D. The width and height Attributes
HTML images have width and height attributes

E. The alt Attribute
The alt attribute specifies an alternative text to be used, if an image cannot be displayed.
can be read by screen readers.

F. The style Attribute
The style attribute is used to specify the styling of an element, like color, font, size etc.
<tagname style="property:value;">

G. The lang Attribute
The language of the document can be declared in the <html> tag.
The language is declared with the lang attribute.
important for accessibility applications (screen readers) and search engines

H. The title Attribute(tooltip)
The value of the title attribute will be displayed as a tooltip when you mouse over


▶ We Suggest: Quote Attribute Values
W3C recommends quotes in HTML, and demands quotes for stricter document types like XHTML.

▶ Single or Double Quotes?
Double quotes around attribute values are the most common in HTML, but single quotes can also be used.

In some situations, when the attribute value itself contains double quotes, it is necessary to use single quotes:

▶ more attributes 
https://www.w3schools.com/tags/ref_attributes.asp

