---
layout: default
title: Bootstrap
parent: CSS
nav_order: 14
---

# Bootstrap
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Bootstrap Basic

이 부트스트랩 파일은 직접 쓰면 이 블로그 CSS와 충돌이 일어나기 때문에 따로 빼서 작성했습니다

### Grid System

그리드는 총 **12열**로 구성

* 기기별 해상도에 따른 클래스 접두사

    | 모바일 (<768px)     | 태블릿 (>=768px)   | 데스트탑 (>=992px) | 와이드 (>=1200px)  |
    |:-------------------|:------------------|:------------------|:------------------|
    | .col-xs-           | .col-sm-          | .col-md-          | .col-lg-          |


* class="container"   

    **레이아웃을 감싸는 역할**
    
    좌우로 살짝 짤리는 부분 발생함

* class="container-fluid" 

    **무조건 전체 화면을 처리**

* class="row" 

    **한 행을 구성, 한 행은 총 12열**

    &#9656; 해상도가 1200px인 경우 자동으로 1170px로 변경
  
    &#9656; 해상도가 1200px보다 작게되면 970px로 변경 

* 중첩 그리드

    **하나의 그리드 내부에 또 그리드를 만들수 있음**
    
    &#9656; 내부에 만들어진 그리드는 또다시 12개의 그리드가 생성

* class="col-md-offset-?"  

    **그리드 사이의 offset**
    
    &#9656; offset 값 까지 더한 총 개수가 12가 되어야 함
  
    &#9656; 총합이 12를 넘겼을때는 아래로 내려감
  
    <div class="code-example" markdown="1">
    <img src="https://gekdev.github.io/assets/images/col-md-offset.jpg" alt="">
    </div>
    ```html
    <div class="row">
      <div class="col-md-5"></div>
      <div class="col-md-5 col-md-offset-2"></div>
    </div>
    ```
* class="col-md-push-?" / class="col-md-pull-?"

    레이아웃의 순서 바꾸기 **두개를 동시에 사용해야 함**
    
    ```html
    <div class="row">
      <div class="col-md-2 col-md-push-10"></div>
      <div class="col-md-10 col-md-pull-2"></div>
    </div>
    ```
    
* visible-xs ... , hidden-xs ... 

    특정 해상도에서 보임/숨김
    
    **모든 해상도 다 써줘야함 lg, mb, sm, xs**

#### Grid System Examples

