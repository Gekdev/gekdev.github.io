---
layout: default
title: Advanced 
parent: Elements
grand_parent: HTML
nav_order: 4
---

# Advanced 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Iframe element

### &#60;iframe&#62; 

**display a web page within a web page**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<iframe src="url" title="description">
</div>

&#9656; height및 width으로 가로 세로값을 지정할 수 있음

&#9656; border:none;으로 테두리를 없앨 수 있음

&#9656; target값 name 따라서 가거나 blank, self, parent, top 등 다양하게 갈 수 있음

&#9656; inframe 서로 들어갈 수 있음

&#8594; a링크 타겟을 지정해서 iframe name과 연결하면 a링크 주소에따라 iframe 주소값이 달라짐

&#8594; 보안 이슈때문에 대기업 사이트들은 iframe 접근을 막아둠

예시
{: .label .label-purple .mt-2}
```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="https://www.w3schools.com" target="iframe_a">W3Schools.com</a></p>
<p><a href="https://www.google.com" target="iframe_a">google.com</a></p>
```

### Youtube Link 

유튜브는 좀 더 복잡한 방식으로 넣어야함

* [w3schools](https://www.w3schools.com/html/html_youtube.asp)

* [cdmanii](https://cdmanii.com/3392)

## Media elements

### &#60;video&#62; 

**show a video on a web page**

&#9656; attribute : autoplay, controls, loop

```html
<video width="320" height="240" controls autoplay loop> 
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
Your browser does not support the video tag.
</video>
```

### &#60;audio&#62; 

**play an audio file on a web page**

```html
<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>
```

### &#60;object, embed&#62; 

**embedded object within an HTML document**

&#9656; supported by all browsers.

&#9656; It was designed to embed plug-ins

```html
<object width="400" height="50" data="bookmark.html"></object>
<object data="audi.jpeg"></object>
---
<embed width="400" height="50" src="bookmark.swf">
```

---

## Quotation and Citation

| description                   | tag                                    | shape                                |
|:------------------------------|:---------------------------------------|:-------------------------------------|
| Short Quotations (" ")        | `<q>q</q>`                             | <q>q</q>                             |
| Quotations (indent)           | `<blockquote>blockquote</blockquote>`  | <blockquote>blockquote</blockquote>  |
| Abbreviations (.....)         | `<abbr title="abbr">abbr</abbr>`       | <abbr title="abbr">abbr</abbr>       |
| Contact Information (italic)  | `<address>address</address>`           | <address>address</address>           |
| Work Title (italic)           | `<cite>cite</cite>`                    | <cite>cite</cite>                    |
| bi-directional override       | `<bdo dir="rtl">bdo</bdo>`             | <bdo dir="rtl">bdo</bdo>             |

---

## Graphics

### &#60;canvas&#62;

**used to draw graphics, on the fly, via JavaScript.**

&#9656; only a container for graphics, You must use JavaScript to actually draw the graphics.

#### Reference
{: .no_toc}
[w3schools](https://www.w3schools.com/graphics/canvas_intro.asp)
    
### &#60;svg&#62;

**vector-based graphics in XML format**

&#9656; svg element is a container for SVG graphics

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

### Differences Between SVG and Canvas

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

---

## Computercode

### &#60;code&#62;

**a fragment of computer code**

&#8594; typically displayed in a monospace font
<div class="code-example" markdown="1">
<code>
x = 5;<br>
y = 6;<br>
z = x + y;
</code>
</div>

Notice
{: .label .label-yellow .mt-3}
```html
that the <code> element does not preserve extra whitespace and line-breaks.
To fix this, you can put the <code> element inside a <pre> element
```

### &#60;kbd&#62;

**Keyboard Input**

**user input, like keyboard input or voice commands**

&#8594; typically displayed in a monospace font
<div class="code-example" markdown="1">
<p>Save the document by pressing <kbd>Ctrl + S</kbd></p>
</div>
```html
<p>Save the document by pressing <kbd>Ctrl + S</kbd></p>
```

### &#60;samp&#62;

**Program Output**

**output from a program or computing system**

&#8594; typically displayed in a monospace font

<div class="code-example" markdown="1">
<p>If you input wrong value, the program will return <samp>Error!</samp></p>
</div>
```html
<p>If you input wrong value, the program will return <samp>Error!</samp></p>
```

### &#60;var&#62;

**Variables**

The variable could be a variable in a mathematical expression or a variable in programming context:
<div class="code-example" markdown="1">
Einstein wrote: <var>E</var> = <var>mc</var><sup>2</sup>
</div>
```html
Einstein wrote: <var>E</var> = <var>mc</var><sup>2</sup>
```

    

