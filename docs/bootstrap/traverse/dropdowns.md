---
layout: default
title: Dropdowns
parent: Traverse
grand_parent: Bootstrap
nav_order: 2
---

# Traverse Dropdowns
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### [Dropdown](https://gekdev.github.io/docs/css/bootstrap/dropdown.html)

* 단독으로 사용할 수 없고, 부트스트랩에 포함된 자바스크립트와 jQuery가 같이 있어야 동작

* ul class="dropdown-menu"
 
    ul/li로 구성된 리스트 태그에 적용
 
* 클릭 메뉴에 `<a data-toggle="dropdown">` 이 있어야 작동
 
    `<button>,<input type="button">`도 가능
    
* 상단 부분에 구분선 처리
 
    `<li role="presentation" class="divider"></li>`
    
* tabindex="-1"
    
    서브메뉴 부분에 tab키 적용을 받지 않게 하기위해 처리, 받으려면 생략


* class="pull-right"
  
   pull-right를 이용한 우측 정렬
  
   `<ul class="dropdown-menu pull-right" role="menu"> ... </ul>`

* class="dropdown-header"

    드롭다운에 별도의 헤더 추가 가능
   
   `<li role="presentation" class="dropdown-header">헤더 </li>`

* class="disabled"

    li 에 disabled 속성 추가로 비활성화 가능

   `<li role="presentation" class="disabled">`

