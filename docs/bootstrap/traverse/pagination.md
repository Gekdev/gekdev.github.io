---
layout: default
title: Pagination
parent: Traverse
grand_parent: Bootstrap
nav_order: 4
---

# Traverse Pagination
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

    
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