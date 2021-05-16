---
layout: default
title: Affix
parent: Plugin
grand_parent: Bootstrap
nav_order: 6
---

# Plugin Affix
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Affix

**페이지를 위아래로 스크롤 할 때 메뉴가 항상 표시되고 해당 위치에 고정**

탐색메뉴 또는 소셜아이콘 버튼과 함께 사용되어 페이지를 위아래로 스크롤하는 동안 특정 영역에 고정 되도록 함

스크롤 위치에 따라 동작을 켜고 끌 수 있음 (CSS position이 static에서 fixed로 변함)

1. 연결 플러그인은 .affix, .affix-top 및 .affix-bottom의 세 가지 클래스를 전환함. (각 클래스는 특정 상태를 나타냄) .affix 클래스에 fixed position을 제외하고 실제 위치를 처리하려면 CSS 속성을 추가해야 함

2. 플러그인은 .affix-top 또는 .affix-bottom 클래스를 추가하여 요소가 맨 위 또는 맨 아래 위치에 있음을 나타냄 (이 시점에서는 CSS로 위치를 지정할 필요가 없음)

3. 부착된 요소를 지나 스크롤하면 실제 부착이 트리거됨 여기서 플러그인은 .affix-top 또는 .affix-bottom 클래스를 .affix 클래스(설정 위치: fixed)로 바꿈. 이 때 CSS 상단 또는 하단 속성을 추가하여 부착된 요소를 페이지에 배치해야 함

4. 하단 오프셋이 정의된 경우, 이 오프셋을 지나 스크롤하면 .affix 클래스가 .affix-bottom으로 바뀜, (오프셋은 선택적이므로 하나를 설정하면 적절한 CSS를 설정해야 함) 이 경우 필요할 때 절대 위치를 추가

### How Affix works

```html
<!--  --> 
<nav class="navbar navbar-inverse" data-spy="affix" data-offset-top="197">
  <ul class="nav navbar-nav">
    <li class="active"><a href="#">Basic Topnav</a></li>
    <li><a href="#">Page 1</a></li>
    <li><a href="#">Page 2</a></li>
    <li><a href="#">Page 3</a></li>
  </ul>
</nav>

<div class="container-fluid" style="height:1000px">
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
  <h1>Some text to enable scrolling</h1>
</div>
```

1. 부착하려는 요소에 data-spy="affix"를 추가

2. 필요에 따라 data-offset-top|bottom속성을 추가 하여 스크롤 위치를 계산해 추가하면 그 위치부터 부착됨

위의 첫 번째 예에서 Apprite 플러그인은 상단에서 197픽셀을 스크롤했을 때 .affix 클래스(position:fixed)를 `<nav>` 요소에 추가. 예를 열면 0의 값을 가진 CSS 최상위 속성을 .afix 클래스에 추가한 것도 볼 수 있음. 이렇게 하면 상단에서 197픽셀을 스크롤했을 때 탐색 막대가 항상 페이지 맨 위에 있어야 함.

---

## Scrollspy & Affix

### Horizontal Menu (Navbar)

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_af_hor.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<body data-spy="scroll" data-target=".navbar" data-offset="50">

<div class="container-fluid" style="background-color:#F44336;color:#fff;height:200px;">
  <h1>Scrollspy & Affix Example</h1>
  <h3>Fixed navbar on scroll</h3>
  <p>Scroll this page to see how the navbar behaves with data-spy="affix" and data-spy="scrollspy".</p>
  <p>The navbar is attached to the top of the page after you have scrolled a specified amount of pixels, and the links in the navbar are automatically updated based on scroll position.</p>
</div>

<nav class="navbar navbar-inverse" data-spy="affix" data-offset-top="197">
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

</body>
```

### Vertical Menu (Sidenav)

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_af_ver.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<body data-spy="scroll" data-target="#myScrollspy" data-offset="15">

<div class="container-fluid" style="background-color:#2196F3;color:#fff;height:220px;">
  <h1>Scrollspy & Affix Example</h1>
  <h3>Fixed vertical sidenav on scroll</h3>
  <p>Scroll this page to see how the navbar behaves with data-spy="affix" and data-spy="scrollspy".</p>
  <p>The left menu sticks the page after you have scrolled a specified amount of pixels, and the links in the menu are automatically updated based on scroll position.</p>
</div>
<br>

<div class="container">
  <div class="row">
    <nav class="col-sm-3" id="myScrollspy">
      <ul class="nav nav-pills nav-stacked" data-spy="affix" data-offset-top="205">
        <li><a href="#section1">Section 1</a></li>
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

## Complete Bootstrap Affix Reference

For a complete reference of all affix methods and events, go to our [Bootstrap JS Affix Reference](https://www.w3schools.com/bootstrap/bootstrap_ref_js_affix.asp)