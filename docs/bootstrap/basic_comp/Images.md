---
layout: default
title: Images
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 2
---

# Basic Images
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

    
### [Image](https://gekdev.github.io/docs/css/bootstrap/image.html)

  (image.html)
 
* class="img-rounded" : 둥근 테두리

* class="img-circle" : 원형이미지

* class="img-thumbnail" : 썸네일 이미지

  `<img src="rose.jpg" alt="장미" class="img-thumbnail">`

* class="img-responsive" : 반응형 이미지(유동 사이즈)

  `<img src="puppy.jpg" alt="개양귀비" class="img-rounded img-responsive">`
  
  
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
        