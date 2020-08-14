---
layout: default
title: List & Table
parent: Elements
grand_parent: HTML
nav_order: 2
---

# List & Table
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## List basic 

### What is list?

**목차를 만드는 태그**

### Features of List

&#9656; Can be nested

&#9656; 다른 요소들을 포함할 수 있음

&#9656; 웹 접근성을 위해 네비게이션처럼 동일항목이 2개이상 중복된다면 거의 다 쓰인다 

### Basic form of list

```html
* Ordered list
<ol>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol> 

* Unordered list
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>

* Description List
<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>
  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```

---

## List elements

### &#60;ol&#62; 

**Ordered list**

* type attribute : define the numbering type (1, A, a, I, i)

* start attribute : control list counting

    ```html
    <ol start="50">
      <li>Coffee</li>
      <li>Tea</li>
      <li>Milk</li>
    </ol>

    <ol type="I" start="50">
      <li>Coffee</li>
      <li>Tea</li>
      <li>Milk</li>
    </ol>
    ```

### &#60;ul&#62; 

**Unordered list**

```html
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

### &#60;dl&#62; 

**Description Lists**

* &#60;dl&#62; : description list

* &#60;dt&#62; : defines a term 

* &#60;dd&#62; : describes the term

```html
<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>
  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```


---

## Table basic 

### What is table?

**표를 만드는 테그**

&#9656; 문법 []안에는 속성값, >뒤에는 하위값, *개수, +동일 항목 더하기

### Basic form of table

<div class="code-example" markdown="1">
<table style="width:100%">
    <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>Jill</td>
        <td>Smith</td>
        <td>50</td>
    </tr>
    <tr>
        <td>Eve</td>
        <td>Jackson</td>
        <td>94</td>
    </tr>
</table>
</div>
```html
<table style="width:100%">
    <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>Jill</td>
        <td>Smith</td>
        <td>50</td>
    </tr>
    <tr>
        <td>Eve</td>
        <td>Jackson</td>
        <td>94</td>
    </tr>
</table>
```

---

## Table elements

### &#60;table&#62;

**표**

* attribute

    &#9656; border
        
    &#9656; cellpadding
    
    &#9656; cellspacing
    
    &#9656; bgcolor
    
    &#9656; width

### &#60;tr&#62; 

**table row(열)**

* attribute 
    
    &#9656; height
    
    &#9656; bgcolor
    
    &#9656; align
    
### &#60;th&#62; 

**table header**

&#9656; 기본 CSS : bold, centered

* attribute : td attribute과 동일

### &#60;td&#62; 

**table data/cell**

&#9656; can contain all sorts of HTML elements; text, images, lists, other tables, etc.

&#9656; 기본 CSS : regular, left-aligned

* attribute 
    
    &#9656; width
    
    &#9656; height
    
    &#9656; bgcolor
    
    &#9656; align (left, center, right)
    
    &#9656; valign (top, middle, bottom) 
    
    &#9656; colspan
    
    &#9656; rowspan

### &#60;caption&#62; 

**caption to a table**

Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
The caption tag must be inserted immediately after the table tag
</div>

---

## Table Accessibility