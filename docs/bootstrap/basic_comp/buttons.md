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

### 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
img class="img-rounded"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_img_rounded.html" height="280" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Rounded Corners</h2>
  <p>The .img-rounded class adds rounded corners to an image (not available in IE8):</p>            
  <img src="cinqueterre" class="img-rounded" alt="Cinque Terre" width="304" height="236"> 
</div>
```


### [Button](https://gekdev.github.io/docs/css/bootstrap/button.html)

* class="btn" : 다양한 버튼 효과

* class="btn btn-default" : 기본 버튼 모양

* class="btn btn-primary" : 중요한 버튼

* class="btn btn-success" : 긍정적 의미의 버튼

* class="btn btn-info" : 정보제공 버튼

* class="btn btn-warning" : 주의를 알리는 버튼

* class="btn btn-danger" : 위험을 나타내는 버튼

* class="btn btn-link" : 단순 링크로 처리하는 버튼

* class="btn btn-lg" : 큰 버튼 btn-lg

* class="btn btn-sm" : 작은 버튼

* class="btn btn-xs" : 아주 작은 버튼

* class="btn btn-block" : 화면 전체 버튼 (width:100%)

* disabled : 버튼 작동 불가능

    ```html
     <button type="button" class="btn btn-default" disabled="disabled" >버튼 작동 안함 </button>
     <input type="submit" class="btn btn-default" value="버튼 작동 안함" disabled>
     <a href="#" class="btn btn-default" disabled="disabled" >버튼 작동 안함 </a>
    ```
    
    
    
* 닫기 버튼 

     <button type="button" class="close" aria-hidden="true">×</button>

### [Button Group](https://gekdev.github.io/docs/css/bootstrap/buttongrp.html)

버튼들이 가로로 배치되고 간격은 0 한 묶음

버튼들을 `<div class="btn-group">`로 묶음

```html
<div class="btn-group">
   <button type="button" class="btn btn-default">버튼 1 </button>
   <button type="button" class="btn btn-default">버튼 2 </button>
   <button type="button" class="btn btn-default">버튼 3 </button>
   <button type="button" class="btn btn-default">버튼 4 </button>
</div>
```    
    
* class="btn-toolbar"

    버튼 그룹을 툴바 형식으로 변환 (좌우배치)  
    
     
* class="btn-group btn-group-lg" , btn-group-sm, btn-group-xs

  버튼 그룹을 이용해서 버튼 크기 일괄 조절

* data-toggle="dropdown"

    중첩하기(버튼 클릭시 드롭다운)

    반드시 드롭다운이 적용되는 버튼에 class="dropdown-toggle"을 주어야함
    
    클릭 메뉴에 data-toggle="dropdown" 이 있어야 작동함

    ```html
   <div class="btn-group">
       <button type="button" class="btn btn-default">버튼 1 </button>
       <button type="button" class="btn btn-default">버튼 2 </button>
        <div class="btn-group">     
           <button type="button" data-toggle="dropdown" class="btn btn-default dropdown-toggle"> 클릭 <span class="caret"> </span>
           </button>
           <ul class="dropdown-menu">
            <li><a tabindex="-1" href="#">메뉴 1</a></li>
            <li><a tabindex="-1" href="#">메뉴 2</a></li>
          </ul>
        </div>
    </div>
    ``` 

* btn-group-vertical

    수직정렬 하기

    `<div class="btn-group">` => `<div class="btn-group-vertical">`

*  btn-group-justified

    양쪽 정렬 하기
    
    `<a>` 태그로 이루어진 버튼에 한해서만 가능
   
    `<div class="btn-group  btn-group-justified">`

### [Button Dropdown](https://gekdev.github.io/docs/css/bootstrap/buttondropdown.html)

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