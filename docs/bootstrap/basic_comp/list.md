---
layout: default
title: List
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 4
---

# Basic List Group
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

    
  7. 목록(list)

     &#9656; ul/ol/li : 왼쪽에 20px 하단으로 10px의 여백

     &#9656; .list-unstyled 클래스 선택자를 사용하면 왼쪽 20px 여백이 0으로 바뀜

     직접 위에 페이지 들어가서 보는걸 추천!
     
     https://www.w3schools.com/bootstrap/bootstrap_typography.asp
     
https://www.w3schools.com/bootstrap/bootstrap_ref_css_text.asp

<ul>	Indicates an unordered list	
<ol>
### <dl>


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