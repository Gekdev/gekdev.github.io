---
layout: default
title: Sources
parent: Advanced
grand_parent: HTML
nav_order: 2
---

# Sources
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Special Characters

### Character Entities

&#9656; 특수문자를 코드로 사용해서 작성해야 마크업 언어가 꼬이지 않음

<span class="fs-2">
[특수문자 사이트](https://dev.w3.org/html5/html-author/charref){: .btn  .btn-outline .mt-2}
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
[이모지 더보기](https://www.w3schools.com/charsets/ref_emoji.asp){: .btn  .btn-outline .mt-2}
</span>

---

## External Sources

### Icon

* [Font Awesome](https://fontawesome.com/) 
    
    <div class="code-example" markdown="1">
    <img src="https://gekdev.github.io/assets/images/font_awesome.jpg" alt="">
    </div>
    ```html
    <script  src="https://kit.fontawesome.com/cefbde467a.js" crossorigin="anonymous"></script>
        &#8594; 가입하면 개인별로 스크립트 코드를 부여함
    ...
    
    <a href="#">
        <span>cat</span>
        <i class="fas fa-cat fa-5x"></i> 
    </a>
    ```

* [Bootstrap Icons](https://icons.getbootstrap.com/) 

    ```html
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    ```

* [Google Icons](https://material.io/resources/icons/?style=baseline) 

    ```html
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
    ```