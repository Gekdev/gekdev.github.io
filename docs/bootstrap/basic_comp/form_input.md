---
layout: default
title: Form & Input
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 6
---

# Basic Form & Input
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Form Basic

### Bootstrap's Default Settings

부트스트랩 폼은 기본적으로 CSS를 가지고 있음

&#9656; input, textarea select에 form-control 클래스를 지정하면 width값은 100%가 됨

&#9656; 부트스트랩은 기본적으로 세가지 폼 레이아웃(버티컬 폼(기본), 세로 폼, 인라인 폼)을 제공함

### Form Layouts Rules

폼 레이아웃의 기본 룰

&#9656; 라벨과 폼을 div class="form-group"로 감싸야 함 (최적의 간격을 위해 필요)

&#8594; class="form-group"은 하단에 15px의 마진이 생김

&#9656; input, textarea, select 요소에 class="form-control"를 추가해야 함

&#8594; class="form-control"는 넓이가 100%, 높이가 34px, 패딩 상하 6px 좌우 12px, border-radius:4px 적용

---

## Three types of Form

부트스트랩은 기본적으로 세가지 폼 레이아웃(버티컬 폼(기본), 세로 폼, 인라인 폼)을 제공함

### Vertical Form (default)

**두 개의 입력 필드, 하나의 확인란 및 제출 버튼이있는 수직 양식**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_form_vert.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Vertical (basic) form</h2>
  <form action="/action_page.php">
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" class="form-control" id="email" placeholder="Enter email" name="email">
    </div>
    <div class="form-group">
      <label for="pwd">Password:</label>
      <input type="password" class="form-control" id="pwd" placeholder="Enter password" name="pwd">
    </div>
    <div class="checkbox">
      <label><input type="checkbox" name="remember"> Remember me</label>
    </div>
    <button type="submit" class="btn btn-default">Submit</button>
  </form>
</div>
```

### Inline Form

**인라인 양식에서 모든 요소는 인라인이고 왼쪽 정렬되며 레이블은 나란히 정렬됨**

&#9656; form 요소에서 form-inline 클래스를 추가해야 함

★ 너비가 768px 이상인 뷰포트 내의 양식에만 적용

&#9656; sr-only 클래스를 사용해서 웹 접근성 높히기, 라벨이 화면에서 안보이게 됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
form class="form-inline" 
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_form_inline.html" height="400" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
   <h2>Inline form</h2>
  <p>Make the viewport larger than 768px wide to see that all of the form elements are inline, left aligned, and the labels are alongside.</p>
  <form class="form-inline" action="/action_page.php">
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" class="form-control" id="email" placeholder="Enter email" name="email">
    </div>
    <div class="form-group">
      <label for="pwd">Password:</label>
      <input type="password" class="form-control" id="pwd" placeholder="Enter password" name="pwd">
    </div>
    <div class="checkbox">
      <label><input type="checkbox" name="remember"> Remember me</label>
    </div>
    <button type="submit" class="btn btn-default">Submit</button>
  </form>
  
  <hr>
  
  <h2>Inline form with .sr-only class</h2>
  <p>Make the viewport larger than 768px wide to see that all of the form elements are inline, left aligned, and the labels are alongside.</p>
  <form class="form-inline" action="/action_page.php">
    <div class="form-group">
      <label class="sr-only" for="email">Email:</label>
      <input type="email" class="form-control" id="email" placeholder="Enter email"  name="email">
    </div>
    <div class="form-group">
      <label class="sr-only" for="pwd">Password:</label>
      <input type="password" class="form-control" id="pwd" placeholder="Enter password" name="pwd">
    </div>
    <div class="checkbox">
      <label><input type="checkbox" name="remember"> Remember me</label>
    </div>
    <button type="submit" class="btn btn-default">Submit</button>
  </form>
</div>
```

### Horizontal Form

**대형 및 중간 화면에서 레이블이 입력 필드 (가로) 옆에 정렬됨**

&#9656; 작은 화면 (767px 이하)에서는 수직 형식으로 변환

&#9656; Tip: Use Bootstrap's predefined grid classes to align labels and groups of form controls in a horizontal layout

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
form class="form-horizontal" 

// 모든 label에 추가

label class ="control-label"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_form_hor.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Horizontal form</h2>
  <form class="form-horizontal" action="/action_page.php">
    <div class="form-group">
      <label class="control-label col-sm-2" for="email">Email:</label>
      <div class="col-sm-10">
        <input type="email" class="form-control" id="email" placeholder="Enter email" name="email">
      </div>
    </div>
    <div class="form-group">
      <label class="control-label col-sm-2" for="pwd">Password:</label>
      <div class="col-sm-10">          
        <input type="password" class="form-control" id="pwd" placeholder="Enter password" name="pwd">
      </div>
    </div>
    <div class="form-group">        
      <div class="col-sm-offset-2 col-sm-10">
        <div class="checkbox">
          <label><input type="checkbox" name="remember"> Remember me</label>
        </div>
      </div>
    </div>
    <div class="form-group">        
      <div class="col-sm-offset-2 col-sm-10">
        <button type="submit" class="btn btn-default">Submit</button>
      </div>
    </div>
  </form>
