---
layout: default
title: Progress Bar
parent: Information
grand_parent: Bootstrap
nav_order: 4
---

# Info Progress Bar
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

    
### [Progressbar](https://gekdev.github.io/docs/css/bootstrap/progressbar.html)

* `<div class="progress">`

* `<span class="sr-only">90% Complete</span>` 

    이 부분은 웹 접근성을 위해 필요 

    ```HTML
     <div class="progress">
         <div class="progress-bar" role="progressbar" aria-valuenow="90" aria-valuemin="0" aria-valuemax="100" 
            style="width: 90%;">
             <span class="sr-only">90% Complete</span>
         </div>
     </div>
     ```
  
* 색상 진행바
        
    &#9656; class="progress-bar progress-bar-success"
    
    &#9656; class="progress-bar progress-bar-info"
    
    &#9656; class="progress-bar progress-bar-warning"
    
    &#9656; class="progress-bar progress-bar-danger"

* 줄무늬

    `<div class="progress progress-striped">` 클래스를 추가
        
* 움직이는 바

    `<div class="progress progress-striped active">` 클래스를 추가

* 하나씩 쌓이는 바

    여러개의 `<div class="progress-bar>`를 사용