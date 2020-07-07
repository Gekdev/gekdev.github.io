---
layout: default
title: Basic
parent: Advanced
grand_parent: CSS
nav_order: 1
---

# Basic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## CSS Object-fit

### CSS object-fit Property

이미지와 비디오태그가 부모 태그 안에서 어떻게 보여야하는지 (사이징)

부모태그 안에 이미지 두개가 width 50%로 지정되어 있으면

리사이징할때 이미지가 비율을 무시하고 자유자재로 늘어나고 줄어들음

따라서 object-fit을 사용해서 **비율을 어떻게 유지시킬건지 설정**

* fill : sized to fill the element's content box. 늘어나거나 줄어듬 (default)

* contain : 비율에 맞춰 꼭 콘텐츠 내부에 들어가야 하는것, 컨텐츠 배경이 보일 수 있음

    > background-size: contain;과 동일함

* cover : 콘텐츠 내부에 꽉차게 하는것, 부모에 맞게 딱 짤린다

    > background-size: cover;과 동일함
    
    ```css
    img {
      width: 200px;
      height: 400px;
      object-fit: cover;
    }
    ```
    
* none : not resized

* scale-down : if none or contain were specified (would result in a smaller concrete object size)

---

## CSS Buttons

### Button Decoration

* 호버시 오른쪽 화살표 생성

    <ul class="list-style-none">
        <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_buttons_animate1">
            <img src="https://gekdev.github.io/assets/images/bt1.JPG" alt="">
        </a>
    </ul>

* 호버시 진해짐

    <ul class="list-style-none">
        <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_buttons_fade">
            <img src="https://gekdev.github.io/assets/images/bt2.JPG" alt="">
        </a>
    </ul>

* 호버시 어두워짐

    <ul class="list-style-none">
        <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_buttons_animate2">
            <img src="https://gekdev.github.io/assets/images/bt3.JPG" alt="">
        </a>
    </ul>

---

## CSS Buttons

### Button Decoration
