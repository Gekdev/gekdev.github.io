---
layout: default
title: Media Objects
parent: Information
grand_parent: Bootstrap
nav_order: 7
---

# Info Media Objects
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

     
### [Media](https://gekdev.github.io/docs/css/bootstrap/media.html)

* `<div class="media">..</div>` 로 감싸줌

* `<a class="pull-left" href="#">`를 display:block으로 만들어줌

* `<div class="media-body">` 이 부분이 바디(본문) 부분, 내부에 `<div class="media">`추가하면 댓글 표현 가능

    ```html
    <div class="media">
      <a class="pull-left" href="#">
           <img class="media-object" src="pic.jpg" alt="...">
      </a>
      <div class="media-body">
            <h4 class="media-heading">Media heading</h4>
            여기는 기본내용이 들어가는 곳 입니다. Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
           Pellentesque non orci interdum, pharetra dui nec, eleifend ligula. Integer rutrum nunc a mi luctus vehicula. 
      </div>
    </div>
    ```

    ```html
      <div class="media">
          <a class="pull-left" href="#">
             <img class="media-object" src="pic.jpg" alt="...">
          </a>
          <div class="media-body">
               <h4 class="media-heading">Media heading</h4>
               여기는 기본내용이 들어가는 곳 입니다. Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
                Pellentesque non orci interdum, pharetra dui nec, eleifend ligula. Integer rutrum nunc a mi luctus vehicula. 
               <div class="media">
                    <a class="pull-left" href="#">
                          <img class="media-object" src="pic.jpg" alt="...">
                    </a>
                    <div class="media-body">
                        <h4 class="media-heading">Media heading</h4>
                         여기는 기본내용이 들어가는 곳 입니다. Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
                    </div>
              </div>
          </div>
      </div>
    ```

* `<h4 class="media-heading">Media heading</h4>` 부분은 생략할 수 있음

* div를 사용하는 방법과 ul/li를 사용하는 두가지 방법이 있음

* 목록 사진을 오른쪽으로 이동

    `<a class="pull-right">`

    ```HTML
    <div class="media">
       <a class="pull-right" href="#">
           <img alt="Generic placeholder image" src="pic.jpg">
       </a>
       <div class="media-body">
            <h4 class="media-heading">Media heading</h4>
            Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin commodo. 
       </div>
    </div>   
    ```      