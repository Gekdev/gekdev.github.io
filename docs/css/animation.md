---
layout: default
title: Animation
parent: CSS
nav_order: 12
---

# CSS Animation
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Animations

### What are CSS Animations?

**요소의 스타일을 다른스타일로 점차 변화시키는것**

★ 필수사항 : **@keyframes**

기본형식
{: .label .mt-3}
```css
/* The animation code */
@keyframes example {
  from {background-color: red;}
  to {background-color: yellow;}
}

/* The element to apply the animation to */
div {
  width: 100px;
  height: 100px;
  background-color: red;
  animation-name: example;
  animation-duration: 4s;
}
```

---

## Animation Properties

### @keyframes

**점차 변화시킬때 사용**

&#9656; 꼭 요소와 bind시켜야함

&#9656; from to 나 % 사용

### animation-name

**keyframes와 bind시키기 위해 꼭 있어야 하는 값**

### animation-duration

**끝날때까지 얼마나 시간이 걸려야하는지**

&#9656; default : 0 이라서 꼭 값이 있어야함

### animation-delay

**처음 시작할 때 얼마나 딜레이 시킬지**

&#9656; 음수값도 가능함

### animation-iteration-count

**the number of times an animation should run**

&#9656; 숫자나 infinite로 무한반복시킬 수 있음

### animation-direction

**어느 방향으로 에니메이션이 진행되어야 하는지**

* normal : forwards (default)

* reverse : backwards

* alternate : forwards first, then backwards

* alternate-reverse : backwards first, then forwards

### animation-timing-function

**speed curve**

* ease : slow start, then fast, then end slowly (default)

* linear : same speed from start to end

* ease-in : slow start

* ease-out : slow end

* ease-in-out : slow start and end

* cubic-bezier(n,n,n,n) - Lets you define your own values in a cubic-bezier function

<span class="fs-2">
[W3C Example](https://www.w3schools.com/css/tryit.asp?filename=trycss3_animation_speed){: .btn .btn-outline }
</span>
    
### animation-fill-mode

**에니메이션이 시작되거나 끝나면 어떻게 마무리(시작) 되어야하는지**

&#9656; 원래 지정한 속성값이 처음에 지정한 애니메이션과 다르면 두가지 값이 동시에 나오는데, 이 값을 설정하면 애니메이션에서 설정한 값만을 실행함 (버벅거리지 않음)

* none : not apply any styles to the element before or after it is executing (default)

* forwards : retain the style values that is set by the last keyframe (depends on animation-direction and animation-iteration-count)

* backwards : get the style values that is set by the first keyframe (depends on animation-direction), and retain this during the animation-delay period

* both : The animation will follow the rules for both forwards and backwards, extending the animation properties in both directions

Shorthand animation property
{: .label .label-blue .mt-3}
```css
div {
    animation: name duration timing-function delay iteration-count direction;
}
```
