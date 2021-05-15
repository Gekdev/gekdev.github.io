---
layout: default
title: Alerts
parent: Information
grand_parent: Bootstrap
nav_order: 6
---

# Info Alerts
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Alert Class

### Alert Basic

**폼 양식에서 입력에 문제가 생겼거나 웹 페이지에서 주의할 내용을 강하게 알려줄 때 사용**

&#9656; alert 클래스 먼저 사용 후 사용해야함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* class="alert alert-success" : 성공! 이 경고 상자는 성공 또는 긍정적 인 작업

* class="alert alert-info" : 정보! 이 경고 상자는 중립적 인 정보 변경 또는 작업

* class="alert alert-warning" : 경고! 이 경고 상자는주의가 필요한 경고

* class="alert alert-danger" : 위험! 이 경고 상자는 위험하거나 잠재적으로 부정적인 작업
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/alt_01.html" height="400" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Alerts</h2>
  <div class="alert alert-success">
    <strong>Success!</strong> This alert box could indicate a successful or positive action.
  </div>
  <div class="alert alert-info">
    <strong>Info!</strong> This alert box could indicate a neutral informative change or action.
  </div>
  <div class="alert alert-warning">
    <strong>Warning!</strong> This alert box could indicate a warning that might need attention.
  </div>
  <div class="alert alert-danger">
    <strong>Danger!</strong> This alert box could indicate a dangerous or potentially negative action.
  </div>
</div>
```

### Alert Links

경고상자 안의 링크에 클래스를 추가하여 **일치하는 색상 링크를 만듦**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//부모 객체에 alert, alert-.... 선언 후

class="alert alert-success"

//자식 a 객체에 alert-link 클래스 선언 가능

a href="#" class="alert-link">
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/alt_02.html" height="400" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Alert Links</h2>
  <p>Add the alert-link class to any links inside the alert box to create "matching colored links".</p>
  <div class="alert alert-success">
    <strong>Success!</strong> You should <a href="#" class="alert-link">read this message</a>.
  </div>
  <div class="alert alert-info">
    <strong>Info!</strong> You should <a href="#" class="alert-link">read this message</a>.
  </div>
  <div class="alert alert-warning">
    <strong>Warning!</strong> You should <a href="#" class="alert-link">read this message</a>.
  </div>
  <div class="alert alert-danger">
    <strong>Danger!</strong> You should <a href="#" class="alert-link">read this message</a>.
  </div>
</div>
```

### Closing Alerts

**알람에 제거 버튼(X) 생성**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//부모 객체에 alert alert-... 선언 후

class = "alert-dismissible"

//자식 a 객체에 아래 코드 선언

a href="#" class="close" data-dismiss="alert" aria-label="close"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/alt_close.html" height="400" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Alerts</h2>
  <p>The a element with class="close" and data-dismiss="alert" is used to close the alert box.</p>
  <p>The alert-dismissible class adds some extra padding to the close button.</p>
  <div class="alert alert-success alert-dismissible">
    <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
    <strong>Success!</strong> This alert box could indicate a successful or positive action.
  </div>
  <div class="alert alert-info alert-dismissible">
    <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
    <strong>Info!</strong> This alert box could indicate a neutral informative change or action.
  </div>
  <div class="alert alert-warning alert-dismissible">
    <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
    <strong>Warning!</strong> This alert box could indicate a warning that might need attention.
  </div>
  <div class="alert alert-danger alert-dismissible">
    <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
    <strong>Danger!</strong> This alert box could indicate a dangerous or potentially negative action.
  </div>
</div>
```

#### aria- *

**스크린 리더를 사용하는 사람들을 위한 웹 접근성 속성**

### Animated Alerts

**경고 메시지를 닫을 때 클래스는 페이딩 효과를 추가**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
class="alert alert-danger fade in
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/alt_animation.html" height="400" width="700" style="border:none;" title=" example"></iframe>
</div>
```html
<div class="container">
  <h2>Animated Alerts</h2>
  <p>The .fade and .in classes adds a fading effect when closing the alert message.</p>
  <div class="alert alert-success alert-dismissible fade in">
    <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
    <strong>Success!</strong> This alert box could indicate a successful or positive action.
  </div>
  <div class="alert alert-info alert-dismissible fade in">
    <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
    <strong>Info!</strong> This alert box could indicate a neutral informative change or action.
  </div>
  <div class="alert alert-warning alert-dismissible fade in">
    <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
    <strong>Warning!</strong> This alert box could indicate a warning that might need attention.
  </div>
  <div class="alert alert-danger alert-dismissible fade in">
    <a href="#" class="close" data-dismiss="alert" aria-label="close">&times;</a>
    <strong>Danger!</strong> This alert box could indicate a dangerous or potentially negative action.
  </div>
</div>
```