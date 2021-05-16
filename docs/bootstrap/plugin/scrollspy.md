---
layout: default
title: Scrollspy
parent: Plugin
grand_parent: Bootstrap
nav_order: 5
---

# Plugin Scrollspy
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Scrollspy

### How Scrollspy works

```html
<!-- [1] [2] [4](scrollable area) --> 
<body data-spy="scroll" data-target=".navbar" data-offset="50">

    <!-- [2] -->
    <nav class="navbar navbar-inverse navbar-fixed-top">
    ...
      <ul class="nav navbar-nav">
        <!-- [3] -->
        <li><a href="#section1">Section 1</a></li>
        ...
    </nav>

    <!-- [3] -->
    <div id="section1">
      <h1>Section 1</h1>
      <p>Try to scroll this page and look at the navigation bar while scrolling!</p>
    </div>
    ...

</body>
```

1. data-spy="scroll" : 스크롤 가능 영역으로 사용해야하는 요소에 추가 (`body data-spy="scroll"`)

2. 스크롤 가능 영역에 있는(`body`) data-target(`.navbar`) 의 ID 또는 클래스값이 있는 속성(`nav`)을 추가 (navbar가 스크롤 가능 영역과 연결되어 있는지 확인하는 것)

3. navbar의 목록 항목에 있는 a 링크의 href값과 스크롤 가능한 요소의 ID와 일치해야함 (`<div id="section1"> = <a href="#section1">`) 

4. 선택적 data-offset속성은 스크롤 위치를 계산할 때 위에서 오프셋할 픽셀 수를 지정 (스크롤 가능한 요소로 이동할 때 탐색 모음 내부의 링크가 활성 상태를 너무 빨리 또는 너무 일찍 변경한다고 느낄 때 유용함, 기본값은 10 픽셀)

5. 상대 위치 지정 필요 : data-spy = "scroll"이있는 요소가 제대로 작동하려면 값이 "relative"인 CSS 위치 속성이 필요 (`body position : relative`)

### Scrollspy Horizontal Menu

&#9656; width 값이 768px 미만이 되면 메뉴가 햄버거 버튼으로 바뀜

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_spy_basic.html" height="400" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<body data-spy="scroll" data-target=".navbar" data-offset="50">

<nav class="navbar navbar-inverse navbar-fixed-top">
  <div class="container-fluid">
    <div class="navbar-header">
        <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#myNavbar">
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>                        
      </button>
      <a class="navbar-brand" href="#">WebSiteName</a>
    </div>
    <div>
      <div class="collapse navbar-collapse" id="myNavbar">
        <ul class="nav navbar-nav">
          <li><a href="#section1">Section 1</a></li>
          <li><a href="#section2">Section 2</a></li>
          <li><a href="#section3">Section 3</a></li>
          <li class="dropdown"><a class="dropdown-toggle" data-toggle="dropdown" href="#">Section 4 <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#section41">Section 4-1</a></li>
              <li><a href="#section42">Section 4-2</a></li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </div>
</nav>    

<div id="section1" class="container-fluid">
  <h1>Section 1</h1>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
</div>
<div id="section2" class="container-fluid">
  <h1>Section 2</h1>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
</div>
<div id="section3" class="container-fluid">
  <h1>Section 3</h1>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
</div>
<div id="section41" class="container-fluid">
  <h1>Section 4 Submenu 1</h1>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
</div>
<div id="section42" class="container-fluid">
  <h1>Section 4 Submenu 2</h1>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
  <p>Try to scroll this section and look at the navigation bar while scrolling! Try to scroll this section and look at the navigation bar while scrolling!</p>
</div>
```

### Scrollspy Vertical Menu

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_spy_vert.html" height="400" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<body data-spy="scroll" data-target="#myScrollspy" data-offset="20">

<div class="container">
  <div class="row">
    <nav class="col-sm-3" id="myScrollspy">
      <ul class="nav nav-pills nav-stacked">
        <li class="active"><a href="#section1">Section 1</a></li>
        <li><a href="#section2">Section 2</a></li>
        <li><a href="#section3">Section 3</a></li>
        <li class="dropdown">
          <a class="dropdown-toggle" data-toggle="dropdown" href="#">Section 4 <span class="caret"></span></a>
          <ul class="dropdown-menu">
            <li><a href="#section41">Section 4-1</a></li>
            <li><a href="#section42">Section 4-2</a></li>                     
          </ul>
        </li>
      </ul>
    </nav>
    <div class="col-sm-9">
      <div id="section1">    
        <h1>Section 1</h1>
        <p>Try to scroll this section and look at the navigation list while scrolling!</p>
      </div>
      <div id="section2"> 
        <h1>Section 2</h1>
        <p>Try to scroll this section and look at the navigation list while scrolling!</p>
      </div>        
      <div id="section3">         
        <h1>Section 3</h1>
        <p>Try to scroll this section and look at the navigation list while scrolling!</p>
      </div>
      <div id="section41">         
        <h1>Section 4-1</h1>
        <p>Try to scroll this section and look at the navigation list while scrolling!</p>
      </div>      
      <div id="section42">         
        <h1>Section 4-2</h1>
        <p>Try to scroll this section and look at the navigation list while scrolling!</p>
      </div>
    </div>
  </div>
</div>

</body>
```

---

## Complete Bootstrap Scrollspy Reference

For a complete reference of all scrollspy methods and events, go to our [Bootstrap JS Scrollspy Reference](https://www.w3schools.com/bootstrap/bootstrap_ref_js_scrollspy.asp)