</div>
```

---

## Form Inputs

### Supported Form Controls

### Bootstrap Input

### Textarea

### Checkboxes

### Radio Buttons

### Select List

### Static Control

### Input Groups

### Form Control States

---

## Bootstrap Input Sizing
### Input Sizing in Forms
### Height Sizing
### Column Sizing
### Help Text


* textarea는 rows 값만 적용

    너비는 100%
 
    `<textarea  rows="5" class="form-control"></textarea>`


* class="checkbox-inline"

    인라인 체크 박스


* class="radio-inline"

    인라인 라디오

 
* p class="form-control-static"

    폼에 텍스트를 삽입 하기 위해

    form-control-static을 적용하지 않을 경우 텍스트가 label 부분과의 정렬이 틀어짐
  
    패딩 7px, 마진바텀 0px 
   
    `<p class="form-control-static">email@example.com</p>`

* disabled 

    비활성화 상태

  `<input type="text" class="form-control" disabled placeholder="이 부분은 disabled 상태입니다.">
  <fieldset disabled> ...  </fieldset>`

* input에 다양한 색 지정 클래스 선택자

  1. Input값이 성공적일(문제없을) 경우
  
     `<label class="control-label" for="inputSuccess">Input값이 성공적일(문제없을) 경우</label>`
  
  2. Input 값에 문제가 있어 경고를 내보낼 경우
  
     `<input type="text" class="form-control" id="inputWarning">`
     
  3. Input값에 에러가 있을 때
  
     `<input type="text" class="form-control" id="inputError">`

* input 크기 제어

    input-lg, 기본값, input-sm
    
    `<input type="text" class="form-control input-lg" placeholder="input-lg">`
    
    `<input type="text" class="form-control input-sm" placeholder="input-sm">`

* 그리드 시스템을 이용해서 컬럼 크기 조절

  `<div>` 태그로 감싼 후 클래스 선택자를 사용해서 처리

    ```html
    <div class="row">
          <div class="col-sm-2 col-lg-2">
            <input type="text" class="form-control" placeholder="">
          </div>
          <div class="col-sm-3  col-lg-3">
            <input type="text" class="form-control" placeholder="">
          </div>
          <div class="col-sm-4  col-lg-4">
            <input type="text" class="form-control" placeholder="">
          </div>
     </div> 
    ```

* input 부분에 대한 도움말

   `<span class="help-block">반드시 010-1234-5678 과 같은 형태로 입력해 주세요. </span>`
   
   
### [Input Group](https://gekdev.github.io/docs/css/bootstrap/inputgroup.html)

div class="input-group"

* `<input>`이 위치한 앞/뒤에 `<span class="input-group-addon"></span>` 을 추가하면 된다.

    ```html
    <div class="input-group">
        <span class="input-group-addon"> <span class="glyphicon glyphicon-user"> </span> </span>
        <input type="text" class="form-control" placeholder="아이디">
    </div>
    <div class="input-group">
        <input type="text" class="form-control">
        <span class="input-group-addon">  Cm  </span>
    </div> 
    ```
 
* 입력 그룹 크기조절

    class="input-group input-group-lg" , class="input-group input-group-sm"
    
    ```html
    <div class="input-group input-group-lg">...</div>
    ```

* 입력 그룹 체크 박스 또는 라디오 버튼 추가

    ```html
    <span class="input-group-addon">  <input type="checkbox"> </span>
    <span class="input-group-addon">  <input type="radio"> </span>
     ```
     
* 입력 그룹 버튼 애드온 추가 

    class="input-group-btn"
    
    ```html
    <span class="input-group-btn"> <button class="btn btn-default" type="button">Go!</button> </span>
    ```

* 입력 그룹 버튼 드롭다운 또는 드롭업 추가

    1. 드롭다운
    
        ```html
        <div class="input-group">
         <div class="input-group-btn"> 
             <button type="button" class="btn btn-default dropdown-toggle" data-toggle="dropdown"> 버튼1  <span class="caret"></span>
         </button>
           <ul class="dropdown-menu" role="menu">
            <li><a href="#">메뉴 1</a></li>
            <li><a href="#">메뉴 2</a></li>
            <li><a href="#">메뉴 3</a></li>
            <li class="divider"></li>
            <li><a href="#">다른 메뉴 </a></li>
          </ul>
         </div>        
        <input type="text" class="form-control">
        </div>
        ```

   2. 드롬업
   
        class="input-group-btn dropup"
        
        ```html
        <div class="input-group">
        <span class="input-group-addon"> <span class="glyphicon glyphicon-user"> </span> </span>            
        <input type="text" class="form-control">
          <div class="input-group-btn dropup"> 
             <button type="button" class="btn btn-default dropdown-toggle" data-toggle="dropdown"> 버튼1  <span class="caret"></span>
         </button>
           <ul class="dropdown-menu" role="menu">
            <li><a href="#">메뉴 1</a></li>
            <li><a href="#">메뉴 2</a></li>
            <li><a href="#">메뉴 3</a></li>
            <li class="divider"></li>
            <li><a href="#">다른 메뉴 </a></li>
          </ul>
         </div>         
        </div>
        ```
   