* [그리드 샘플1-2단](https://gekdev.github.io/docs/css/bootstrap/grid-sample1.html)

* [그리드 샘플 2:8:2](https://gekdev.github.io/docs/css/bootstrap/grid-sample2.html)

* [그리드 중첩 3:9(7:5)](https://gekdev.github.io/docs/css/bootstrap/grid-Nesting -sample.html)

* [그리드 이해](https://gekdev.github.io/docs/css/bootstrap/grid2.html)

* [반응형 유틸리티](https://gekdev.github.io/docs/css/bootstrap/responsiveutil.html)

### [Typography](https://gekdev.github.io/docs/css/bootstrap/typo-sample.html)

* 부트스트랩의 타이포

  1. h1~h6  (36,30,24,18,14,12)의 고정 px 크기를 갖음

        `<small></small>` 태그 지정시  65%(h1~h3) 75%(h4~h6), 축소 색상은 #999

  2. `<p>` 
  
        하단에 자동으로 10px의 마진값 적용

  3. class="lead"  

        **단락의 첫 문장을 강조** 16px, 살짝 두꺼운 글꼴  
  
  4. 문단 정렬

        class="text-left", class="text-center", class="text-right"
  
  5. 다양한 강조클래스
  
        &#9656; class="text-muted" 

        &#9656; class="text-primary"

        &#9656; class="text-success" 

        &#9656; class="text-info"

        &#9656; class="text-warning" 

        &#9656; class="text-danger"
    
  6. `<abbr>` 

        **물음표와 원래 텍스트 표현**

        영문 약어는 abbr에 class="initialism" 를 추가하게 되면 단어가 소문자인 경우에도 영문 대문자로 
        변환되면서 글씨 크기는 90%정도로 변환
    
  7. 목록(list)

     &#9656; ul/ol/li : 왼쪽에 20px 하단으로 10px의 여백

     &#9656; .list-unstyled 클래스 선택자를 사용하면 왼쪽 20px 여백이 0으로 바뀜

     직접 위에 페이지 들어가서 보는걸 추천!
     
* 부트스트랩 기본 글꼴

    &#9656; helvetica neue , helvetica , arial , sans-serif 계열 글꼴 설정
  
    &#9656; 글꼴의 크기 14px
  
    &#9656; 행간 1.42857443
  
    &#9656; 글자색상 #333

    ```css
      body {
        font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
        font-size: 14px;
        line-height: 1.42857143;
        color: #333;
        background-color: #fff;
      }
    ```

* 브라우저에 따른 기본글꼴

    | 구글(크롬)          | 파이어폭스/IE11     | 맥(사파리)             | 맥(크롬)            | 
    |:-------------------|:------------------|:----------------------|:-------------------|
    | 한글 글꼴(굴림체)    | 한글 글꼴(맑은 고딕) | 한글 글꼴(산돌 고딕 Neo) | 한글 글꼴(애플 고딕) |


* 구글 폰트 사용

    @font-face{}
    
    ```css
    @font-face{
      font-family:'NanumBarunGothic';
      src:url("../fonts/NanumBarunGothic.eot");
      src:local("☺"),url("../fonts/NanumBarunGothic.woff") format("woff");
    }

    body { font-family: "Helvetica Neue", Helvetica, Arial,"NanumBarunGothic",  sans-serif; }
    ```
    
    or 
    
    ```css
    @import url(http://fonts.googleapis.com/earlyaccess/nanumgothic.css);

    body { font-family: "Helvetica Neue", Helvetica, Arial,'Nanum Gothic', sans-serif; }
    ```

### [Code](https://gekdev.github.io/docs/css/bootstrap/code-sample.html)

* 간단한 코드 표시

    `code` 태그 사용

* 행일 길 경우 
    
    `pre` 태그 사용
    
    `<pre class="pre-scrollable"></pre>`를 사용하면, 높이가 350px이 넘어가는 경우 자동으로 스크롤 생성

### [Table](https://gekdev.github.io/docs/css/bootstrap/table-sample.html)

* class="table"
    
    넓이가 100%인 테이블 생성, 행 사이에 보더 적용
    
* class="table table-striped"

    각 행에 색상(배경)을 줌
    
* class="table table-bordered"

    테이블 전체 테두리
    
* class="table table-hover"

    각 행에 마우스 오버시 색상에 오버 기능 추가
    
* class="table table-condensed"

    각행의 padding 값이 작아짐
    
* class="active" class="success" class="warning" class="danger" 

    각 셀에 색상을 지원
    
* div class="table-responsive"

    테이블을 감싸게 되면, 768px 이하의 사이즈에서 자동으로 테이블에 스크롤 바가 생성
    
* table class="table table-hover"

   호버시 색상 살짝 바뀜
       

### [Form 형태](https://gekdev.github.io/docs/css/bootstrap/form-sample.html)

* role="form"

    role값은 리더기가 읽어준다(접근성)

* class="form-control"

    넓이가 100%, 높이가 34px, 패딩 상하 6px 좌우 12px, border-radius:4px 적용
    
* class="form-group"

    하단에 15px의 마진이 생김

* 인라인 폼

    브라우져 너비가 커지면 한 라인으로 구성
    
    `<form role="form" class="form-inline"></form>`
  
* class="sr-only" 

    라벨을 화면에서 안보이게 할때 적용
    
    `<label for="Name" class="sr-only">이름</label>`

* class="form-horizontal" 
    
    라벨 오른쪽에 폼요소들을 배치
 
### [Form 형식](https://gekdev.github.io/docs/css/bootstrap/form-sample-2.html)


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
    
### [Image](https://gekdev.github.io/docs/css/bootstrap/image.html)

  (image.html)
 
* class="img-rounded" : 둥근 테두리

* class="img-circle" : 원형이미지

* class="img-thumbnail" : 썸네일 이미지

  `<img src="rose.jpg" alt="장미" class="img-thumbnail">`

* class="img-responsive" : 반응형 이미지(유동 사이즈)

  `<img src="puppy.jpg" alt="개양귀비" class="img-rounded img-responsive">`

### [Helper Class](https://gekdev.github.io/docs/css/bootstrap/etc.html)

* 닫기 버튼 

     <button type="button" class="close" aria-hidden="true">×</button>

* class="pull-right" ,  class="pull-left"

    박스모델 정렬(float과 같은 처리)
    
    ```html
    <section class="box1 pull-right">
         이 부분은 pull-right을 적용해 준 상태입니다. 따라서 오른쪽에 박스가 배치되어 있습니다. 
    </section>
    <section class="box1 pull-left">
         이 부분은 pull-left을 적용해 준 상태입니다. 따라서 왼쪽에 박스가 배치되어 있습니다. 
    </section> 
    ```
    
* clear:both 와 같은 처리

    ```html
    <div class="clearfix"></div>
    ```
 
* class="show" , class="hide"

    ```html
    <div class="show">여기 콘텐츠는 보입니다.</div>
    <div class="hide">여기 콘텐츠는 숨겨집니다.</div> 
     ```
 
* class="sr-only"

    ```html
    <a class="sr-only" href="#content">이 부분은 스크린 리더에서는 건너 뜁니다. </a>
    ```
    
* class="text-hide"

    텍스트는 숨기고 배경이미지로 대체 하는 방법(ir기법)
    
    ```html
    <style>
       .logo { background:url(logo.jpg) no-repeat; width: 317px; height: 60px; }
    </style>
    <h1 class="text-hide logo">9pixelstudio</h1>
    ```

* visible-xs ... , hidden-xs ...

    해상도에 따라 요소들을 감추거나 나타나게하는 클래스 선택자
    
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

*  visible-print , hidden-print

    프린트시 요소들을 감추거나 나타나게하는 클래스 선택자
   
    ```html
    <div class="visible-print box cl2">프린터로 출력하면 나오지만 화면에서는 안 나옴.</div>
    <div class="hidden-print box cl1">화면에서는 나오지만 프린터에서는 안 나옴 </div>
    ```
    
## Bootstrap Component

### Glyphicons

**특수문자 전용 글꼴처리**

[공식사이트](http://glyphicons.com)

<a href="https://gekdev.github.io/docs/css/bootstrap/glyphicons-sample.html"><img src="https://gekdev.github.io/assets/images/glyphicons-sample.jpg" alt=""></a>

* class="btn-group" 으로 묶어 사용할 수 있음

* 폰트이기 때문에 css로 컬러를 바꿀 수 있음

   ```html
    <style>
      .red { color: #FF0000}
    </style>
   ```

* 버튼의 스타일 변경

    class="btn-warning", class="btn-danger"  ...
    
    ```html
     <button type="button" class="btn btn-default btn-lg btn-warning">   
          <span class="glyphicon glyphicon-exclamation-sign"> </span> Info 
     </button>
    ```
    
### [Dropdown](https://gekdev.github.io/docs/css/bootstrap/dropdown.html)

* 단독으로 사용할 수 없고, 부트스트랩에 포함된 자바스크립트와 jQuery가 같이 있어야 동작

* ul class="dropdown-menu"
 
    ul/li로 구성된 리스트 태그에 적용
 
* 클릭 메뉴에 `<a data-toggle="dropdown">` 이 있어야 작동
 
    `<button>,<input type="button">`도 가능
    
* 상단 부분에 구분선 처리
 
    `<li role="presentation" class="divider"></li>`
    
* tabindex="-1"
    
    서브메뉴 부분에 tab키 적용을 받지 않게 하기위해 처리, 받으려면 생략


* class="pull-right"
  
   pull-right를 이용한 우측 정렬
  
   `<ul class="dropdown-menu pull-right" role="menu"> ... </ul>`

* class="dropdown-header"

    드롭다운에 별도의 헤더 추가 가능
   
   `<li role="presentation" class="dropdown-header">헤더 </li>`

* class="disabled"

    li 에 disabled 속성 추가로 비활성화 가능

   `<li role="presentation" class="disabled">`


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
    
### [Navigation](https://gekdev.github.io/docs/css/bootstrap/navigation.html)

* class="nav" 클래스 선택자를 사용한다.

* 탭형 네비게이션

    class="nav nav-tabs"   
    
    `<li class="active">` => 메뉴 활성화
    
    ```html
     <ul class="nav nav-tabs">
         <li><a href="#">메뉴1</a></li>
         <li class="active"><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li><a href="#">메뉴4</a></li>
     </ul>
    ```

* 알약형 네비게이션

    class="nav nav-pills"
    
    ```html
     <ul class="nav nav-pills">
         <li class="active"><a href="#">메뉴1</a></li>
         <li><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li><a href="#">메뉴4</a></li>
     </ul>
    ```

* 알약형 네비게이션은 수직으로 정렬 가능(탭형은 불가)

    class="nav nav-pills nav-stacked" 추가
    
    ```html
     <ul class="nav nav-pills nav-stacked">
         <li class="active"><a href="#">메뉴1</a></li>
         <li><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li><a href="#">메뉴4</a></li>
     </ul>
    ```
    
* 네비게이션 양쪽 정렬

     탭형 `<ul class="nav nav-tabs nav-justified">`
     
     알약형 `<ul class="nav nav-pills nav-justified">`

* class="disabled"을 이용한 링크 비활성화

    ```html
    <li class="disabled"><a href="#">메뉴3</a></li>
    ```

* 탭형 네비게이션 드롭다운

    ```html
    <ul class="nav nav-tabs">
         <li class="active"><a href="#">메뉴1</a></li>
         <li><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li class="dropdown">
               <a data-toggle="dropdown" href="#">여기 클릭 <span class="caret"></span></a>
               <ul class="dropdown-menu" role="menu">
                <li><a role="menuitem" href="#">메뉴 1</a></li>
                <li><a role="menuitem" href="#">메뉴 2</a></li>
                <li><a role="menuitem" href="#">메뉴 3</a></li>
                <li class="divider"></li>
                <li><a role="menuitem" href="#">분리된 메뉴 </a></li>
              </ul>
         </li>
     </ul>
    ```

* 알약형 형 네비게이션 드롭다운

    ```html
    <ul class="nav nav-pills">
         <li  class="active"><a href="#">메뉴1</a></li>
         <li><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li class="dropdown">
               <a data-toggle="dropdown" href="#">여기 클릭 <span class="caret"></span></a>
               <ul class="dropdown-menu" role="menu">
                <li><a role="menuitem" href="#">메뉴 1</a></li>
                <li><a role="menuitem" href="#">메뉴 2</a></li>
                <li><a role="menuitem" href="#">메뉴 3</a></li>
                <li class="divider"></li>
                <li><a role="menuitem" href="#">분리된 메뉴 </a></li>
              </ul>
         </li>
     </ul>
     ```
         
### Navigation bar(RWD) 

* 네비게이션 바(반응형 네비)

   1. html5의 `<nav>`요소를 사용
   
   2. `<nav class="navbar navbar-default">`를 적용한다.
   
   3. `<div class="navbar-header"></div>`  => 주로 사이트의 로고/모바일에서 변하지 않는 영역
   
   4. `<div class="collapse navbar-collapse navbar-ex1-collapse"></div>`
   
        => 모바일에서는 센드위치메뉴로 바뀌면서 서브를 열리는 형태로 처리한다  
   
* 기본 구조

    ```html
        <nav class="navbar navbar-default" role="navigation">
          <div class="navbar-header">
             .....  
          </div>
          <div class="collapse navbar-collapse navbar-ex1-collapse">
             .....
          </div>
        </nav>   
    ```
  
* [메뉴 위치를 오른쪽으로 이동하려면](https://gekdev.github.io/docs/css/bootstrap/navbar-right.html)

    class="navbar-right"를 추가
    
* [드롭다운을 적용한 네비게이션 바](https://gekdev.github.io/docs/css/bootstrap/navbar-dropdown.html)
   
* [드롭다운을 적용한 오른쪽 정렬 네비게이션 바](https://gekdev.github.io/docs/css/bootstrap/navbar-dropdown-right.html)
   
* [텍트스/버튼/링크처리](https://gekdev.github.io/docs/css/bootstrap/navbar-btn-text-link.html)
   
     - 단순 버튼  class="btn btn-default navbar-btn"
     
     - 텍스트  p태그사용  `<p class="navbar-text">텍스트</p>`
     
     - 단순 링크     `<a href="#" class="navbar-link">링크</a>`
     
* [상단/하단 고정](https://gekdev.github.io/docs/css/bootstrap/navbar-topfix.html)

* [네비게이션 바의 배경색과 텍스트 색상 반전](https://gekdev.github.io/docs/css/bootstrap/navbar-inverse.html)

* [네비게이션 바의 상단고정](https://gekdev.github.io/docs/css/bootstrap/navbar-inverse.html)

* [네비게이션 바의 상단고정 폼형식](https://gekdev.github.io/docs/css/bootstrap/navbar-inverse.html)

### [Pagination](https://gekdev.github.io/docs/css/bootstrap/brnpaging.html)

* 경로

    ol 태그에 class="breadcrumb" 지정

    ```html
      <ol class="breadcrumb">
         <li><a href="#">Home</a></li>
         <li><a href="#">menu1 </a></li>
         <li class="active">submenu</li>
     </ol>
    ```

* 페이지네이션

    ul 태그에 class="pagination" 지정
    
    ```html
    <ul class="pagination">
    <li><a href="#">&lt;</a></li>
    <li><a href="#">1</a></li>
    <li><a href="#">2</a></li>
    <li><a href="#">3</a></li>
    <li><a href="#">4</a></li>
    <li><a href="#">&gt;</a></li>
    </ul>
    ```

* 페이지네이션 활성 또는 비활성

   class="disabled" (비활성화) , class="active" (활성화)

    ```html
      <ul class="pagination">
         <li class="disabled"><a href="#">&lt;</a></li>
        <li class="active"><a href="#">1</a></li>
        <li><a href="#">2</a></li>
        <li><a href="#">3</a></li>
        <li><a href="#">4</a></li>
        <li><a href="#">5</a></li>
        <li><a href="#">&gt;</a></li>
     </ul>
    ```
    
* span을 이용해서 a 태그 제거

    ```html
    <li class="disabled"><span>&lt;</span></li>
    <li class="active"><span>1 <span class="sr-only">(current)</span></span></li>
    ```

* 크기조절    
    
     크게: `<ul class="pagination pagination-lg">`
     
     작게: `<ul class="pagination pagination-sm">`

* 가운데 정렬     

    ```html
    <ul class="pager">
      <li><a href="#">이전 페이지 </a></li>
      <li><a href="#">다음 페이지 </a></li>
    </ul>
    ```

* 양 끝 정렬

    ```html
     <ul class="pager">
        <li class="previous"><a href="#">← 이전 글 </a></li>
       <li class="next"><a href="#">새로운 글  →</a></li>
    </ul> 
    ```
    
* 비활성화

    ```html
     <ul class="pager">
        <li class="previous disabled"><a href="#">← 이전 글 </a></li>
        <li class="next"><a href="#">새로운 글 →</a></li>
    </ul>
    ```

### [Label](https://gekdev.github.io/docs/css/bootstrap/labelnbadge.html)

* 라벨 => span 태그로 만든다.   

    class="label label-default"

    ```html
    <span class="label label-default">Default</span>
    <span class="label label-primary">Primary</span>
    <span class="label label-success">Success</span>
    <span class="label label-info">Info</span>
    <span class="label label-warning">Warning</span>
    <span class="label label-danger">Danger</span>
    ```
    
* 배지

    `<span class="badge pull-right">42</span>`

### [Jumbotron](https://gekdev.github.io/docs/css/bootstrap/jumbotron.html)

* 웹사이트에서 중요한 내용 또는 공지사항 등을 부각

* 점보트론 내부의 글꼴크기 21px, 내부는 30px의 패딩값 적용, 배경색상 #eee

* `<div class="container">`  외부에 두면 넓이가 100%

    ```html
    <div class="jumbotron">
      <div class="container">
               ....
      </div>
    </div>

    <div class="container"> 
      <div class="jumbotron">
               ....
      </div>
    </div>
    ```

### [Pageheader](https://gekdev.github.io/docs/css/bootstrap/pageheader.html)

* 제목 부분이 본문과 선으로 분리

    ```html
    <div class="page-header">
    <h1> 여기는 페이지 제목 부분입니다.</h1>
    </div>
    ```
      
### [Thumbnail](https://gekdev.github.io/docs/css/bootstrap/thumbnail.html)

* class="thumbnail" 을 지정하고 그리드 시스템과 결합하여 사용

     ```html
     <div class="row">
     <div class="col-sm-6 col-md-3">
      <a href="#" class="thumbnail">
        <img src="DSC_6305.jpg" alt="...">
      </a>
     </div>
      <div class="col-sm-6 col-md-3">
      <a href="#" class="thumbnail">
        <img src="DSC_0374.jpg" alt="...">
      </a>
     </div>
      <div class="col-sm-6 col-md-3">
      <a href="#" class="thumbnail">
        <img src="DSC_5041.jpg" alt="...">
      </a>
     </div>
      <div class="col-sm-6 col-md-3">
      <a href="#" class="thumbnail">
        <img src="DSC_4999.jpg" alt="...">
      </a>
     </div>
     </div>
     ```
 
* class="caption" 을 사용해서 제목과 내용 등 다른 요소들도 추가 가능

    ```html
    <div class="caption">
        <h3>제목과 </h3>
        <p>내용도 넣을 수 있다.</p>
        <p><a href="#" class="btn btn-primary" role="button">Button</a> <a href="#" class="btn btn-default" role="button">Button</a></p>
    </div>
    ```
        
### [Alert](https://gekdev.github.io/docs/css/bootstrap/progressbar.html)
 
* 폼 양식에서 입력에 문제가 생겼거나 웹 페이지에서 주의할 내용을 강하게 알려줄 때 사용.

    ```HTML
    <div class="alert alert-success"></div>
    <div class="alert alert-info"></div>
    <div class="alert alert-warning"></div>
    <div class="alert alert-danger"></div>
    ```

* 없애기 버튼(X)과 .alert-dismissable 을 이용한 경보 없애기

    ```html
    <div class="alert alert-danger alert-dismissable">
         <button type="button" class="close" data-dismiss="alert" aria-hidden="true">×</button>
         <strong>경고!</strong> 입력하신 이메일이 존재하지 않습니다.
    </div>
    ```

* 경보내에 링크 처리는 .alert-link 선택자를 이용

    ```html
    <div class="alert alert-success alert-dismissable">
        <button type="button" class="close" data-dismiss="alert" aria-hidden="true">×</button>
        <strong>축하합니다.!</strong> 회원이 성공적으로 이뤄졌습니다.   <a href="#" class="alert-link">홈으로 돌아가기 </a>
    </div>
    ```
    
### [Progressbar](https://gekdev.github.io/docs/css/bootstrap/progressbar.html)

* `<div class="progress">`

* `<span class="sr-only">90% Complete</span>` 

    이 부분은 웹 접근성을 위해 필요 

    ```HTML
     <div class="progress">
         <div class="progress-bar" role="progressbar" aria-valuenow="90" aria-valuemin="0" aria-valuemax="100" 
            style="width: 90%;">
             <span class="sr-only">90% Complete</span>
         </div>
     </div>
     ```
  
* 색상 진행바
        
    &#9656; class="progress-bar progress-bar-success"
    
    &#9656; class="progress-bar progress-bar-info"
    
    &#9656; class="progress-bar progress-bar-warning"
    
    &#9656; class="progress-bar progress-bar-danger"

* 줄무늬

    `<div class="progress progress-striped">` 클래스를 추가
        
* 움직이는 바

    `<div class="progress progress-striped active">` 클래스를 추가

* 하나씩 쌓이는 바

    여러개의 `<div class="progress-bar>`를 사용
     
### [Media](https://gekdev.github.io/docs/css/bootstrap/media.html)

* `<div class="media">..</div>` 로 감싸줌

* `<a class="pull-left" href="#">`를 display:block으로 만들어줌

* `<div class="media-body">` 이 부분이 바디(본문) 부분, 내부에 `<div class="media">`추가하면 댓글 표현 가능

    ```html
    <div class="media">
      <a class="pull-left" href="#">
           <img class="media-object" src="pic.jpg" alt="...">
      </a>
      <div class="media-body">
            <h4 class="media-heading">Media heading</h4>
            여기는 기본내용이 들어가는 곳 입니다. Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
           Pellentesque non orci interdum, pharetra dui nec, eleifend ligula. Integer rutrum nunc a mi luctus vehicula. 
      </div>
    </div>
    ```

    ```html
      <div class="media">
          <a class="pull-left" href="#">
             <img class="media-object" src="pic.jpg" alt="...">
          </a>
          <div class="media-body">
               <h4 class="media-heading">Media heading</h4>
               여기는 기본내용이 들어가는 곳 입니다. Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
                Pellentesque non orci interdum, pharetra dui nec, eleifend ligula. Integer rutrum nunc a mi luctus vehicula. 
               <div class="media">
                    <a class="pull-left" href="#">
                          <img class="media-object" src="pic.jpg" alt="...">
                    </a>
                    <div class="media-body">
                        <h4 class="media-heading">Media heading</h4>
                         여기는 기본내용이 들어가는 곳 입니다. Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
                    </div>
              </div>
          </div>
      </div>
    ```

* `<h4 class="media-heading">Media heading</h4>` 부분은 생략할 수 있음

* div를 사용하는 방법과 ul/li를 사용하는 두가지 방법이 있음

* 목록 사진을 오른쪽으로 이동

    `<a class="pull-right">`

    ```HTML
    <div class="media">
       <a class="pull-right" href="#">
           <img alt="Generic placeholder image" src="pic.jpg">
       </a>
       <div class="media-body">
            <h4 class="media-heading">Media heading</h4>
            Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin commodo. 
       </div>
    </div>   
    ```      
        
### [List Group](https://gekdev.github.io/docs/css/bootstrap/list-group.html)

웹사이트의 서브페이지의 오른쪽/왼쪽에 위치한 서브메뉴를 구성할때 사용

ul/li , div a  의 두가지로 구성가능

```html
  <ul class="list-group">
     <li class="list-group-item">기본 목록 </li>
     <li class="list-group-item">기본 목록 2</li>
     <li class="list-group-item">기본 목록 3</li>
 </ul>

 <div class="list-group">
    <a href="#" class="list-group-item active"> 기본 목록  </a>
    <a href="#" class="list-group-item"> 기본 목록 </a>
    <a href="#" class="list-group-item">기본 목록 </a>
 </div>
 ```

* 배지가 있는  목록 그룹

    ```html
   <li class="list-group-item"><span class="badge">14</span> 배지가 있는 목록 그룹 </li>  
   또는
   <a href="#" class="list-group-item active"><span class="badge">14</span>  기본 목록  </a>
    ```

* 목록그룹 확장
 
    ```html
   <div class="list-group">
       <a href="#" class="list-group-item active">
           <h4 class="list-group-item-heading">여긴 제목 </h4>
           <p class="list-group-item-text">여긴 내용  </p>
       </a>
       <a href="#" class="list-group-item"> 기본 목록 </a>
       <a href="#" class="list-group-item"><span class="badge">14</span>기본 목록 </a>
       <a href="#" class="list-group-item">기본 목록 </a>
    </div>
    ```
     
### [Panel](https://gekdev.github.io/docs/css/bootstrap/panel.html)

DOM으로 처리된 부분에 박스를 만들어 줌

* 기본 패널 상단

    ```html
    <div class="panel panel-default">
         <div class="panel-heading">Panel heading without title</div>
         <div class="panel-body">
              Panel content
        </div>
    </div>
    ```

* 기본 패널 상단 h태그 이용 => <h3 class="panel-title">Panel title</h3>
        
    ```html
   <div class="panel panel-default">
     <div class="panel-heading">
        <h3 class="panel-title">Panel title</h3>
     </div>
     <div class="panel-body">
           Panel content
     </div>
   </div>
   ```

* 패널에 색상 적용 
     
     ```html
     <div class="panel panel-primary">
     <div class="panel panel-success">
     <div class="panel panel-info">
     <div class="panel panel-warning">
     <div class="panel panel-danger">
     ```

* 패널 내부에 테이블 적용 패널 내부에 panel-body 있는 경우와 없는 경우 아래 부분을 생략가능
 
    ```html
    <div class="panel-body">
         Panel content
    </div>
    ```
       
* 패널 내부에 리스트 그룹 적용

    ```html
    <div class="panel panel-default">
       <div class="panel-heading">패널 제목 </div>
        <div class="panel-body">
          Panel content
        </div>
       <ul class="list-group">
          <li class="list-group-item">기본 목록 </li>
          <li class="list-group-item">기본 목록 2</li>
          <li class="list-group-item">기본 목록 3</li>
       </ul>
    </div>
    ```

     
### [Wells](https://gekdev.github.io/docs/css/bootstrap/wells.html)

우물과 같이 박스가 움푹 파인 효과

```html
 <div class="well"> well 선택자는 안쪽으로 파인 효과를 내는 박스를 만들어 준다.</div>
 <div class="well well-lg"> 큰 박스는 well-lg를 적용하면 된다. </div>
 <div class="well well-sm"> 작은 박스는 well-sm을 적용하면 된다.</div>
```