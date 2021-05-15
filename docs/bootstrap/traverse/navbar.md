---
layout: default
title: Navbar
parent: Traverse
grand_parent: Bootstrap
nav_order: 3
---

# Traverse Navbar
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### [Navigation](https://gekdev.github.io/docs/css/bootstrap/navigation.html)

* class="nav" 클래스 선택자를 사용한다.

* 탭형 네비게이션

    class="nav nav-tabs"   
    
    `<li class="active">` => 메뉴 활성화
    
    ```html
     <ul class="nav nav-tabs">
         <li><a href="#">메뉴1</a></li>
         <li class="active"><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li><a href="#">메뉴4</a></li>
     </ul>
    ```

* 알약형 네비게이션

    class="nav nav-pills"
    
    ```html
     <ul class="nav nav-pills">
         <li class="active"><a href="#">메뉴1</a></li>
         <li><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li><a href="#">메뉴4</a></li>
     </ul>
    ```

* 알약형 네비게이션은 수직으로 정렬 가능(탭형은 불가)

    class="nav nav-pills nav-stacked" 추가
    
    ```html
     <ul class="nav nav-pills nav-stacked">
         <li class="active"><a href="#">메뉴1</a></li>
         <li><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li><a href="#">메뉴4</a></li>
     </ul>
    ```
    
* 네비게이션 양쪽 정렬

     탭형 `<ul class="nav nav-tabs nav-justified">`
     
     알약형 `<ul class="nav nav-pills nav-justified">`

* class="disabled"을 이용한 링크 비활성화

    ```html
    <li class="disabled"><a href="#">메뉴3</a></li>
    ```

* 탭형 네비게이션 드롭다운

    ```html
    <ul class="nav nav-tabs">
         <li class="active"><a href="#">메뉴1</a></li>
         <li><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li class="dropdown">
               <a data-toggle="dropdown" href="#">여기 클릭 <span class="caret"></span></a>
               <ul class="dropdown-menu" role="menu">
                <li><a role="menuitem" href="#">메뉴 1</a></li>
                <li><a role="menuitem" href="#">메뉴 2</a></li>
                <li><a role="menuitem" href="#">메뉴 3</a></li>
                <li class="divider"></li>
                <li><a role="menuitem" href="#">분리된 메뉴 </a></li>
              </ul>
         </li>
     </ul>
    ```

* 알약형 형 네비게이션 드롭다운

    ```html
    <ul class="nav nav-pills">
         <li  class="active"><a href="#">메뉴1</a></li>
         <li><a href="#">메뉴2</a></li>
         <li><a href="#">메뉴3</a></li>
         <li class="dropdown">
               <a data-toggle="dropdown" href="#">여기 클릭 <span class="caret"></span></a>
               <ul class="dropdown-menu" role="menu">
                <li><a role="menuitem" href="#">메뉴 1</a></li>
                <li><a role="menuitem" href="#">메뉴 2</a></li>
                <li><a role="menuitem" href="#">메뉴 3</a></li>
                <li class="divider"></li>
                <li><a role="menuitem" href="#">분리된 메뉴 </a></li>
              </ul>
         </li>
     </ul>
     ```
         
### Navigation bar(RWD) 

* 네비게이션 바(반응형 네비)

   1. html5의 `<nav>`요소를 사용
   
   2. `<nav class="navbar navbar-default">`를 적용한다.
   
   3. `<div class="navbar-header"></div>`  => 주로 사이트의 로고/모바일에서 변하지 않는 영역
   
   4. `<div class="collapse navbar-collapse navbar-ex1-collapse"></div>`
   
        => 모바일에서는 센드위치메뉴로 바뀌면서 서브를 열리는 형태로 처리한다  
   
* 기본 구조

    ```html
        <nav class="navbar navbar-default" role="navigation">
          <div class="navbar-header">
             .....  
          </div>
          <div class="collapse navbar-collapse navbar-ex1-collapse">
             .....
          </div>
        </nav>   
    ```
  
* [메뉴 위치를 오른쪽으로 이동하려면](https://gekdev.github.io/docs/css/bootstrap/navbar-right.html)

    class="navbar-right"를 추가
    
* [드롭다운을 적용한 네비게이션 바](https://gekdev.github.io/docs/css/bootstrap/navbar-dropdown.html)
   
* [드롭다운을 적용한 오른쪽 정렬 네비게이션 바](https://gekdev.github.io/docs/css/bootstrap/navbar-dropdown-right.html)
   
* [텍트스/버튼/링크처리](https://gekdev.github.io/docs/css/bootstrap/navbar-btn-text-link.html)
   
     - 단순 버튼  class="btn btn-default navbar-btn"
     
     - 텍스트  p태그사용  `<p class="navbar-text">텍스트</p>`
     
     - 단순 링크     `<a href="#" class="navbar-link">링크</a>`
     
* [상단/하단 고정](https://gekdev.github.io/docs/css/bootstrap/navbar-topfix.html)

* [네비게이션 바의 배경색과 텍스트 색상 반전](https://gekdev.github.io/docs/css/bootstrap/navbar-inverse.html)

* [네비게이션 바의 상단고정](https://gekdev.github.io/docs/css/bootstrap/navbar-inverse.html)

* [네비게이션 바의 상단고정 폼형식](https://gekdev.github.io/docs/css/bootstrap/navbar-inverse.html)
