---
layout: default
title: Graphics
parent: HTML
nav_order: 6
---

# Graphics
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Graphics

### Canvas Graphics

**used to draw graphics, on the fly, via JavaScript.**

&#9656; only a container for graphics, You must use JavaScript to actually draw the graphics.

#### Reference
{: .no_toc}
[w3schools](https://www.w3schools.com/graphics/canvas_intro.asp)
    
### SVG Graphics

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
