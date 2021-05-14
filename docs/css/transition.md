---
layout: default
title: Transition
parent: CSS
nav_order: 11
---

# CSS Transition
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Transitions

### What is Transitions?

**Property values를 시간을 주고 부드럽게 움직이게 하는것**

&#9656; 필수요소 : 원하는 프로퍼티, 지속시간(default : 0)

---

## Transition Properties

기본형식
{: .label .mt-3}
```css
div {
  width: 100px;
  height: 100px;
  background: red;
  transition: width 2s;
}

div:hover {
  width: 300px;
}

```

### transition

**단축프로퍼티**

```css
div {
  transition: property duration timing-function delay;
}
```

### transition-delay

**딜레이 걸기**

### transition-duration

**지속시간**

### transition-property

**트랜지션 걸 프로퍼티**

### transition-timing-function

**스피드 커브 설정**

* ease : a transition effect with a slow start, then fast, then end slowly (this is default)

* linear : a transition effect with the same speed from start to end

* ease-in : a transition effect with a slow start

* ease-out : a transition effect with a slow end

* ease-in-out : a transition effect with a slow start and end

* cubic-bezier(n,n,n,n) : define your own values in a cubic-bezier function

<span class="fs-2">
[W3C Example](https://www.w3schools.com/css/tryit.asp?filename=trycss3_transition_speed){: .btn .btn-outline }
</span>
