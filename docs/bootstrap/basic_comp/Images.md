---
layout: default
title: Images
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 2
---

# Basic BT Images
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Image Shape Class

**부트 스트랩 이미지 모양**

### img-rounded

**둥근 테두리**

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

### img-circle

**둥근 테두리**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
img class="img-circle" 
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_img_circle.html" height="280" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Circle</h2>
  <p>The .img-circle class shapes the image to a circle (not available in IE8):</p>            
  <img src="newyork.jpg" class="img-circle" alt="Cinque Terre" width="304" height="236"> 
</div>
```

### img-thumbnail

**둥근 테두리**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
img class="img-thumbnail"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_img_thumb.html" height="280" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Thumbnail</h2>
  <p>The .img-thumbnail class creates a thumbnail of the image:</p>            
  <img src="sanfran.jpg" class="img-thumbnail" alt="Cinque Terre" width="304" height="236"> 
</div>
```

---

## Responsive Image Class

### img-responsive

**반응형 이미지는 화면 크기에 맞게 자동으로 크기를 조정**

&#9656; 상위 요소에 맞게 조정

&#9656; 이미지에 **display: block; max-width: 100%; height: auto;** CSS 적용한 것과 같음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
img class="img-responsive"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_img_responsive.html" height="280" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Image</h2>
  <p>The .img-responsive class makes the image scale nicely to the parent element (resize the browser window to see the effect):</p>
  <img class="img-responsive" src="img_chania.jpg" alt="Chania" width="460" height="345"> 
</div>
```

---

## Image Technic

### Image Gallery

thumbnail 클래스와 그리드 시스템을 동시에 사용해 이미지 갤러리를 만들 수 있음

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_img_gallery.html" height="350" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Image Gallery</h2>
  <p>The .thumbnail class can be used to display an image gallery.</p>
  <p>The .caption class adds proper padding and a dark grey color to text inside thumbnails.</p>
  <p>Click on the images to enlarge them.</p>
  <div class="row">
    <div class="col-md-4">
      <div class="thumbnail">
        <a href="lights.jpg" target="_blank">
          <img src="lights.jpg" alt="Lights" style="width:100%">
          <div class="caption">
            <p>Lorem ipsum donec id elit non mi porta gravida at eget metus.</p>
          </div>
        </a>
      </div>
    </div>
    <div class="col-md-4">
      <div class="thumbnail">
        <a href="nature.jpg" target="_blank">
          <img src="nature.jpg" alt="Nature" style="width:100%">
          <div class="caption">
            <p>Lorem ipsum donec id elit non mi porta gravida at eget metus.</p>
          </div>
        </a>
      </div>
    </div>
    <div class="col-md-4">
      <div class="thumbnail">
        <a href="fjords.jpg" target="_blank">
          <img src="fjords.jpg" alt="Fjords" style="width:100%">
          <div class="caption">
            <p>Lorem ipsum donec id elit non mi porta gravida at eget metus.</p>
          </div>
        </a>
      </div>
    </div>
  </div>
</div>
```

#### caption class

**제목과 내용 등 다른 요소들도 추가 가능**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="caption"
</div>
```html
...
<div class="col-md-4">
    <div class="thumbnail">
        <a href="fjords.jpg" target="_blank">
          <img src="fjords.jpg" alt="Fjords" style="width:100%">
          <div class="caption">
            <h3>제목과 </h3>
            <p>내용도 넣을 수 있다.</p>
            <p>
                <a href="#" class="btn btn-primary" role="button">Button</a> 
                <a href="#" class="btn btn-default" role="button">Button</a>
            </p>
          </div>
        </a>
    </div>
</div>
...
```

### Responsive Embeds

**비디오 또는 슬라이드 쇼를 모든 장치에서 적절하게 확장**

&#9656; 클래스는 `<iframe>`, `<embed>`, `<video>`, `<object>` 요소에 직접 적용 할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//부모 객체 비율 선언

div class="embed-responsive embed-responsive-16by9"

//자식 객체(like iframe) 반응형 선언

class : "embed-responsive-item"
</div>


What is aspect ratio?
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
**이미지의 가로 세로 비율은 너비와 높이 사이의 비례 관계를 나타냄**

일반적인 비디오 종횡비는 4 : 3 (20 세기의 범용 비디오 형식),
16 : 9 (HD TV 및 유럽 디지털 TV의 범용) 두가지가 있음

두 가지 종횡비 클래스 중에서 선택할 수 있음
</div>
<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_img_ratio.html" height="1300" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<!-- 16:9 aspect ratio -->
<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>

<!-- 4:3 aspect ratio -->
<div class="embed-responsive embed-responsive-4by3">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>
```
