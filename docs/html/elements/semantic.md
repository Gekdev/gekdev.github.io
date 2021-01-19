---
layout: default
title: Semantic
parent: Elements
grand_parent: HTML
nav_order: 5
--- 

# Semantic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Semantic Basic

### What are Semantic Elements?

**문서의 구조와 의미를 표현하는 태그**

its meaning to both the browser and the developer

웹 접근성을 위해 꼭 필요함, 검색 엔진이 시멘틱 태그 기반으로 움직임

대표적인 non-semantic : div, span / 대표적인 semantic : form, table, article ... 

사용해야 하는 이유 : A semantic Web allows data to be shared and reused across applications, enterprises, and communities

### Basic form of Semantic Elements

![](https://gekdev.github.io/assets/images/img_sem_elements.gif)

### Features of Semantic Elements

* Can nest <article> in <section> or vice versa

* 스스로 html 태그를 만들어서 사용할 수 있음

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

### Semantic block & Inline tag

* 시멘틱 블록 태그

    &#9656; figure	본문에 삽입된 그림을 블록화 하는 시맨틱 태그
    
    &#9656; details	상세정보 담기 summary가 제목태그
 
* 시멘틱 인라인 태그

    &#9656; mark, time, meter value=“0.8”, progress value=“2” max=“10”

---

## Semantic Layout Elements

### &#60;header&#62;
    
**페이지나 섹션의 머리말을 표현** 

&#9656; section이나 article 태그 내에도 사용됨

&#9656; 여러개의 header를 가져도 됨
    
### &#60;nav&#62; 
    
**하이퍼링크들을 모아논 특별한 섹션, 목차**

중요한 네비게이션 링크만 모아놓은 박스로 사용해야함.

### &#60;section&#62;  

**문서의 장 혹은 절을 구성하는 역할** 

**h1~6로 섹션의 주제를 기재해야함** 

A home page could normally be split into sections for introduction, content, and contact information.
    
### &#60;article&#62; 

**본문과 연결되어 있는 독립적인 콘텐츠**, section의 보조적인 기사

(Forum post, BLog post나 Newpaper article와 같은것들...)

### &#60;aside&#62; 

**흐름에 벗어나 짤막하게 곁들이는 관련 기사** (like a sidebar)

### &#60;footer&#62; 

**꼬리말 영역을 표시하는 태그**

&#9656; author of the document, copyright information, links to terms of use, contact information, etc.

&#9656; 여러번 사용해도 됨

### &#60;figure&#62;, &#60;figcation&#62;
    
figure : **본문에 삽입된 그림을 블록화 하는 시맨틱 태그**

figcation : **add a visual explanation to an image**

<div class="code-example" markdown="1">
<figure>
  <img src="https://www.w3schools.com/html/pic_trulli.jpg" alt="Trulli">
  <figcaption>Fig1. - Trulli, Puglia, Italy.</figcaption>
</figure>
</div>
```html
<figure>
  <img src="https://www.w3schools.com/html/pic_trulli.jpg" alt="Trulli">
  <figcaption>Fig1. - Trulli, Puglia, Italy.</figcaption>
</figure>
```
!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
The <img> element defines the image / the <figcaption> element defines the caption.
</div>

---

## Other Semantic Elements

### &#60;details&#62; 

**상세정보 담기**

&#60;summary&#62; 제목태그!

open attribute로 연 상태를 초기상태로 만들 수 있음(닫혀있는게 기본)

<div class="code-example" markdown="1">
<details>
  <summary>Epcot Center</summary>
  <p>Epcot is a theme park at Walt Disney World Resort featuring exciting attractions, international pavilions, award-winning fireworks and seasonal special events.</p>
</details>
</div>
```html
<details>
  <summary>Epcot Center</summary>
  <p>Epcot is a theme park at Walt Disney World Resort featuring exciting attractions, international pavilions, award-winning fireworks and seasonal special events.</p>
</details>
```

### &#60;main&#62;

**main content of a document**

should be unique to the document

It should not contain any content that is repeated across documents such as sidebars, navigation links, copyright information, site logos, and search forms.

<div class="code-example" markdown="1">
<h1>The main element</h1>

<main>
  <h1>Most Popular Browsers</h1>
  <p>Chrome, Firefox, and Edge are the most used browsers today.</p>

  <article>
    <h2>Google Chrome</h2>
    <p>Google Chrome is a web browser developed by Google, released in 2008. Chrome is the world's most popular web browser today!</p>
  </article>
</main>
</div>
```html
<h1>The main element</h1>

<main>
  <h1>Most Popular Browsers</h1>
  <p>Chrome, Firefox, and Edge are the most used browsers today.</p>

  <article>
    <h2>Google Chrome</h2>
    <p>Google Chrome is a web browser developed by Google, released in 2008. Chrome is the world's most popular web browser today!</p>
  </article>
</main>
```

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
There must not be more than one <main> element in a document. The <main> element must NOT be a descendant of an <article>, <aside>, <footer>, <header>, or <nav> element.
</div>

### &#60;mark&#62;

**marked/highlighted text**

default : background-color: yellow; color: black;

<div class="code-example" markdown="1">
<p>Do not forget to buy <mark>milk</mark> today.</p>
</div>
```html
<p>Do not forget to buy <mark>milk</mark> today.</p>
```

### &#60;time&#62; 

**specific time (or datetime)**

attribute : datetime - Represent a machine-readable format

this element is used translate the time into a machine-readable format so that browsers can offer to add date reminders through the user's calendar, and search engines can produce smarter search results

<div class="code-example" markdown="1">
<p>Open from <time>10:00</time> to <time>21:00</time> every weekday.</p>

<p>I have a date on <time datetime="2008-02-14 20:00">Valentines day</time>.</p>
</div>
```html
<p>Open from <time>10:00</time> to <time>21:00</time> every weekday.</p>

<p>I have a date on <time datetime="2008-02-14 20:00">Valentines day</time>.</p>
```

### &#60;meter&#62;

**미터 표시하기**

<div class="code-example" markdown="1">
<p>meter value="0.8"   <meter value="0.8"></meter></p>
</div>
```html
<p>meter value="0.8"   <meter value="0.8"></meter></p>
```

### &#60;progress&#62;

**진척도 표시하기**

<div class="code-example" markdown="1">
<p>progress value="2" max="5" <progress value="2" max="5"></progress></p>
</div>
```html
<p>progress value="2" max="5" <progress value="2" max="5"></progress></p>
```



