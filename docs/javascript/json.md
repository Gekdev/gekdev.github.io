---
layout: default
title: JSON
parent: JavaScript
nav_order: 15
has_children: true
---

# JavaScript JSON
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSON Introduction

### What is JSON?

**JavaScript 객체 표기법으로 작성된 텍스트**, JavaScript Object Notation의 약자

데이터를 저장하고 교환하기위한 구문, 형식

"자체 서술 적"이며 이해하기 쉽다

언어와 무관함

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
JSON은 JavaScript 구문을 사용하지만 JSON 형식은 텍스트 전용

모든 프로그래밍 언어에서 텍스트를 읽고 데이터 형식으로 사용할 수 있음
</div>

### Why use JSON?

JSON 형식은 텍스트 전용이므로 서버와 쉽게 주고받을 수 있음

모든 프로그래밍 언어에서 데이터 형식으로 사용할 수 있음

JavaScript에는 JSON 형식으로 작성된 문자열을 기본 JavaScript 객체로 변환하는 기능(`JSON.parse()`)이 내장되어 있음

따라서 서버에서 데이터를 JSON 형식으로 받으면 다른 JavaScript 객체처럼 사용할 수 있음

### Exchanging Data

브라우저와 서버간에 데이터를 교환 할 때 **데이터는 텍스트만** 될 수 있음

JSON은 텍스트이며 모든 JavaScript 객체를 JSON으로 변환하고 그 JSON을 서버로 보낼 수 있음

또한 그 반대인 서버에서 받은 JSON을 JavaScript 객체로 변환 할 수도 있음

이런 식으로 복잡한 구문 분석 및 변환없이 데이터를 JavaScript 객체로 작업 할 수 있음

### Sending Data

JavaScript 객체에 데이터가 저장된 경우 객체를 JSON으로 변환하여 서버로 보낼 수 있음

예제
{: .label .label-purple .mt-3}
```js
var myObj = {name: "John", age: 31, city: "New York"};
var myJSON = JSON.stringify(myObj);
window.location = "demo_json.php?x=" + myJSON;
```

### Receiving Data

JSON 형식의 데이터를 수신하면 이를 JavaScript 객체로 변환 할 수 있음

예제
{: .label .label-purple .mt-3}
```js
var myJSON = '{"name":"John", "age":31, "city":"New York"}';
var myObj = JSON.parse(myJSON);
document.getElementById("demo").innerHTML = myObj.name;
``` 

### Storing Data

데이터를 저장할 때 데이터는 특정 형식이어야하며, 저장 위치에 관계없이 텍스트 는 항상 유효한 형식 중 하나여야 함

JSON을 사용하면 JavaScript 객체를 텍스트로 저장할 수 있습니다.

예제
{: .label .label-purple .mt-3}
```js
// Storing data:
myObj = {name: "John", age: 31, city: "New York"};
myJSON = JSON.stringify(myObj);
localStorage.setItem("testJSON", myJSON);

// Retrieving data:
text = localStorage.getItem("testJSON");
obj = JSON.parse(text);
document.getElementById("demo").innerHTML = obj.name;
``` 

---

## JSON vs XML

### XML

JSON과 XML 모두 웹 서버에서 데이터를 수신하는 데 사용할 수 있습니다.

JSON 예제
{: .label .label-purple .mt-3}
```json
{"employees":[
  { "firstName":"John", "lastName":"Doe" },
  { "firstName":"Anna", "lastName":"Smith" },
  { "firstName":"Peter", "lastName":"Jones" }
]}
```

XML 예제
{: .label .label-purple .mt-3}
```xml
<employees>
  <employee>
    <firstName>John</firstName> <lastName>Doe</lastName>
  </employee>
  <employee>
    <firstName>Anna</firstName> <lastName>Smith</lastName>
  </employee>
  <employee>
    <firstName>Peter</firstName> <lastName>Jones</lastName>
  </employee>
</employees>
```

### Common Features of JSON and XML

JSON과 XML 모두 "자체 설명"(사람이 읽을 수 있음)
JSON과 XML은 모두 계층 적입니다 (값 내의 값)
많은 프로그래밍 언어에서 JSON과 XML을 구문 분석하고 사용할 수 있습니다.
XMLHttpRequest로 JSON과 XML을 모두 가져올 수 있습니다.


### Difference between JSON XML

JSON은 종료 태그를 사용하지 않습니다
JSON이 짧다
JSON이 더 빨리 읽고 쓰기
JSON은 배열을 사용할 수 있습니다
XML은 XML 파서로 구문 분석해야합니다. JSON은 표준 JavaScript 함수로 구문 분석 할 수 있습니

### Why JSON is Better Than XML

XML은 JSON보다 구문 분석하기가 훨씬 어려움

JSON은 **즉시 사용 가능한 JavaScript 객체로 구문 분석**됨

AJAX 애플리케이션의 경우 JSON이 XML보다 빠르고 쉽다

* XML 사용

    1. XML 문서를 가져옴
    2. XML DOM을 사용하여 문서를 반복
    3. 값을 추출하고 변수에 저장

* JSON 사용

    1. JSON 문자열을 가져옴
    2. JSON 문자열을 구문분석함
