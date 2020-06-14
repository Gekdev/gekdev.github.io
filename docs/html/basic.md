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

## HTML Element

### Head element

● The `<title>` element
	defines a title in the browser tab
	provides a title for the page when it is added to favorites
	displays a title for the page in search engine results

● The HTML `<style>` Element
	define style information for a single HTML page

● The HTML `<link>` Element
	link to external style sheets
    
	`<link rel="stylesheet" href="mystyle.css">`

● The HTML <meta> Element
metadata is used by browsers (how to display content), by search engines (keywords), and other web services.
The <meta> element is used to specify which character set is used, page description, keywords, author, and other metadata.
<meta charset="UTF-8">
<meta name=“description” content=“생활코딩의 소개자료” > 
<meta name="keywords" content="HTML, CSS, XML, JavaScript"> 문서를 정의하는 단어들(키워드)
<meta name="author" content="John Doe">
<meta http-equiv="refresh" content="30"> 30초 간격으로 새로고침됨

Setting The Viewport
HTML5 introduced a method to let web designers take control over the viewport, through the <meta> tag.
The viewport is the user's visible area of a web page. It varies with the device, and will be smaller on a mobile phone than on a computer screen.

<meta name="viewport" content="width=device-width, initial-scale=1.0">

A <meta> viewport element gives the browser instructions on how to control the page's dimensions and scaling.

The width=device-width part sets the width of the page to follow the screen-width of the device (which will vary depending on the device).

The initial-scale=1.0 part sets the initial zoom level when the page is first loaded by the browser.

● The HTML <script> Element
The <script> element is used to define client-side JavaScripts.
● The HTML <base> Element
The <base> element specifies the base URL and base target for all relative URLs in a page:
<base href="https://www.w3schools.com/images/" target="_blank">

▶ Omitting <html>, <head> and <body>?
According to the HTML5 standard; the <html>, the <body>, and the <head> tag can be omitted.

Note:
W3Schools does not recommend omitting the <html> and <body> tags. Omitting these tags can crash DOM or XML software and produce errors in older browsers (IE9).

However, omitting the <head> tag has been a common practice for quite some time now.