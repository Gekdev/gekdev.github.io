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
  <img src="http://www.placehold.it/200" class="img-rounded" alt="Cinque Terre" width="304" height="236"> 
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
  <img src="http://www.placehold.it/200" class="img-circle" alt="Cinque Terre" width="304" height="236"> 
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
  <img src="http://www.placehold.it/200" class="img-thumbnail" alt="Cinque Terre" width="304" height="236"> 
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
  <img class="img-responsive" src="http://www.placehold.it/200" alt="Chania" width="460" height="345"> 
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






예
<img class="img-responsive" src="img_chania.jpg" alt="Chania">
이미지 갤러리
. 와 함께 Bootstrap의 그리드 시스템 을 사용하여 이미지 갤러리를 만들 수도 있습니다.

불빛
Lorem ipsum donec id elit non mi porta gravida at eget metus.

자연
Lorem ipsum donec id elit non mi porta gravida at eget metus.

피요르드
Lorem ipsum donec id elit non mi porta gravida at eget metus.

참고 : 이 자습서의 뒷부분에서 그리드 시스템에 대해 자세히 알아 봅니다 (다른 양의 열을 사용하여 레이아웃을 만드는 방법).

예
 <div class="row">
  <div class="col-md-4">
    <div class="thumbnail">
      <a href="/w3images/lights.jpg">
        <img src="/w3images/lights.jpg" alt="Lights" style="width:100%">
        <div class="caption">
          <p>Lorem ipsum...</p>
        </div>
      </a>
    </div>
  </div>
  <div class="col-md-4">
    <div class="thumbnail">
      <a href="/w3images/nature.jpg">
        <img src="/w3images/nature.jpg" alt="Nature" style="width:100%">
        <div class="caption">
          <p>Lorem ipsum...</p>
        </div>
      </a>
    </div>
  </div>
  <div class="col-md-4">
    <div class="thumbnail">
      <a href="/w3images/fjords.jpg">
        <img src="/w3images/fjords.jpg" alt="Fjords" style="width:100%">
        <div class="caption">
          <p>Lorem ipsum...</p>
        </div>
      </a>
    </div>
  </div>
</div>


* class="caption" 을 사용해서 제목과 내용 등 다른 요소들도 추가 가능

    ```html
    <div class="caption">
        <h3>제목과 </h3>
        <p>내용도 넣을 수 있다.</p>
        <p><a href="#" class="btn btn-primary" role="button">Button</a> <a href="#" class="btn btn-default" role="button">Button</a></p>
    </div>
    ```


반응 형 삽입
또한 비디오 또는 슬라이드 쇼를 모든 장치에서 적절하게 확장 할 수 있습니다.

클래스는 <iframe>, <embed>, <video> 및 <object> 요소에 직접 적용 할 수 있습니다.

다음 예제 .embed-responsive-item는 <iframe>태그에 클래스를 추가하여 반응 형 비디오를 만듭니다. 그러면 비디오가 상위 요소에 맞게 조정됩니다. 포함 <div>은 비디오의 종횡비 를 정의합니다.

예
<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>
종횡비 란 무엇입니까?

이미지의 가로 세로 비율은 너비와 높이 사이의 비례 관계를 나타냅니다. 두 가지 일반적인 비디오 종횡비는 4 : 3 (20 세기의 범용 비디오 형식)과 16 : 9 (HD TV 및 유럽 디지털 TV의 범용)입니다.

두 가지 종횡비 클래스 중에서 선택할 수 있습니다.

<!-- 16:9 aspect ratio -->
<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>

<!-- 4:3 aspect ratio -->
<div class="embed-responsive embed-responsive-4by3">
  <iframe class="embed-responsive-item" src="..."></iframe>
</div>


        