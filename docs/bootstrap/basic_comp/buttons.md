---
layout: default
title: Buttons
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 3
---

# Basic Buttons
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Single Button  

### Button Styles

**a, button, input태그에 사용될 수 있음**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class="btn" : 다양한 버튼 효과

* class="btn btn-default" : 기본 버튼 모양

* class="btn btn-primary" : 중요한 버튼

* class="btn btn-success" : 긍정적 의미의 버튼

* class="btn btn-info" : 정보제공 버튼

* class="btn btn-warning" : 주의를 알리는 버튼

* class="btn btn-danger" : 위험을 나타내는 버튼

* class="btn btn-link" : 단순 링크로 처리하는 버튼
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_bt_style.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Button Styles</h2>
  <button type="button" class="btn">Basic</button>
  <button type="button" class="btn btn-default">Default</button>
  <button type="button" class="btn btn-primary">Primary</button>
  <button type="button" class="btn btn-success">Success</button>
  <button type="button" class="btn btn-info">Info</button>
  <button type="button" class="btn btn-warning">Warning</button>
  <button type="button" class="btn btn-danger">Danger</button>
  <button type="button" class="btn btn-link">Link</button>
  <hr>
  <h2>Button Tags</h2>
  <a href="#" class="btn btn-info" role="button">Link Button</a>
  <button type="button" class="btn btn-info">Button</button>
  <input type="button" class="btn btn-info" value="Input Button">
  <input type="submit" class="btn btn-info" value="Submit Button">      
</div>    
```

링크에 #사용이유
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
링크 할 페이지가없고 "404"메시지를 받고 싶지 않을 때 자주 사용
</div>

### Button Sizes

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class="btn btn-lg" : 큰 버튼 btn-lg

* class="btn btn-sm" : 작은 버튼

* class="btn btn-xs" : 아주 작은 버튼
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_bt_size.html" height="100" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Button Sizes</h2>
  <button type="button" class="btn btn-primary btn-lg">Large</button>
  <button type="button" class="btn btn-primary">Normal</button>    
  <button type="button" class="btn btn-primary btn-sm">Small</button>
  <button type="button" class="btn btn-primary btn-xs">XSmall</button>
</div>
```

### Block Level Buttons

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="btn btn-block" : 화면 전체 버튼 (width:100%)
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_bt_block.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Block Level Buttons</h2>
  <button type="button" class="btn btn-primary btn-block">Button 1</button>
  <button type="button" class="btn btn-default btn-block">Button 2</button>

  <h2>Large Block Level Buttons</h2>
  <button type="button" class="btn btn-primary btn-lg btn-block">Button 1</button>
  <button type="button" class="btn btn-default btn-lg btn-block">Button 2</button>

  <h2>Small Block Level Buttons</h2>
  <button type="button" class="btn btn-primary btn-sm btn-block">Button 1</button>
  <button type="button" class="btn btn-default btn-sm btn-block">Button 2</button>
</div>
```

### Active/Disabled Buttons

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class="btn btn-primary active" : 활성화

* class="btn btn-primary disabled" : 비활성화
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_bt_active.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Button States</h2>
  <button type="button" class="btn btn-primary">Primary Button</button>
  <button type="button" class="btn btn-primary active">Active Primary</button>
  <button type="button" class="btn btn-primary disabled">Disabled Primary</button>
</div>
```

---

## Button Groups

### Button Groups & Size

**버튼들을 하나의 묶음으로 만들어주는 것**

&#9656; 버튼들이 가로로 배치되고 간격은 0

&#9656; 버튼들을 붙잡고 있는 부모 객체에 주어야함

&#9656; .btn-group-lg|sm|xs으로 크기를 지정할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class = "btn-group"

//sizing

