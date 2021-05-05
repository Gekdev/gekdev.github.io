---
layout: default
title: Transform
parent: CSS
nav_order: 10
---

# CSS Transform
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Transform

### What is Transform?

**요소에 회전, 크기 조절, 기울이기, 이동 효과를 부여하는 것**

CSS시각적 서식 모델의 좌표 공간을 변경

### Features of Transform

&#9656; transform 속성은 키워드 none 또는 하나 이상의 <transform-function> 값을 사용해 지정할 수 있음

```css
/* 키워드 값 */
transform: none;

/* 함수 값 */
transform: matrix(1.0, 2.0, 3.0, 4.0, 5.0, 6.0);
transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1);
transform: perspective(17px);
transform: rotate(0.5turn);
transform: rotate3d(1, 2.0, 3.0, 10deg);
transform: rotateX(10deg);
transform: rotateY(10deg);
transform: rotateZ(10deg);
transform: translate(12px, 50%);
transform: translate3d(12px, 50%, 3em);
transform: translateX(2em);
transform: translateY(3in);
transform: translateZ(2px);
transform: scale(2, 0.5);
transform: scale3d(2.5, 1.2, 0.3);
transform: scaleX(2);
transform: scaleY(0.5);
transform: scaleZ(0.3);
transform: skew(30deg, 20deg);
transform: skewX(30deg);
transform: skewY(1.07rad);

/* 다중 함수 값 */
transform: translateX(10px) rotate(10deg) translateY(5px);
transform: perspective(500px) translate(10px, 0, 20px) rotateY(3deg);

/* 전역 값 */
transform: inherit;
transform: initial;
transform: unset;
```

---

## 2D Transform Values

### translate()

**X,Y축에 따라 현재 위치에서 이동시키는것**

```css
div {
  transform: translate(50px, 100px);
}
```

### rotate()

**각도값으로 회전시키는것**

&#9656; 양수값이면 시계방향, 음수값이면 반시계방향임

```css
div {
  transform: rotate(20deg);
}
```

### scale()

**크기를 키우거나 줄이는 값**

&#9656; 인수를 넣으면 원래 주어진값에 배로 들어감

```css
div {
  transform: scale(2, 3);
}

div {
  transform: scale(0.5, 0.5);
}
```

### scaleX()

**가로값만 크기 조정**

```css
div {
  transform: scaleX(2);
}
```

### scaleY()

**세로값만 크기 조정**

```css
div {
  transform: scaleY(2);
}
```

### skew()

**비틀기**

```css
div {
  transform: skew(20deg, 10deg);
}

div {
  transform: skew(20deg);
}
```

### skewX()

**X축으로 비틀기**

```css
div {
  transform: skewX(20deg);
}
```

### skewY()

**Y축으로 비틀기**

```css
div {
  transform: skewY(20deg);
}
```

### matrix()

**모든 2D변형 메소드를 모아놓은것** 단축 프로퍼티 같은것

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
matrix(scaleX(),skewY(),skewX(),scaleY(),translateX(),translateY())
</div>
```css
div {
  transform: matrix(1, -0.3, 0, 1, 0, 0);
}
```    

<span class="fs-2">
[W3C Example](https://www.w3schools.com/css/tryit.asp?filename=trycss3_transform_matrix1){: .btn .btn-outline .mt-2}
</span>
  
---

## 3D Transforms Values

### rotateX()

**X축으로 돌기**

```css
#myDiv {
  transform: rotateX(150deg);
}
```

### rotateY()

**Y축으로 돌기**

```css
#myDiv {
  transform: rotateY(130deg);
}
```

### rotateZ()

**Z축으로 돌기**

```css
#myDiv {
  transform: rotateZ(90deg);
}
```
