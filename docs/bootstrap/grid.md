---
layout: default
title: Grid
parent: Bootstrap
nav_order: 2
has_children: true
---

# Bootstrap Grid
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Bootstrap Grid Basic

### What is Grid System?

**그리드는 화면을 총 12열로 구성해서 레이아웃을 잡는 시스템**

&#9656; 여러개를 그룹화 해 더 많은 열로 만들 수 있음

&#9656; 그리드 클래스를 이용해 스크린 사이즈에 따라서 Responisve하게 열을 리사이징 할 수 있음

![](https://gekdev.github.io/assets/images/gridsystem.PNG)

### Grid Basic Structure

1. 먼저 행을 추가 하기 `row`

2. 다음 원하는 수의 열을 각 행에 최대 12개 더하기

기본 구조
{: .label .mt-2}
```js
<div class="row">
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
</div>
<div class="row">
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
</div>
<div class="row">
  ...
</div>
```

### Grid System Rules

**일부 부트 스트랩 그리드 시스템 규칙**

* 적절한 정렬 및 패딩을 위해 행은 .container(고정 너비) 또는 .container-fluid(전체 너비)내에 배치되어야함

* 행을 사용하여 가로 열 그룹 만들기

* 콘텐츠는 열 내에 배치되어야하며 열만 행의 직계 자식 일 수 있음

* 열은 패딩을 통해 gutters(열 내용 사이의 간격)를 만들고 해당 패딩은 .rows의 음수 여백을 통해 첫 번째 및 마지막 열의 행에서 오프셋됨

* 열 너비는 백분율로 표시되므로 항상 상위 요소에 비해 유동적이고 크기가 조정됨

### Nested Columns

**하나의 그리드 내부에 또 그리드를 만들수 있음**

&#9656; 내부에 만들어진 그리드는 또다시 12개의 그리드가 생성

<span class="fs-2">
[W3School](https://www.w3schools.com/bootstrap/tryit.asp?filename=trybs_grid_ex4&stacked=h){: .btn .btn-outline .mt-2}
</span>

### Grid Option

|  	                         | Extra small <768px	        | Small >=768px	                                | Medium >=992px	                               | Large >=1200px     |
|---------------------------:|---------------------------:|----------------------------------------------:|-----------------------------------------------:|-------------------:|
| 해상도에 따른 클래스 접두사  | .col-xs-	                  | .col-sm-	                                     | .col-md-	                                      | .col-lg-          |
| 맞는 기기             	    | Phones	                  | Tablets	                                      | Small Laptops                                 	| Laptops & Desktops |
| 그리드 행동                 | 항상 수평으로	             | Collapsed to start, breakpoint까지 수평으로	| Collapsed to start, breakpoint까지 수평으로	        | Collapsed to start, breakpoint까지 수평으로 |
| 컨테이너의 가로값            | None (auto)              |	750px                                        |	970px                                             | 1170px |
| # of columns		            | 12	| 12	| 12	| 12 |
| 열 넓이	| Auto	| ~62px	| ~81px	| ~97px |
| Gutter width	| 30px (15px on each side of a column)	| 30px (15px on each side of a column)	| 30px (15px on each side of a column)	| 30px (15px on each side of a column) |
| 중첩 가능 여부	 | Yes	| Yes	| Yes	| Yes |
| 오프셋 가능 여부	| Yes	| Yes	| Yes	| Yes |
| Column ordering	| Yes	| Yes	| Yes	| Yes |
