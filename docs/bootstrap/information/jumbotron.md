---
layout: default
title: Jumbotron
parent: Information
grand_parent: Bootstrap
nav_order: 1
---

# Info Jumbotron
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

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
