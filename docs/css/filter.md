---
layout: default
title: Filter
parent: CSS
nav_order: 9
---

# CSS Filter
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Filter

### What is Filter?

**이미지, 배경, 테두리 렌더링들에 그래픽 효과를 적용조정하는 데 쓰임**

### Features of Filter

&#9656; 나열해서 다중으로 사용가능함

&#9656; filter:none;은 필터없음

```css
/* SVG 필터를 가리키는 URL */
filter: url("filters.svg#filter-id");

/* <filter-function> 값 */
filter: blur(5px);
filter: brightness(0.4);
filter: contrast(200%);
filter: drop-shadow(16px 16px 20px blue);
filter: grayscale(50%);
filter: hue-rotate(90deg);
filter: invert(75%);
filter: opacity(25%);
filter: saturate(30%);
filter: sepia(60%);

/* 다중 값 */
filter: contrast(175%) brightness(3%);

/* 필터 없음 */
filter: none;

/* 전역 값 */
filter: inherit;
filter: initial;
filter: unset;
```

---

## Filter Values

### blur()

**주어진 이미지에 가우시안 블러를 적용**

&#9656; radius 값은 정규 분포의 표준 편차, 즉 화면에서 혼합할 픽셀의 수를 지정하므로 값이 클수록 이미지가 흐려짐

&#9656; 보간 시 누락값은 0

&#9656; 매개변수는 CSS 길이로 명시되어 있지만 백분율 값은 받지 않음

### brightness()

**주어진 이미지에 선형 배수를 적용하여 이미지를 밝거나 어둡게 표시**

&#9656; 0%일 경우 완전히 검은색 이미지가 되고, 100%일 경우 이미지가 그대로 유지되며, 이외의 값은 효과의 선형 배수로 작용

&#9656; 100%보다 큰 값도 허용되며, 이때는 더 밝은 이미지가 생성

&#9656; 보간 시 누락값은 1입니다.

### contrast()

**주어진 이미지의 대비를 조정** 

&#9656; 0%일 경우 완전히 회색 이미지, 100%일 경우 이미지가 그대로 유지

&#9656; 100%보다 큰 값도 허용되며, 이때는 대비가 더 큰 이미지가 생성

&#9656; 보간 시 누락값은 1입니다.

<div class="code-example" markdown="1">
<div style="width: 200px; height: 100px;">
<img src="https://placeimg.com/200/100" alt="">
</div>
<p>basic image</p>
<div style="width: 200px; height: 100px; filter: grayscale(100%)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: grayscale(100%)</p>
<div style="width: 200px; height: 100px; filter: sepia(100%)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: sepia(100%)</p>
<div style="width: 200px; height: 100px; filter: saturate(10)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: saturate(10)</p>
<div style="width: 200px; height: 100px; filter: hue-rotate(90deg)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: hue-rotate(90deg)</p>
<div style="width: 200px; height: 100px; filter: invert(100%)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: invert(100%)</p>
<div style="width: 200px; height: 100px; filter: brightness(140%)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: brightness(140%)</p>
<div style="width: 200px; height: 100px; filter: contrast(200%)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: contrast(200%)</p>
<div style="width: 200px; height: 100px; filter: blur(3px)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: blur(3px)</p>
<div style="width: 200px; height: 100px; filter: drop-shadow(5px 5px 5px purple)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: drop-shadow(5px 5px 5px purple)</p>
<div style="width: 200px; height: 100px; filter: grayscale(100%) blur(3px) drop-shadow(5px 5px 5px #000)"><img src="https://placeimg.com/200/100" alt=""></div>
<p>filter: grayscale(100%) blur(3px) drop-shadow(5px 5px 5px #000)</p>
</div>
```html
<div style="width: 200px; height: 100px;"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>basic image</p>
    <div style="width: 200px; height: 100px; filter: grayscale(100%)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: grayscale(100%)</p>
    <div style="width: 200px; height: 100px; filter: sepia(100%)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: sepia(100%)</p>
    <div style="width: 200px; height: 100px; filter: saturate(10)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: saturate(10)</p>
    <div style="width: 200px; height: 100px; filter: hue-rotate(90deg)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: hue-rotate(90deg)</p>
    <div style="width: 200px; height: 100px; filter: invert(100%)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: invert(100%)</p>
    <div style="width: 200px; height: 100px; filter: brightness(140%)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: brightness(140%)</p>
    <div style="width: 200px; height: 100px; filter: contrast(200%)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: contrast(200%)</p>
    <div style="width: 200px; height: 100px; filter: blur(3px)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: blur(3px)</p>
    <div style="width: 200px; height: 100px; filter: drop-shadow(5px 5px 5px purple)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: drop-shadow(5px 5px 5px purple)</p>
    <div style="width: 200px; height: 100px; filter: grayscale(100%) blur(3px) drop-shadow(5px 5px 5px #000)"><img src="https://placeimg.com/200/100" alt=""></div>
    <p>filter: grayscale(100%) blur(3px) drop-shadow(5px 5px 5px #000)</p>
```