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
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/alt_01.html" height="300" width="700" style="border:none;" title=" example"></iframe>
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
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/alt_02.html" height="300" width="700" style="border:none;" title=" example"></iframe>
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

### [Alert](https://gekdev.github.io/docs/css/bootstrap/progressbar.html)
 

* 없애기 버튼(X)과 .alert-dismissable 을 이용한 경보 없애기

    ```html
    <div class="alert alert-danger alert-dismissable">
         <button type="button" class="close" data-dismiss="alert" aria-hidden="true">×</button>
         <strong>경고!</strong> 입력하신 이메일이 존재하지 않습니다.
    </div>
    ```

* 경보내에 링크 처리는 .alert-link 선택자를 이용

    ```html
    <div class="alert alert-success alert-dismissable">
        <button type="button" class="close" data-dismiss="alert" aria-hidden="true">×</button>
        <strong>축하합니다.!</strong> 회원이 성공적으로 이뤄졌습니다.   <a href="#" class="alert-link">홈으로 돌아가기 </a>
    </div>
    ```