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