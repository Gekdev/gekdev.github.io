---
layout: default
title: AJAX
parent: JavaScript
nav_order: 30
has_children: true
---

# JavaScript AJAX
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## AJAX Introduction

### What is AJAX?

**JavaScript와 XML을 이용한 비동기적 정보 교환 기법**

Asynchronous JavaScript And XML 의 축약어

프로그래밍 언어가 아니고 **웹 페이지에서 웹 서버로 접근하기 위한 테크닉**

AJAX는 브라우저 내장 `XHLHTTPRequst` 객체 (웹 서버에서 데이터 요청)와 JavaScript 및 HTML DOM (데이터 표시 또는 사용)의 조합을 사용함

AJAX를 사용하면 **비하인드 웹 서버와 데이터를 교환해 웹 페이지를 비동기 식으로 업데이트** 할 수 있음, 한마디로 새로고침 없이 데이터를 서버에서 가져온다는 뜻

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
AJAX는 사실 잘못된 이름. AJAX 어플리케이션은 XML로 데이터를 전송하기도 하지만, 거의 동일하게 비슷한 방법으로 일반 텍스트 또는 JSON 텍스트로 전송하는게 일반적임 
</div>

### Why use AJAX?

1. 페이지가로드 된 후 웹 서버에서 데이터 읽기
2. 페이지를 다시로드하지 않고 웹 페이지 업데이트
3. 백그라운드에서 웹 서버로 데이터 보내기

### How AJAX Works

![](https://www.w3schools.com/js/pic_ajax.gif)

1. 웹 페이지에서 이벤트가 발생 (페이지가로드되고 버튼이 클릭 됨)
2. XMLHttpRequest 객체는 JavaScript에 의해 생성됨
3. XMLHttpRequest 객체는 웹 서버에 요청을 보냄
4. 서버가 요청을 처리
5. 서버가 웹 페이지로 응답
6. JavaScript로 응답을 읽음
7. JavaScript로 적절한 조치 (예 : 페이지 업데이트)가 수행

### AJAX Example

<div class="code-example" markdown="1">
<div id="demo">
<h2>The XMLHttpRequest Object</h2>
<button type="button" onclick="loadDoc()">Change Content</button>
</div> 

<script>
function ajax() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
     document.getElementById("demo").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}
</script>
</div>
```html
<div id="demo">
<h2>The XMLHttpRequest Object</h2>
<button type="button" onclick="ajax()">Change Content</button>
</div>

<script>
function ajax() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
     document.getElementById("demo").innerHTML = this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}
</script>

```

