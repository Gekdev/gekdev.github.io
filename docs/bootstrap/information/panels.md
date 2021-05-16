---
layout: default
title: Panels
parent: Information
grand_parent: Bootstrap
nav_order: 2
---

# Info Panels
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Panels

### Panel Basic

**내용 주위에 약간의 패딩이있는 테두리가 있는 상자**

&#9656; 자식 객체에 헤딩, 바디(필수사항), 푸터를 넣을 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//부모 객체 

class="panel"

//자식 객체

class="panel-body"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/pn_basic.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Panel</h2>
  <div class="panel panel-default">
    <div class="panel-heading">Panel Heading</div>
    <div class="panel-body">Panel Content</div>
    <div class="panel-footer">Panel Footer</div>
  </div>
</div>
```

### Panel Group

**여러 패널을 그룹화하려면 패널들을 부모 객체에 panel-group으로 묶음**

&#9656; panel-group클래스는 각 패널의 하단 여백을 지움

&#9656; 리스트 그룹을 사용해 패널 안에 리스트를 넣을수도 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//제일 상위 객체

class="panel-group"
  
  ..패널들

</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/pn_group.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Panel Group</h2>
  <p>The panel-group class clears the bottom-margin. Try to remove the class and see what happens.</p>
  <div class="panel-group">
    <div class="panel panel-default">
      <div class="panel-heading">Panel Header</div>
      <div class="panel-body">Panel Content</div>
    </div>
    <div class="panel panel-default">
      <div class="panel-heading">Panel Header</div>
      <div class="panel-body">Panel Content</div>
    </div>
    <div class="panel panel-default">
      <div class="panel-heading">Panel Header</div>
      <div class="panel-body">Panel Content</div>
    </div>
    <div class="panel panel-default">
       <div class="panel-heading">패널 제목 </div>
       <div class="panel-body">
          패널 내용
       </div>
       <ul class="list-group">
          <li class="list-group-item">기본 목록 </li>
          <li class="list-group-item">기본 목록 2</li>
          <li class="list-group-item">기본 목록 3</li>
       </ul>
    </div>
  </div>
</div>
```

### Contextual Classes Panels

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class="panel panel-default"

* class="panel panel-primary"

* class="panel panel-success"

* class="panel panel-info"

* class="panel panel-warning"

* class="panel panel-danger"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/pn_cont.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Panels with Contextual Classes</h2>
  <div class="panel-group">
    <div class="panel panel-default">
      <div class="panel-heading">Panel with panel-default class</div>
      <div class="panel-body">Panel Content</div>
    </div>

    <div class="panel panel-primary">
      <div class="panel-heading">Panel with panel-primary class</div>
      <div class="panel-body">Panel Content</div>
    </div>

    <div class="panel panel-success">
      <div class="panel-heading">Panel with panel-success class</div>
      <div class="panel-body">Panel Content</div>
    </div>

    <div class="panel panel-info">
      <div class="panel-heading">Panel with panel-info class</div>
      <div class="panel-body">Panel Content</div>
    </div>

    <div class="panel panel-warning">
      <div class="panel-heading">Panel with panel-warning class</div>
      <div class="panel-body">Panel Content</div>
    </div>

    <div class="panel panel-danger">
      <div class="panel-heading">Panel with panel-danger class</div>
      <div class="panel-body">Panel Content</div>
    </div>
  </div>
</div>
```
