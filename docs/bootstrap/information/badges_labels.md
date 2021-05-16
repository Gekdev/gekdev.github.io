---
layout: default
title: Badges & Label
parent: Information
grand_parent: Bootstrap
nav_order: 3
---

# Info Badges & Label
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Badges

### Badges Basic

**링크와 연결된 항목 수를 나타내는 숫자 표시기**

&#9656; 다른 요소에도 사용가능 (like 버튼)

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="badge"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/bg_basic.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Badges</h2>
  <a href="#">News <span class="badge">5</span></a><br>
  <a href="#">Comments <span class="badge">10</span></a><br>
  <a href="#">Updates <span class="badge">2</span></a>
  
  <h2>Badges on Buttons</h2>
  <button type="button" class="btn btn-primary">Primary <span class="badge">7</span></button>
  <button type="button" class="btn btn-success">Success <span class="badge">3</span></button>    
  <button type="button" class="btn btn-danger">Danger <span class="badge">5</span></button>   
</div>
```

---

## Label

### Label Basic

**무언가에 대한 추가정보를 제공하는 데 사용**

&#9656; span 태그로 만듦 

&#9656; 부모객체 크기에 영향을 받음

★ label 클래스와 label의 문맥클래스를 꼭 동시에 사용해야함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* span class="label label-default"

* span class="label label-primary"

* span class="label label-success"

* span class="label label-info"

* span class="label label-warning"

* span class="label label-danger"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/lb_basic.html" height="450" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Labels</h2>
  <h1>Example <span class="label label-default">New</span></h1>
  <h2>Example <span class="label label-default">New</span></h2>
  <h3>Example <span class="label label-default">New</span></h3>
  <h4>Example <span class="label label-default">New</span></h4>
  <h5>Example <span class="label label-default">New</span></h5>
  <h6>Example <span class="label label-default">New</span></h6>
  
  <h2>Contextual Label Classes</h2>
  <p>Contextual classes can be used to color the label.</p>  
  <span class="label label-default">Default Label</span>
  <span class="label label-primary">Primary Label</span>
  <span class="label label-success">Success Label</span>
  <span class="label label-info">Info Label</span>
  <span class="label label-warning">Warning Label</span>
  <span class="label label-danger">Danger Label</span>
</div>
```