class = "btn-group-lg|sm|xs"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_btg_basic.html" height="450" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Button Groups - Set Sizes</h2>
  <p>Add class .btn-group-* to size all buttons in a button group.</p>
  <h3>Default Buttons:</h3>
  <div class="btn-group">
    <button type="button" class="btn btn-primary">Apple</button>
    <button type="button" class="btn btn-primary">Samsung</button>
    <button type="button" class="btn btn-primary">Sony</button>
  </div>
  <h3>Large Buttons:</h3>
   <div class="btn-group btn-group-lg">
    <button type="button" class="btn btn-primary">Apple</button>
    <button type="button" class="btn btn-primary">Samsung</button>
    <button type="button" class="btn btn-primary">Sony</button>
  </div>
  <h3>Small Buttons:</h3>
  <div class="btn-group btn-group-sm">
    <button type="button" class="btn btn-primary">Apple</button>
    <button type="button" class="btn btn-primary">Samsung</button>
    <button type="button" class="btn btn-primary">Sony</button>
  </div>
  <h3>Extra Small Buttons:</h3>
  <div class="btn-group btn-group-xs">
    <button type="button" class="btn btn-primary">Apple</button>
    <button type="button" class="btn btn-primary">Samsung</button>
    <button type="button" class="btn btn-primary">Sony</button>
  </div>
</div>
```

### Vertical Button Groups





* class="btn-toolbar"

    버튼 그룹을 툴바 형식으로 변환 (좌우배치)  
    

* data-toggle="dropdown"

    중첩하기(버튼 클릭시 드롭다운)

    반드시 드롭다운이 적용되는 버튼에 class="dropdown-toggle"을 주어야함
    
    클릭 메뉴에 data-toggle="dropdown" 이 있어야 작동함


* btn-group-vertical

    수직정렬 하기

    `<div class="btn-group">` => `<div class="btn-group-vertical">`

*  btn-group-justified

    양쪽 정렬 하기
    
    `<a>` 태그로 이루어진 버튼에 한해서만 가능
   
    `<div class="btn-group  btn-group-justified">`

### Button Dropdown

* class="btn dropdown-toggle" 선택자를 btn 클래스 선택자가 적용된 부분에 같이 사용

    둥근모서리 사각형이 적용되지 않음

* `<span class="caret"></span>`
  
  역삼각형 영역이 만들어짐
    
   ```html
   <button type="button" class="btn btn-default dropdown-toggle" data-toggle="dropdown">
     버튼1<span class="caret"></span>
   </button>
   ```
  
* 일반적인 버튼 드롭다운

    ```html
    <div class="btn-group">
         <button type="button" class="btn btn-default dropdown-toggle" data-toggle="dropdown">
            버튼1   <span class="caret"></span>
         </button>
       <ul class="dropdown-menu" role="menu">
        <li><a href="#">메뉴 1</a></li>
        <li><a href="#">메뉴 2</a></li>
        <li><a href="#">메뉴 3</a></li>
      </ul>
    </div> 
    ```
 
* 분할된 버튼 드롭 다운

    ```html
    <div class="btn-group">
          <button type="button" class="btn btn-default"> 버튼1 </button> 
          <button type="button" class="btn btn-default dropdown-toggle" data-toggle="dropdown">
          <span class="caret"></span>
         </button>
       <ul class="dropdown-menu" role="menu">
        <li><a href="#">메뉴 1</a></li>
        <li><a href="#">메뉴 2</a></li>
        <li><a href="#">메뉴 3</a></li>
      </ul>
    </div>
    ```

* 버튼 드롭 다운 크기 조절

    class="btn btn-lg",  class="btn btn-sm"
    
    ```html
    <button type="button" class="btn btn-default btn-lg"> 버튼1 </button> 
    <button type="button" class="btn btn-default btn-lg dropdown-toggle" data-toggle="dropdown">
        <span class="caret"></span>
    </button>
    ```
    
* 드롭업(위로 열리는 드롭다운)

    `<div class="btn-group dropup"> ...  </div>`
    
    ```html
    <div class="btn-group dropup">
         <button type="button" class="btn btn-default dropdown-toggle" data-toggle="dropdown">
             버튼1   <span class="caret"></span>
         </button>
       <ul class="dropdown-menu" role="menu">
        <li><a href="#">메뉴 1</a></li>
        <li><a href="#">메뉴 2</a></li>
        <li><a href="#">메뉴 3</a></li>
        <li class="divider"></li>
        <li><a href="#">다른 메뉴 </a></li>
      </ul>
    </div>
    ```