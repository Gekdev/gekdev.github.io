---
layout: default
title: Class
parent: Grid
grand_parent: Bootstrap
nav_order: 1
---

# Grid Class
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Grid Classes

### Grid Device Classes

&#9656; 4개의 그리드 클래스를 가지고 있음

&#9656; 그리드 클래스를 가지고 동적인 레이아웃 제작이 가능함

&#9656; 한가지 접두사만을 사용하고 디바이스 가로값이 변경되었을 때 그 접두사보다 작은 디바이스 요소의 레이아웃은 100%로 확장됨 (위로는 유지됨)

&#9656; 각 클래스는 확장되므로 xs 및 sm에 대해 동일한 너비를 설정하려면 xs만 지정

* xs : 핸드폰, 768px 미만

* ms : 태블릿, 768px 이상

* md : 작은 노트북, 992px 이상

* lg : 컴퓨터(노트북), 1200px 이상

기기별 해상도에 따른 클래스 접두사
{: .label .mt-2}

| 모바일 (<768px)    | 태블릿 (>=768px)   | 데스트탑 (>=992px) | 와이드 (>=1200px)  |
|:-------------------|:------------------|:------------------|:------------------|
| .col-xs-           | .col-sm-          | .col-md-          | .col-lg-          |

예시
{: .label .mt-2 .label-purple}
```html
<div class="row">
  <div class="col-xs-7 col-sm-6 col-lg-8">.col-xs-7 .col-sm-6 .col-lg-8</div>
  <div class="col-xs-5 col-sm-6 col-lg-4">.col-xs-5 .col-sm-6 .col-lg-4</div>
</div>

<div class="row">
  <div class="col-xs-6 col-sm-8 col-lg-10">.col-xs-6 .col-sm-8 .col-lg-10</div>
  <div class="col-xs-6 col-sm-4 col-lg-2">.col-xs-6 .col-sm-4 .col-lg-2</div>
</div>
```

### container

**레이아웃을 감싸는 역할**

좌우로 살짝 짤리는 부분 발생함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="container"
</div>

### container-fluid

**무조건 전체 화면을 처리**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="container-fluid"
</div>

<span class="fs-2">
[W3School](https://www.w3schools.com/bootstrap/tryit.asp?filename=trybs_grid_container-fluid&stacked=h){: .btn .btn-outline .mt-2}
</span>

### row

**한 행을 구성, 한 행은 총 12열**

&#9656; 해상도가 1200px인 경우 자동으로 1170px로 변경

&#9656; 해상도가 1200px보다 작게되면 970px로 변경 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="row"
</div>

### row-no-gutters

**행과 열에서 거터를 제거함**

&#9656; 그래서 사용하면 양 옆으로 마진 값이 생김

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="row row-no-gutters"
</div>

<span class="fs-2">
[W3School](https://www.w3schools.com/bootstrap/tryit.asp?filename=trybs_grid_no-gutters&stacked=h){: .btn .btn-outline .mt-2}
</span>

### offset 

**그리드 사이의 여백**

&#9656; offset 값까지 더한 총 개수가 12가 되어야 함

&#9656; 총합이 12를 넘겼을때는 아래로 내려감

&#9656; 여백은 왼쪽으로 생성됨!

<img src="https://gekdev.github.io/assets/images/col-md-offset.jpg" alt="">

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="col-md-offset-?"
</div>
```html
<div class="row">
    <div class="col-md-5"></div>
    <div class="col-md-5 col-md-offset-2"></div>
</div>
```

<span class="fs-2">
[W3School](https://www.w3schools.com/bootstrap/tryit.asp?filename=trybs_grid_ex8&stacked=h){: .btn .btn-outline .mt-2}
</span>

### push and pull

**레이아웃의 순서 바꾸기**

★ 두개를 동시에 사용해야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="col-md-push-?"

and 

class="col-md-pull-?"
</div>
```html
<div class="row">
    <div class="col-md-2 col-md-push-10"></div>
    <div class="col-md-10 col-md-pull-2"></div>
</div>
```

<span class="fs-2">
[W3School](https://www.w3schools.com/bootstrap/tryit.asp?filename=trybs_grid_ex9&stacked=h){: .btn .btn-outline .mt-2}
</span>

### pull-right and left

**박스모델 정렬(float과 같은 처리)**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="pull-right"

or

class="pull-left"
</div>
```html
<section class="box1 pull-right">
      이 부분은 pull-right을 적용해 준 상태입니다. 따라서 오른쪽에 박스가 배치되어 있습니다. 
</section>
<section class="box1 pull-left">
      이 부분은 pull-left을 적용해 준 상태입니다. 따라서 왼쪽에 박스가 배치되어 있습니다. 
</section> 
  ```

### visible and hidden

**특정 해상도에서 보임/숨김**

★ 모든 해상도(lg, mb, sm, xs) 다 써줘야함 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="visible-xs"

or

class="hidden-xs"
</div>
```html
<div class="container">  
    <div class="visible-xs box cl1">.visible-xs (모바일폰) 해상도가 768px이하 에서 보임  </div>
    <div class="visible-sm box cl1">.visible-sm (태블릿) 해상도가 768px 보다 크거나 같은 경우에서 보임</div>
    <div class="visible-md box cl1">.visible-md (데스크탑) 해상도가 992px보다 크거나 같은 경우에서 보임 </div>
    <div class="visible-lg box cl1">.visible-lg (데스크탑) 해상도가1200px보다 크거나 같은 경우에서 보임</div>

    <div class="hidden-xs box cl2">.hidden-xs (모바일폰) 해상도가 768px이하에서 감춰짐  </div>
    <div class="hidden-sm box cl2">.hidden-sm (태블릿) 해상도가 768px 보다 크거나 같은 경우 감춰짐 </div>
    <div class="hidden-md box cl2">.hidden-md (데스크탑) 해상도가 992px보다 크거나 같은 경우 감춰짐 </div>
    <div class="hidden-lg box cl2">.hidden-lg (데스크탑) 해상도가1200px보다 크거나 같은 경우 감춰짐 </div> 
</div>
```

### show and hide

**보임/숨김**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="show"

or

class="hide"
</div>
```html
<div class="show">여기 콘텐츠는 보입니다.</div>
<div class="hide">여기 콘텐츠는 숨겨집니다.</div> 
```

### text-hide

**텍스트는 숨기고 배경이미지로 대체 = IR기법**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="text-hide"
</div>
```html
<style>
    .logo { background:url(logo.jpg) no-repeat; width: 317px; height: 60px; }
</style>
<h1 class="text-hide logo">9pixelstudio</h1>
```

### sr-only

**스크린 리더에서는 건너 뜀**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="sr-only"
</div>
```html
<div class="sr-only" >이 부분은 스크린 리더에서는 건너 뜁니다. </div>
```

###  visible-print , hidden-print

**프린트시 요소들을 감추거나 나타나게함**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="visible-print"

or

class="hidden-print"
</div>
```html
<div class="visible-print box cl2">프린터로 출력하면 나오지만 화면에서는 안 나옴</div>
<div class="hidden-print box cl1">화면에서는 나오지만 프린터에서는 안 나옴</div>
```

### clearfix

**고르지 않은 콘텐츠로 이상한 래핑을 방지하기 위해 특정 해상도에서 clear: both같은 효과를 줌**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="clearfix"
</div>

<span class="fs-2">
[W3School](https://www.w3schools.com/bootstrap/tryit.asp?filename=trybs_grid_ex7&stacked=h){: .btn .btn-outline .mt-2}
</span>
