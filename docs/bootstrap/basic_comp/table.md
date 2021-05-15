---
layout: default
title: Table
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 5
---

# Basic BT Table
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Table Class

### table 

**넓이가 100%인 테이블 생성, 행 사이에 보더 적용**

&#9656; 기본 부트 스트랩 테이블에는 밝은 패딩과 수평 구분선만 있음

&#9656; .table클래스는 테이블에 기본 스타일만 추가

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
table class="table"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_tb_table.html" height="280" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Basic Table</h2>
  <p>The .table class adds basic styling (light padding and only horizontal dividers) to a table:</p>            
  <table class="table">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
  </table>
</div>
```

### table-striped 

**스트라이프 행**

&#9656; 테이블에 얼룩말 줄무늬를 추가

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
table class="table table-striped"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_tb_striped.html" height="300" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Striped Rows</h2>
  <p>The .table-striped class adds zebra-stripes to a table:</p>            
  <table class="table table-striped">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
  </table>
</div>
```

### table-bordered 

**경계선이 있는 표**

&#9656; 표와 셀의 모든면에 테두리를 추가

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
table class="table table-bordered"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_tb_bordered.html" height="300" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Bordered Table</h2>
  <p>The .table-bordered class adds borders to a table:</p>            
  <table class="table table-bordered">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
  </table>
</div>
```

### table-hover 

**호버할 수 있는 행**

&#9656; 클래스는 테이블 행에 호버 효과 (회색 배경 색상)을 추가

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
table class="table table-hover"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_tb_hover.html" height="300" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Hover Rows</h2>
  <p>The .table-hover class enables a hover state on table rows:</p>            
  <table class="table table-hover">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
  </table>
</div>
```

### table-condensed 

**압축된 테이블**

&#9656; 각 행의 padding을 반으로 줄여 테이블을 더 간결하게 만듦

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
table class="table table-bordered"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_tb_condensed.html" height="270" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Bordered Table</h2>
  <p>The .table-bordered class adds borders to a table:</p>            
  <table class="table table-bordered">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
  </table>
</div>
```

---

## tr, td Class

### Contextual Classes

**상황별 클래스**

상황별 클래스로 테이블 행(<tr>) 또는 테이블 셀(<td>)의 색상을 지정

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class="success" : 성공적인 작업 또는 긍정적인 작업

* class="danger" : 위험하거나 잠재적으로 부정적인 조치

* class="info" : 중립적인 정보 변경 또는 조치

* class="warning" : 주의가 필요할 수 있는 경고

* class="active" : 테이블 행 또는 테이블 셀에 호버 색상을 적용
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_tb_contextual.html" height="450" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Contextual Classes</h2>
  <p>Contextual classes can be used to color table rows or table cells. 
  The classes that can be used are: .active, .success, .info, .warning, and .danger.</p>
  <table class="table">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Default</td>
        <td>Defaultson</td>
        <td>def@somemail.com</td>
      </tr>      
      <tr class="success">
        <td>Success</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr class="danger">
        <td>Danger</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr class="info">
        <td>Info</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
      <tr class="warning">
        <td>Warning</td>
        <td>Refs</td>
        <td>bo@example.com</td>
      </tr>
      <tr class="active">
        <td>Active</td>
        <td>Activeson</td>
        <td>act@example.com</td>
      </tr>
    </tbody>
  </table>
</div>
```

---

## Responsible table 

### table-responsive 

**반응형 테이블**

&#9656; 테이블이 소형 장치 (768px 미만)에서 가로로 스크롤됨, (768px보다 큰 화면에서 볼 때 차이가 없음)

&#9656; 테이블을 감싸는 부모 요소에 클래스를 집어넣어야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
div class="table-responsive"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_tb_responsive.html" height="230" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Table</h2>
  <p>The .table-responsive class creates a responsive table which will scroll horizontally on small devices (under 768px).
  When viewing on anything larger than 768px wide, there is no difference:</p>                                                                                      
  <div class="table-responsive">          
  <table class="table">
    <thead>
      <tr>
        <th>#</th>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Age</th>
        <th>City</th>
        <th>Country</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>1</td>
        <td>Anna</td>
        <td>Pitt</td>
        <td>35</td>
        <td>New York</td>
        <td>USA</td>
      </tr>
    </tbody>
  </table>
  </div>
</div>
```
