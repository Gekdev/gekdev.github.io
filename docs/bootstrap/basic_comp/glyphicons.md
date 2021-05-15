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
    