---
layout: default
title: Carousel
parent: Plugin
grand_parent: Bootstrap
nav_order: 1
---

# Plugin Carousel
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Carousel

### How Carousel works

```html
<!--[1]-->
<div id="myCarousel" class="carousel slide" data-ride="carousel">
  <!-- Indicators [2]-->
  <ol class="carousel-indicators">
    <li data-target="#myCarousel" data-slide-to="0" class="active"></li>
    <li data-target="#myCarousel" data-slide-to="1"></li>
    <li data-target="#myCarousel" data-slide-to="2"></li>
  </ol>

  <!-- Wrapper for slides [3]-->
  <div class="carousel-inner">
    <div class="item active">
      <img src="la.jpg" alt="Los Angeles">
    </div>

    <div class="item">
      <img src="chicago.jpg" alt="Chicago">
    </div>

    <div class="item">
      <img src="ny.jpg" alt="New York">
    </div>
  </div>

  <!-- Left and right controls [4]-->
  <a class="left carousel-control" href="#myCarousel" data-slide="prev">
    <span class="glyphicon glyphicon-chevron-left"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="right carousel-control" href="#myCarousel" data-slide="next">
    <span class="glyphicon glyphicon-chevron-right"></span>
    <span class="sr-only">Next</span>
  </a>
</div>
```

1. 가장 바깥 쪽 &#60;div&#62; 

    * id="myCarousel" : Carousel이 작동해야 하는 div에 선언, **Carousel 컨트롤이 제대로 작동(함수)하게 만듦**

    * class="carousel" : div가 Carousel을 포함한다는 걸 명시

    * class="slide" : CSS 전환 및 애니메이션 효과를 추가하여 새 항목을 표시 할 때 항목이 슬라이드 되도록 함. 이 효과를 원하지 않으면이 클래스를 생략

    * data-ride="carousel" 속성은 페이지가 로드 될 때 즉시 Carousel 애니메이션을 시작하도록 Bootstrap에 지시

2. Indicators

    **Indicators : 각 슬라이드의 하단에있는 작은 점 (Carousel에 있는 슬라이드 수와 사용자가 현재보고있는 슬라이드를 나타냄)**

    * 정렬 목록과 함께 .carousel-indicators로 선언함

    * data-target="#" : Carousel의 ID를 가리킴
    
    * data-slide-to="number" : 특정 점을 클릭 할 때 어디로 이동해야 하는지 하는 슬라이드 속성 지정

3. Wrapper for slides

    **슬라이드는 div의 .carousel-inner로 지정**

    * class="item" : 각 슬라이드의 내용을 정의, 텍스트 또는 이미지
    
        &#8594; 이곳에 캡션을 추가할 수 있음

    * class="active" : **최초값, 최소 하나 값이 필요한 꼭 필요한 속성, 없으면 캐 러셀이 표시되지 않음**

4. Left and right controls

    **사용자가 슬라이드 사이를 수동으로 앞뒤로 이동할 수있는 버튼**

    * data-slide="" : 키워드 "prev" 또는 "next"를 수락하여 현재 위치에 비해 슬라이드 위치를 변경

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
슬라이드 효과를 얻기 위해 CSS3 전환 및 애니메이션을 사용하기 때문에 Internet Explorer 9 및 이전 버전에서는 carousel이 제대로 지원되지 않음
</div>

### Add Captions to Slides

item 클래스가 있는 곳에 div class="carousel-caption을 추가해 캡션을 넣을 수 있음

```html
    <div class="item">
      <img src="chicago.jpg" alt="Chicago">
      <div class="carousel-caption">
        <h3>Chicago</h3>
        <p>Thank you, Chicago!</p>
      </div>
    </div>
```

### Carosel Basic Example

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_car_cap.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Carousel Example</h2>  
  <div id="myCarousel" class="carousel slide" data-ride="carousel">
    <!-- Indicators -->
    <ol class="carousel-indicators">
      <li data-target="#myCarousel" data-slide-to="0" class="active"></li>
      <li data-target="#myCarousel" data-slide-to="1"></li>
      <li data-target="#myCarousel" data-slide-to="2"></li>
    </ol>

    <!-- Wrapper for slides -->
    <div class="carousel-inner">
      <div class="item active">
        <img src="la.jpg" alt="Los Angeles" style="width:100%;">
      </div>

      <div class="item">
        <img src="chicago.jpg" alt="Chicago" style="width:100%;">
      </div>
    
      <div class="item">
        <img src="ny.jpg" alt="New york" style="width:100%;">
      </div>
    </div>

    <!-- Left and right controls -->
    <a class="left carousel-control" href="#myCarousel" data-slide="prev">
      <span class="glyphicon glyphicon-chevron-left"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a class="right carousel-control" href="#myCarousel" data-slide="next">
      <span class="glyphicon glyphicon-chevron-right"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>
</div>
```
 