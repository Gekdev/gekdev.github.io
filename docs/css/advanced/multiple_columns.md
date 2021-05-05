---
layout: default
title: Multiple Columns
parent: Advanced
grand_parent: CSS
nav_order: 6
---

# Columns
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## CSS Multiple Columns Properties

### column-count

**몇 가지의 컬럼으로 나뉘어야 하는지 결정하는 속성**

```css
div {
  column-count: 3;
}

/*3단으로 나누기*/
```

### column-gap

**컬럼 사이의 갭 설정**

```css
div {
  column-gap: 40px;
}
```

### column-rule

**갭 스타일의 단축 프로퍼티**

```css
div {
  column-rule: 1px solid lightblue;
}
``

### column-rule-style

**갭의 스타일을 설정**

```css
div {
  column-rule-style: solid;
}
```

### column-rule-width

**갭의 두깨**

```css
div {
  column-rule-width: 1px;
}
```

### column-rule-color

**갭의 색상**

```css
div {
  column-rule-color: lightblue;
}
```

### column-span

요소가 몇개의 열에 걸쳐서 존재해야 하는지

예를들어, 3단으로 나눈 요소 안에 1단으로 존재해야 하는 제목이 있을 때 사용

```css
.newspaper {
  column-count: 3;
  column-gap: 40px;
  column-rule: 1px solid lightblue;
}

.newspaper h2 {
  column-span: all;
}
```

### column-width

**열의 너비를 지정**

현재 디바이스의 width값이 column-count * column-width값보다 작다면

column-width을 우선하여 표시함!

```css
div {
  column-width: 100px;
}
```
