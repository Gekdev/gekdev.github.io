---
layout: default
title: Request
parent: AJAX
grand_parent: JavaScript
nav_order: 1
---

# AJAX Request
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Send a Request To a Server

### Request Method

서버에 요청을 보내기 위해 사용되는 `XMLHttpRequest` 객체의 메소드들

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
xhttp.open("GET", "ajax_info.txt", true); <br>
xhttp.send();                        
</div>

* open(method, url, async) : 요청의 타입을 명시

    &#9656; method: the type of request: GET or POST

    &#9656; url: the server (file) location

    &#9656; async: true (asynchronous) or false (synchronous)

* send() : 서버에 요청 (used for GET)

* send(string) : 서버에 요청 (used for POST)

### GET or POST


