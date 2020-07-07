---
layout: default
title: Counters
parent: Advanced
grand_parent: CSS
nav_order: 3
---

# Counters
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## CSS Counters
{: .no_toc}

### What are Counters?

카운터는 변수와 같은것

CSS규칙에 따라 변수값이 올라감 (얼마나 사용했느냐를 셈)

자동으로 앞에 숫자를 달아줌!

### Basic form of Counters

```css
body {
  counter-reset: section;
}

h2::before {
  counter-increment: section;
  content: "Section " counter(section) ": ";
}

/*결과물로 h2 앞에 Section n: ... 이렇게 나옴*/
```

### Counter Properties

* counter-reset 

    **Creates or resets a counter**
    
    가장 먼저 생성되어야 하는 속성
    
    ```css
    body {
      counter-reset: section;
    }
    ```
    
* counter-increment

    **Increments a counter value**

* content

    **Inserts generated content**

* counter() or counters() function 

    **Adds the value of a counter to an element**

### Nesting Counters

section1의 subsection 1,2,3으로 만들고싶을때 사용

```css
body {
  counter-reset: section;
}

h1 {
  counter-reset: subsection;
}

h1::before {
  counter-increment: section;
  content: "Section " counter(section) ". ";
}

h2::before {
  counter-increment: subsection;
  content: counter(section) "." counter(subsection) " ";
}
```

### Using Counters

[자세히 확인하기](https://www.w3schools.com/css/tryit.asp?filename=trycss_counters3)

```css
ol {
  counter-reset: section;
  list-style-type: none;
}

li::before {
  counter-increment: section;
  content: counters(section,".") " ";
}

/*결과물로 1 1.1 1.2 ... 2*/
```
