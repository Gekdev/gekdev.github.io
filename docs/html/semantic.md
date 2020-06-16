---
layout: default
title: Semantic
parent: HTML
nav_order: 6
---

# Semantic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## HTML Semantic

### What is Semantic?

**문서의 구조와 의미를 표현하는 태그**

웹 접근성을 위해 꼭 필요함, 검색 엔진이 시멘틱 태그 기반으로 움직임

### HTML Layout Elements

* header : 페이지나 섹션의 머리말을 표현, section이나 article 태그 내에도 사용됨
* nav : 하이퍼링크들을 모아논 특별한 섹션, 목차
* section : 문서의 장 혹은 절을 구성하는 역할, h1~6로 섹션의 주제를 기재하는 것이 바람직 
* article : 본문과 연결되어 있는 독립적인 콘텐츠, section의 보조적인 기사
* aside : 흐름에 벗어나 짤막하게 곁들이는 관련 기사.. 
* footer : 꼬리말 영역을 표시하는 태그 
* figure : 본문에 삽입된 그림을 블록화 하는 시맨틱 태그
* details : 상세정보 담기 summary가 제목태그

### Features of Semantic Elements

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
IE9에서는 시멘틱 의미를 해석못해서, head태그 안에 HTML5Shiv라는 구문을 추가 해줘야함 
</div>
```html
<!--[if lt IE 9]>
    <script src="/js/html5shiv.js"></script>
<![endif]-->
```

### New Elements

스스로 html 테그를 만들어서 사용할 수 있음
