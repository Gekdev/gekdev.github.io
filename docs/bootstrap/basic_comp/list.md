---
layout: default
title: List
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 4
---

# Basic BT List
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## List Basic
    
### Default Setting

부트스트랩의 기본 목록 그룹의 CSS는 살짝 다름

&#9656; ul, ol, li의 왼쪽 20px, 하단 10px의 여백

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_default.html" height="800" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p>Use the ul element to indicate an unordered list:</p>
  <ul>
    <li>Coffee</li>
    <li>Tea
      <ul>
        <li>Black tea</li>
        <li>Green tea</li>
      </ul>
    </li>
    <li>Milk</li>
  </ul>
  
  <p>Use the ol element to indicate an ordered list:</p>
  <ol>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk
    	<ol>
        	<li>Chocolate</li>
            <li>Macha</li>
        </ol>
    </li>
  </ol>
  
  <p>Use the dl element to indicate a description list:</p>
  <dl>
    <dt>Coffee</dt>
    <dd>- black hot drink</dd>
    <dt>Milk</dt>
    <dd>- white cold drink</dd>
  </dl>    
</div>
```

### list-unstyled class

**목록 항목의 기본 목록 스타일 및 왼쪽 여백을 제거**

&#9656; ul, ol 모두 사용가능

부모객체에 선언한다고 자식 객체까지 스타일이 없어지는건 아님 (따로 설정해야 함)

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_unstyled.html" height="100" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p>The class .list-unstyled removes the default list-style and left margin on list items (immediate children only):</p>
  <ul class="list-unstyled">
    <li>Coffee</li>
    <li>Tea
      <ul>
        <li>Black tea</li>
        <li>Green tea</li>
      </ul>
    </li>
    <li>Milk</li>
  </ul>
</div>
```

### list-inline class

**모든 목록 항목을 한 줄에 배치**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_inline.html" height="100" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p>The class .list-inline places all list items on a single line:</p>
  <ul class="list-inline">
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
  </ul>
</div>
```

### dl-horizontal class

**dl, dt요소를 나란히 정렬**

&#9656; 화면이 작아지면 아래로 내리고, 커지면 나란히 정렬함

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_dl_hor.html" height="100" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p>Use the .dl-horizontal class line up the description list side-by-side when the browser window expands:</p>
  <dl class="dl-horizontal">
    <dt>Coffee</dt>
    <dd>- black hot drink</dd>
    <dt>Milk</dt>
    <dd>- white cold drink</dd>
  </dl>     
  <p><strong>Tip:</strong> Try to resize the browser window to see the behaviour of the description list.</p>      
</div>
```

---

## List Group

웹사이트의 서브페이지의 오른쪽/왼쪽에 위치한 서브메뉴를 구성할때 사용

### Basic List Groups

두가지로 구성가능

1. ul > li

2. div > a : 링크를 생성하고 싶을 때

    호버시 뒤 색상이 바뀜

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//부모 객체

class="list-group"

//자식 객체

class="list-group-item"
</div>
```html
//1. ul > li 로 생성하는 모습
<ul class="list-group">
     <li class="list-group-item">기본 목록 1</li>
     <li class="list-group-item">기본 목록 2</li>
     <li class="list-group-item">기본 목록 3</li>
</ul>

//2.div a 로 생성하는 모습
<div class="list-group">
    <a href="#" class="list-group-item active"> 기본 목록</a>
    <a href="#" class="list-group-item">기본 목록</a>
    <a href="#" class="list-group-item">기본 목록</a>
</div>
```

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_basic_listgroup.html" height="150" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Basic List Group</h2>
  <ul class="list-group">
    <li class="list-group-item">First item</li>
    <li class="list-group-item">Second item</li>
    <li class="list-group-item">Third item</li>
  </ul>
</div>
```

#### Active, Disabled class 

**리스트를 활성화 하거나 비활성화 시킬 때 사용함**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class= "list-group-item active"

* class= "list-group-item disable"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_ad.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Active Item in a List Group</h2>
  <div class="list-group">
    <a href="#" class="list-group-item active">First item</a>
    <a href="#" class="list-group-item">Second item</a>
    <a href="#" class="list-group-item">Third item</a>
  </div>
  
  <h2>List Group With a Disabled Item</h2>
  <div class="list-group">
    <a href="#" class="list-group-item disabled">First item</a>
    <a href="#" class="list-group-item">Second item</a>
    <a href="#" class="list-group-item">Third item</a>
  </div>
</div>
```

### List Group With Badges

목록 그룹에 배지를 추가, 자동으로 오른쪽으로 배치됨

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_bgs.html" height="200" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>List Group With Badges</h2>
  <ul class="list-group">
    <li class="list-group-item">New <span class="badge">12</span></li>
    <li class="list-group-item">Deleted <span class="badge">5</span></li>
    <li class="list-group-item">Warnings <span class="badge">3</span></li>
  </ul>
</div>
```

### Contextual Classes

**컨텍스트 클래스를 사용하여 목록 항목의 색상을 지정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class="list-group-item list-group-item-success" 

* class="list-group-item list-group-item-info" 

* class="list-group-item list-group-item-warning"

* class="list-group-item list-group-item-danger"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_cont.html" height="400" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>List Group With Contextual Classes</h2>
  <ul class="list-group">
    <li class="list-group-item list-group-item-success">First item</li>
    <li class="list-group-item list-group-item-info">Second item</li>
    <li class="list-group-item list-group-item-warning">Third item</li>
    <li class="list-group-item list-group-item-danger">Fourth item</li>
  </ul>
  
  <h2>Linked Items With Contextual Classes</h2>
  <p>Move the mouse over the linked items to see the hover effect:</p>
  <div class="list-group">
    <a href="#" class="list-group-item list-group-item-success">First item</a>
    <a href="#" class="list-group-item list-group-item-info">Second item</a>
    <a href="#" class="list-group-item list-group-item-warning">Third item</a>
    <a href="#" class="list-group-item list-group-item-danger">Fourth item</a>
  </div>
</div>
```

### Custom Content

목록 그룹 항목내에 거의 모든 HTML을 추가가능

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class="list-group-item-heading"

* class="list-group-item-text"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_lt_custom.html" height="200" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>List Group With Custom Content</h2>
  <div class="list-group">
    <a href="#" class="list-group-item active">
      <h4 class="list-group-item-heading">First List Group Item Heading</h4>
      <p class="list-group-item-text">List Group Item Text</p>
    </a>
    <a href="#" class="list-group-item">
      <h4 class="list-group-item-heading">Second List Group Item Heading</h4>
      <p class="list-group-item-text">List Group Item Text</p>
    </a>
    <a href="#" class="list-group-item">
      <h4 class="list-group-item-heading">Third List Group Item Heading</h4>
      <p class="list-group-item-text">List Group Item Text</p>
    </a>
  </div>
</div>
```
