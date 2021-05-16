---
layout: default
title: Glyphicons
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 8
---

# Basic Glyphicons
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Glyphicons

**특수문자 전용 글꼴처리**

&#9656; 텍스트, 버튼, 도구 모음, 탐색, 양식 등에서 사용

&#9656; 폰트이기 때문에 css로 컬러를 바꿀 수 있음

<span class="fs-2">
[공식사이트](http://glyphicons.com){: .btn .btn-outline .mt-2}
</span>

### Glyphicon Syntax

&#9656; glyphicon-name은 아이콘에 따라 달라짐

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
&#60;span class="glyphicon glyphicon-name"&#62;&#60;/span&#62;  
</div>

### Glyphicons Example

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_gly_ex.html" height="400" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Glyphicon Examples</h2>
  <p>Envelope icon: <span class="glyphicon glyphicon-envelope"></span></p>
  <p>Envelope icon as a link:
    <a href="#"><span class="glyphicon glyphicon-envelope"></span></a>
  </p>
  <p>Search icon: <span class="glyphicon glyphicon-search"></span></p>
  <p>Search icon on a button:
    <button type="button" class="btn btn-default">
      <span class="glyphicon glyphicon-search"></span> Search
    </button>
  </p>
  <p>Search icon on a styled button:
    <button type="button" class="btn btn-info">
      <span class="glyphicon glyphicon-search"></span> Search
    </button>
  </p>
  <p>Print icon: <span class="glyphicon glyphicon-print"></span></p>      
  <p>Print icon on a styled link button:
    <a href="#" class="btn btn-success btn-lg">
      <span class="glyphicon glyphicon-print"></span> Print 
    </a>
  </p> 
</div>
```
