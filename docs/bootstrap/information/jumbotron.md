---
layout: default
title: Jumbotron & Page Header
parent: Information
grand_parent: Bootstrap
nav_order: 1
---

# Info Jumbotron
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Jumbotron

### What is Jumbotron?

**특별한 내용이나 정보에 특별한주의를 기울이는 큰 상자**

&#9656; 웹사이트에서 중요한 내용 또는 공지사항 등을 부각할 때 사용

&#9656; 모서리가 둥근 회색 상자로 표시되고 내부 텍스트의 글꼴 크기를 확대함

&#9656; 점보트론 내부의 글꼴크기 21px, 내부는 30px의 패딩값 적용, 배경색상 #eee

★ jumbotron 안에는 다른 Bootstrap 요소, 클래스를 포함하여 거의 모든 유효한 HTML에 사용할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="container"
</div>

### Jumbotron Inside Container

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/jb_in.html" height="350" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <div class="jumbotron">
    <h1>Bootstrap Tutorial</h1>      
    <p>Bootstrap is the most popular HTML, CSS, and JS framework for developing responsive, mobile-first projects on the web.</p>
  </div>
  <p>This is some text.</p>      
  <p>This is another text.</p>      
</div>
```

### Jumbotron Outside Container

외부에 두면 넓이가 100%가 된다

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/jb_out.html" height="350" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="jumbotron">
  <h1>Bootstrap Tutorial</h1>      
  <p>Bootstrap is the most popular HTML, CSS, and JS framework for developing responsive, mobile-first projects on the web.</p>
</div>

<div class="container">
  <p>This is some text.</p>      
  <p>This is another text.</p>      
</div>
```

---

## Page Header

**제목 아래 수평 라인을 추가**

&#9656; 페이지 헤더는 섹션 구분선과 같음

### Example Page Header

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/jb_ph.html" height="350" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <div class="page-header">
    <h1>Example Page Header</h1>      
  </div>
  <p>This is some text.</p>      
  <p>This is another text.</p>      
</div>
```
