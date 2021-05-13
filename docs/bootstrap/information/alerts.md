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

### [Alert](https://gekdev.github.io/docs/css/bootstrap/progressbar.html)
 
* 폼 양식에서 입력에 문제가 생겼거나 웹 페이지에서 주의할 내용을 강하게 알려줄 때 사용.

    ```HTML
    <div class="alert alert-success"></div>
    <div class="alert alert-info"></div>
    <div class="alert alert-warning"></div>
    <div class="alert alert-danger"></div>
    ```

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