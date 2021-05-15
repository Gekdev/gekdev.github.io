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

## Scrollspy Horizontal Menu

1. data-spy="scroll" : 스크롤 가능 영역으로 사용해야하는 요소에 추가

2. data-target(.navbar) 의 ID 또는 클래스 이름 값이 있는 속성(nav)을 추가 (navbar가 스크롤 가능 영역과 연결되어 있는지 확인하는 것)

3. navbar의 목록 항목에 있는 a 링크의 href값과 스크롤 가능한 요소의 ID와 일치해야함 (`<div id="section1"> = <a href="#section1">`) 

4. 선택적 data-offset속성은 스크롤 위치를 계산할 때 위에서 오프셋할 픽셀 수를 지정 (스크롤 가능한 요소로 이동할 때 탐색 모음 내부의 링크가 활성 상태를 너무 빨리 또는 너무 일찍 변경한다고 느낄 때 유용함, 기본값은 10 픽셀)

5. 상대 위치 지정 필요 : data-spy = "scroll"이있는 요소가 제대로 작동하려면 값이 "relative"인 CSS 위치 속성이 필요 (body position : relative)

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_spy_basic.html" height="400" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<!-- The scrollable area -->
<body data-spy="scroll" data-target=".navbar" data-offset="50">

    <!-- The navbar - The <a> elements are used to jump to a section in the scrollable area -->
    <nav class="navbar navbar-inverse navbar-fixed-top">
    ...
      <ul class="nav navbar-nav">
        <li><a href="#section1">Section 1</a></li>
        ...
    </nav>

    <!-- Section 1 -->
    <div id="section1">
      <h1>Section 1</h1>
      <p>Try to scroll this page and look at the navigation bar while scrolling!</p>
    </div>
    ...

</body>
```

---

## Scrollspy Vertical Menu

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_spy_vert.html" height="400" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<body data-spy="scroll" data-target="#myScrollspy" data-offset="20">

  <div class="container">
    <div class="row">
      <nav class="col-sm-3" id="myScrollspy">
        <ul class="nav nav-pills nav-stacked">
          <li><a href="#section1">Section 1</a></li>
          ...
        </ul>
      </nav>
      <div class="col-sm-9">
        <div id="section1">
          <h1>Section 1</h1>
          <p>Try to scroll this page and look at the navigation list while scrolling!</p>
        </div>
        ...
      </div>
    </div>
  </div>

</body>
```
