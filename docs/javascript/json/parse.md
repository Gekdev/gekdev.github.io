---
layout: default
title: Parse
parent: JSON
grand_parent: JavaScript
nav_order: 3
---

# JSON.parse()
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSON.parse()

### Parsing JSON

JSON의 일반적인 용도는 웹 서버와 데이터를주고받는 것

**웹 서버에서 데이터를 수신 할 때 데이터는 항상 문자열**임

`JSON.parse()`로 데이터를 구문 분석하면, **데이터가 JavaScript 객체가됨**

### Example

1. 웹 서버로부터 아래 택스트를 받음

    ! 텍스트가 JSON 형식으로 작성되어 있는지 확인 해야함 (그렇지 않으면 구문 오류가 발생)

    ```txt
    '{ "name":"John", "age":30, "city":"New York"}'
    ```

2. JavaScript 함수 JSON.parse()를 사용하여 텍스트를 JavaScript 객체로 변환

    ```js
    var obj = JSON.parse('{ "name":"John", "age":30, "city":"New York"}');
    ```

3. 페이지에서 JavaScript 객체를 사용

    ```html
    <p id="demo"></p>

    <script>
    ...
    document.getElementById("demo").innerHTML = obj.name + ", " + obj.age;
    </script>
    ```

### JSON From the Server

AJAX 요청을 사용하여 서버에서 JSON을 요청할 수 있음

서버의 응답이 JSON 형식으로 작성되는한 문자열을 JavaScript 객체로 구문분석 할 수 있음

[json_demo.txt](https://www.w3schools.com/js/json_demo.txt)

예제
{: .label .label-purple .mt-3}
```json
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    var myObj = JSON.parse(this.responseText);
    document.getElementById("demo").innerHTML = myObj.name;
  }
};
xmlhttp.open("GET", "json_demo.txt", true);
xmlhttp.send();
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjson_ajax){: .btn  .btn-outline .mt-2}
</span>

### Array as JSON

배열에서 파생 된 JSON을 `JSON.parse()`로 사용 하는 경우, 이 메소드는 **JavaScript 객체 대신 JavaScript 배열을 반환**

[json_demo_array.txt](https://www.w3schools.com/js/json_demo_array.txt)

예제
{: .label .label-purple .mt-3}
```json
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    var myArr = JSON.parse(this.responseText);
    document.getElementById("demo").innerHTML = myArr[0];
  }
};
xmlhttp.open("GET", "json_demo_array.txt", true);
xmlhttp.send();
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjson_ajax_array){: .btn  .btn-outline .mt-2}
</span>


### Exceptions - Parsing Dates

날짜 객체는 JSON에서 허용되지 않음

날짜를 포함해야하는 경우 날짜를 문자열로 작성해야함 (나중에 날짜 객체로 다시 변환할 수 있음)

아니면 `JSON.parse()`의 두 번째 매개 변수인 **reviver를 사용**해 **요소 값을 리턴하기 전에 각 Property를 검사**함

예제
{: .label .label-purple .mt-3}
```json
var text = '{ "name":"John", "birth":"1986-12-14", "city":"New York"}';
var obj = JSON.parse(text);
obj.birth = new Date(obj.birth);

document.getElementById("demo").innerHTML = obj.name + ", " + obj.birth;
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjson_parse_date){: .btn  .btn-outline .mt-2}
</span>

### Exceptions - Parsing Dates


또는 reviver 라는 함수 의 를 사용할 수 있습니다 .

염색제의 파라미터 값을 리턴하기 전에, 기능 검사 각 속성이다.

예
reviver 함수를 사용하여 문자열을 날짜로 변환하십시오 .

var text = '{ "name":"John", "birth":"1986-12-14", "city":"New York"}';
var obj = JSON.parse(text, function (key, value) {
  if (key == "birth") {
    return new Date(value);
  } else {
    return value;
  }
});

document.getElementById("demo").innerHTML = obj.name + ", " + obj.birth;
파싱 ​​함수
JSON에서는 함수가 허용되지 않습니다.

함수를 포함해야 할 경우 문자열로 작성하십시오.

나중에 함수로 다시 변환 할 수 있습니다.

예
문자열을 함수로 변환하십시오.

var text = '{ "name":"John", "age":"function () {return 30;}", "city":"New York"}';
var obj = JSON.parse(text);
obj.age = eval("(" + obj.age + ")");

document.getElementById("demo").innerHTML = obj.name + ", " + obj.age();
JSON에서 함수를 사용하지 않아야합니다. 함수의 범위가 없어지고 eval()함수로 다시 변환하는 데 사용해야 합니다.

브라우저 지원
이 JSON.parse()기능은 모든 주요 브라우저와 최신 ECMAScript (JavaScript) 표준에 포함되어 있습니다.

아래 표의 숫자는 JSON.parse()기능 을 완전히 지원하는 첫 번째 브라우저 버전을 지정합니다 .

Yes	8.0	3.5	4.0	10.0
이전 브라우저의 경우 JavaScript 라이브러리는 https://github.com/douglascrockford/JSON-js 에서 사용할 수 있습니다 .