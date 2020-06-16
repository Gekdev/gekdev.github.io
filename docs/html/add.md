---
layout: default
title: Add
parent: HTML
nav_order: 99
---

# Add
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Basic

### Attribute

* Feature

    &#9656; All HTML elements can have attributes

    &#9656; Attributes provide additional information about an element

    &#9656; Attributes are always specified in the start tag

    &#9656; Attributes usually come in name/value pairs like: name="value"

    &#9656; attribute값 안에 불필요한 공백이 들어가면 오류 <br>
            &#8594; but 파일 이름 등 필수로 들어가는 경우 “”로 묶어야지 오류가 안남

* Basic Attributes

    * href : link address is specified in the href attribute

    * src : filename of the image source = 주소

    * alt : The alt attribute specifies an alternative text to be used, if an image cannot be displayed. **can be read by screen readers**

    * style : specify the styling of an element, like color, font, size etc.

    * lang : **important for accessibility applications (screen readers) and search engines**

    * title : displayed as a tooltip when you mouse over

    * [view more...](https://www.w3schools.com/tags/ref_attributes.asp)


Single or Double Quotes?
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
Double quotes around attribute values are the most common in HTML, but single quotes can also be used.
</div>

### Comments

**주석달기**

&#8594; 여러줄도 가능

<div class="code-example" markdown="1">
<!-- This is a comment --> This is a comment
</div>
```html
<!-- This is a comment --> This is a comment
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

### Character Entities

&#9656; 특수문자를 코드로 사용해서 작성해야 마크업 언어가 꼬이지 않음

<span class="fs-2">
[특수문자 사이트](https://dev.w3.org/html5/html-author/charref){: .btn .btn-blue .mt-3}
</span>

### Emoji Characters

**Emojis are characters from the UTF-8 alphabet**

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

<span class="fs-2">
[이모지 더보기](https://www.w3schools.com/charsets/ref_emoji.asp){: .btn .btn-blue }
</span>

---

## Advanced



    

