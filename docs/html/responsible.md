---
layout: default
title: Responsive
parent: HTML
nav_order: 4
---

# HTML Responsive 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Responsive Basics

### What is Responsive?

**creating web pages that look good on all devices**

---

## How to make Responsive layout

### Setting The Viewport

head의 meta태그에 추가함

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This will set the viewport of your page, which will give the browser instructions on how to control the page's dimensions and scaling.

[meta 태그 더 확인하기](https://gekdev.github.io/docs/html/advanced/meta/)

### Responsive Images

**Responsive images are images that scale nicely to fit any browser size**

&#8594; 원본 크기보다 커질 수 있음 그래서 max-width 사용함

* Using the width Property

<div class="code-example" markdown="1">
<img src="https://gekdev.github.io/assets/images/cat1.jpg" style="width:100%;">
</div>
```html
<img src="https://gekdev.github.io/assets/images/cat1.jpg" style="width:100%;">
```

* Using the max-width Property

100%로 설정되어 있으면 원본크기보다 커지지 않는이상 최대한 크게 맞춤.

<div class="code-example" markdown="1">
<img src="https://gekdev.github.io/assets/images/cat1.jpg" style="max-width:100%;height:auto;">
</div>
```html
<img src="https://gekdev.github.io/assets/images/cat1.jpg" style="max-width:100%;height:auto;">
```

* Show Different Images Depending on Browser Width

**`<picture>` element allows you to define different images for different browser window sizes**

<div class="code-example" markdown="1">
<picture>
  <source srcset="https://gekdev.github.io/assets/images/dog2.png" media="(max-width: 600px)">
  <source srcset="https://gekdev.github.io/assets/images/dog3.png" media="(max-width: 1500px)">
  <source srcset="https://gekdev.github.io/assets/images/dog4.png">
  <img src="img_smallflower.jpg" alt="Flowers">
</picture>
</div>
```html
<picture>
  <source srcset="https://gekdev.github.io/assets/images/dog2.png" media="(max-width: 600px)">
  <source srcset="https://gekdev.github.io/assets/images/dog3.png" media="(max-width: 1500px)">
  <source srcset="https://gekdev.github.io/assets/images/dog4.png">
  <img src="img_smallflower.jpg" alt="Flowers">
</picture>
```

### Responsive Text Size

**can be set with a "vw"(viewport width) unit**

Viewport is the browser window size. 1vw = 1% of viewport width. If the viewport is 50cm wide, 1vw is 0.5cm.

<div class="code-example" markdown="1">
<h1 style="font-size:10vw;">Responsive Text</h1>
<p style="font-size:5vw;">Resize the browser window to see how the text size scales.</p>
</div>
```html
<h1 style="font-size:10vw;">Responsive Text</h1>
<p style="font-size:5vw;">Resize the browser window to see how the text size scales.</p>
```

### Media Queries

**can define completely different styles for different browser sizes**

```html
/* Use a media query to add a break point at 800px: */
@media screen and (max-width:800px) {
  .left, .main, .right {
    width:100%; /* The width is 100%, when the viewport is 800px or smaller */
  }
}
```

[여기에서 더 확인하기](https://gekdev.github.io/docs/css/12.responsive/#rwd-media-queries)

### Responsive Web Page


<span class="fs-2">
[W3C Example](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_responsive_media_query3){: .btn  .btn-outline .mt-3}
</span>

### Bootstrap

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.0/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
```

<span class="fs-2">
[Bootstrap](https://www.w3schools.com/bootstrap/bootstrap_ver.asp){: .btn  .btn-outline .mt-3}
</span>

