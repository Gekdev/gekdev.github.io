---
layout: default
title: Where to
parent: Basic
grand_parent: JavaScript
nav_order: 1
---

# JavaScript Where to
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Internal JavaScript

### &#60;script&#62; 

**must be inserted between `<script>` tags**

```html
<script>-here!-</script> tags
```

&#9656; 스크립트가 짧을때 간편하게 사용

!Note
{: .label .label-blue}
<div class="code-example" markdown="1">
Old JavaScript examples may use a type attribute: `<script type="text/javascript">`
The type attribute is not required. JavaScript is the default scripting language in HTML
</div>

### html 태그

&#9656; script태그를 사용하지 않고 이벤트 핸들러로 자바스크립트를 실행 (코드가 짧은 경우 사용)

&#9656; 리스너 속성 : 이벤트가 발생할 때 처리하는 코드(자바스크립트)  ex) onclick=“this.src=’banana.png’”

&#9656; a의 href태그 속성에서도 코드작성 가능

이벤트와 이벤트 리스너
{: .label .label-blue .mt-2}
<div class="code-example" markdown="1">
* 이벤트 : 사용자의 입력 행위를 브라우저가 웹페이지에 전달하는 수단 (click, mousemove, change)
* 이벤트 리스너 : 이벤트를 처리하는 자바스크립트 코드 (onclick, onmouseover, onchange)
</div>

!JavaScript in head or body
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
어디든, 여러번 들어갈 수 있다
Placing scripts at the bottom of the `<body>` element improves the display speed, because script interpretation slows down the display.
</div>

---

## External Javascript

### external file

**스크립트 내용이 많을 때 사용**

```html
<script src="myScript.js"></script>

<script src=“파일이름.js”>이곳에 자바스크립트 코드 추가작성 가능</script> 
```

Placing scripts in external files has some advantages

1. It separates HTML and code

2. It makes HTML and JavaScript easier to read and maintain

3. Cached JavaScript files can speed up page loads

&#9733; 자바스크립트 파일에 스크립트 태그 저장하면 안됨

### external url
    
<script src="https://www.w3schools.com/js/myScript.js"></script>

