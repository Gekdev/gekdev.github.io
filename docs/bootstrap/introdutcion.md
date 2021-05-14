---
layout: default
title: Information
parent: Bootstrap
nav_order: 1
---

# Bootstrap Information
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Bootstrap 3

반응형 모바일 우선 웹 사이트를 개발하기위한 가장 인기있는 HTML, CSS 및 JavaScript 프레임워크

### What is Bootstrap?

**Bootstrap은 빠르고 쉬운 웹 개발을위한 무료 프런트 엔드 프레임 워크**

&#9656; 부트 스트랩에는 타이포그래피, 양식, 버튼, 테이블, 탐색, 모달, 이미지 캐 러셀 및 기타 여러 가지를위한 HTML 및 CSS 기반 디자인 템플릿과 선택적 JavaScript 플러그인이 포함

&#9656; 부트 스트랩은 또한 반응형 디자인을 쉽게 만들 수있는 기능을 제공

### Why Use Bootstrap?

&#9656; 사용하기 쉬움 : HTML과 CSS에 대한 기본적인 지식 만 있으면 누구나 부트 스트랩을 사용할 수 있음

&#9656; 반응 형 기능 : Bootstrap의 반응 형 CSS는 휴대폰, 태블릿 및 데스크톱에 맞게 조정

&#9656; 모바일 우선 접근 방식 : Bootstrap 3에서 모바일 우선 스타일은 핵심 프레임 워크의 일부

&#9656; 브라우저 호환성 : Bootstrap은 모든 최신 브라우저 (Chrome, Firefox, Internet Explorer, Edge, Safari 및 Opera)와 
호환

### Where to Get Bootstrap?

두가지 방법이 있음

1. [getbootstrap.com](https://getbootstrap.com/)에서 부트스트랩 소스 파일 다운로드

2. 부트 스트랩 CDN(Content Delivery Network)으로 파일에 직접 코드 포함

    <div class="code-example" markdown="1">
    이미 다른 사이트를 방문 할 때 MaxCDN에서 Bootstrap을 다운로드해서 로드 속도가 빠름, 또한 대부분의 CDN은 사용자가 파일을 요청하면 가장 가까운 서버에서 제공되므로 로드시간이 빠르다
    </div>
    ```js
    <!-- Latest compiled and minified CSS -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">

    <!-- jQuery library -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <!-- Latest compiled JavaScript -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
    ```
    
### jQuery and Bootstrap

&#9656; Bootstrap은 **jQuery 플러그인 (모달, 툴팁 등)을 사용하기 때문에 jQuery를 포함해야 함!**

&#8594; 하지만 Bootstrap의 CSS부분만 사용하는 경우에는 jQuery가 필요하지 않음

### Features of Bootstrap

* Bootstrap 3 is mobile-first

    Bootstrap 3은 모바일 장치에 반응하도록 설계되었음 (모바일 우선은 핵심 프레임 워크의 일부)

    &#8594; 적절한 렌더링과 터치 확대 / 축소를 보장하려면 요소 `<meta>`내부에 다음 태그를 추가해야함

    ```js
    <meta name="viewport" content="width=device-width, initial-scale=1">
    ```

* [Containers]()

    **사이트 콘텐츠를 래핑하기위한 포함 요소도 필요함**

    &#9656; container, container-fluid 두가지 클래스를 사용함

    ![](https://gekdev.github.io/assets/images/bootstrap_intro.png)

---

## Bootstrap 4

새로운 구성 요소, 더 빨라진 스타일 시트 및 더 빠른 응답 성, 모든 주요 브라우저 및 플랫폼의 안정적인 최신 릴리스를 지원을 제공하지만 Internet Explorer 9 이하는 지원하지 않음

