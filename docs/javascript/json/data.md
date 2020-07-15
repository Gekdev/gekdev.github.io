---
layout: default
title: Data
parent: JSON
grand_parent: JavaScript
nav_order: 2
---

# JSON Data
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Data Types

### Valid Data Types

JSON 데이터 타입이 될 수 있는 값들

* a string
* a number
* an object (JSON object)
* an array
* a boolean
* null

warning
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
JSON 데이터 유형이 되면 안되는 것들

* a function
* a date
* undefined
</div>

### JSON Strings

JSON의 문자열은 무조건 큰 따옴표로 묶여야 함

예제
{: .label .label-purple .mt-3}
```json
{ "name": "John" }
```

### JSON Numbers

JSON의 숫자는 정수 또는 부동 소수점

예제
{: .label .label-purple .mt-3}
```json
{ "age": 30 }
```

### JSON Objects

JSON의 값은 객체 일 수 있음

JSON의 값인 객체는 JSON 객체와 동일한 규칙을 따라야함

예제
{: .label .label-purple .mt-3}
```json
{
"employee": { "name":"John", "age":30, "city":"New York" }
}
```

### JSON Arrays

JSON의 값은 배열이 될 수 있음

예제
{: .label .label-purple .mt-3}
```json
{
"employees": [ "John", "Anna", "Peter" ]
}
```

### JSON Booleans

JSON의 값은 true / false 일 수 있음

예제
{: .label .label-purple .mt-3}
```json
{ "sale": true }
```

### JSON null

JSON의 값은 null 일 수 있음

예제
{: .label .label-purple .mt-3}
```json
{ "middlename": null }
```

---

## JSON Objects

### Object Syntax

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
{ "key":"value", "key":"value", ...}
</div>

&#9656; **중괄호 {}**로 묶임

&#9656; **"키" : "값"의 쌍**으로 쓰임, 쌍은 **쉼표**로 구분

&#8594; **키는 문자열, 값은 유효한 JSON 데이터 유형 (string, number, object, array, boolean 또는 null) 이어야 함**

### Accessing Object Values

1. 점 (.) 표기법 (dot notation)

    예제
    {: .label .label-purple .mt-3}
    ```json
    myObj = { "name":"John", "age":30, "car":null };
    x = myObj.name;
    ```

2. 대괄호 ([]) 표기법 (bracket notation)

    예제
    {: .label .label-purple .mt-3}
    ```json
    myObj = { "name":"John", "age":30, "car":null };
    x = myObj["name"];
    ```

### Looping an Object

**for-in 루프**를 사용하여 객체 속성 반복

**x는 키값이 됨!**

속성값에 접근하려면 대괄호 표기법을 사용해 접근해야 함 (점 표기법은 안됨)

예제: 키 추출
{: .label .label-purple .mt-3}
```json
myObj = { "name":"John", "age":30, "car":null };
for (x in myObj) {
  document.getElementById("demo").innerHTML += x;
}
```

예제: 값 추출
{: .label .label-purple .mt-3}
```json
myObj = { "name":"John", "age":30, "car":null };
for (x in myObj) {
  document.getElementById("demo").innerHTML += myObj[x];
}
```

### Nested JSON Objects

객체의 값은 또 객체일 수 있음

**점 표기법 또는 대괄호 표기법을 사용해 중첩 JSON 객체에 접근**할 수 있음

예제: 중첩된 객체
{: .label .label-purple .mt-3}
```json
myObj = {
  "name":"John",
  "age":30,
  "cars": {
    "car1":"Ford",
    "car2":"BMW",
    "car3":"Fiat"
  }
 }
```

예제: 중첩 JSON 객체에 접근하는 방법
{: .label .label-purple .mt-3}
```json
x = myObj.cars.car2;
// or:
x = myObj.cars["car2"];
```

### Modify Values

**점, 대괄호 표기법을 사용하여 JSON 객체의 값을 수정**

예제
{: .label .label-purple .mt-3}
```json
myObj.cars.car2 = "Mercedes";
```

예제
{: .label .label-purple .mt-3}
```json
myObj.cars["car2"] = "Mercedes";
```

### Delete Object Properties

**`delete` 키워드 사용해 JSON 객체의 값을 삭제**

예제
{: .label .label-purple .mt-3}
```json
delete myObj.cars.car2;
```

---

## JSON Arrays

### Arrays as JSON Objects

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
[ "value", "value", ...]
</div>

&#9656; JSON의 배열은 JavaScript의 배열과 거의 동일

&#9656; **JSON에서 배열 값은 유효한 JSON 데이터 유형 (string, number, object, array, boolean 또는 null) 이어야 함**

&#9656; JavaScript에서 배열 값은 위의 모든 값과 함수, 날짜 및 정의되지 않은 기타 유효한 JavaScript 표현식 일 수 있음

### Arrays in JSON Objects

배열은 객체의 속성 값일 수 있음

예제
{: .label .label-purple .mt-3}
```json
{
"name":"John",
"age":30,
"cars":[ "Ford", "BMW", "Fiat" ]
}
```

### Accessing Array Values

1. **인덱스 번호를 사용**하여 배열 값에 액세스

    예제: 인덱스
    {: .label .label-purple .mt-3}
    ```json
    x = myObj.cars[0];
    ```

2. **for-in 루프 또는 for 루프를 사용하여 배열 값에 액세스**

    예제: for-in 
    {: .label .label-purple .mt-3}
    ```json
    for (i in myObj.cars) {
      x += myObj.cars[i];
    }
    ```

    예제: for
    {: .label .label-purple .mt-3}
    ```json
    for (i = 0; i < myObj.cars.length; i++) {
      x += myObj.cars[i];
    }
    ```

### Nested Arrays in JSON Objects

**배열의 값은 다른 배열 또는 다른 JSON 객체 일 수도 있음**

예제: 객체 안 배열의 객체의 값이 배열
{: .label .label-purple .mt-3}
```json
myObj = {
  "name":"John",
  "age":30,
  "cars": [ 
    { "name":"Ford", "models":[ "Fiesta", "Focus", "Mustang" ] },
    { "name":"BMW", "models":[ "320", "X3", "X5" ] },
    { "name":"Fiat", "models":[ "500", "Panda" ] }
  ]
 }
```

**배열 내부의 배열에 액세스하려면 각 배열에 for-in 루프를 사용**

예제
{: .label .label-purple .mt-3}
```json
for (i in myObj.cars) {
  x += "<h1>" + myObj.cars[i].name + "</h1>";
  for (j in myObj.cars[i].models) {
    x += myObj.cars[i].models[j];
  }
}
```

### Modify Array Values

**인덱스 번호를 사용해 배열을 수정**

예제
{: .label .label-purple .mt-3}
```json
myObj.cars[1] = "Mercedes";
```

### Delete Array Items

`delete` 키워드를 사용하여 배열에서 항목을 삭제 

예제
{: .label .label-purple .mt-3}
```json
delete myObj.cars[1];
```

---

## JSON PHP

JSON의 일반적인 용도는 웹 서버에서 데이터를 읽고 웹 페이지에 데이터를 표시하는 것

클라이언트와 PHP 서버간에 JSON 데이터를 교환하는 방법에 대해 설명

### The PHP File

PHP에는 JSON을 처리하기위한 내장 함수 `json_encode()`를 사용하여 PHP의 객체를 JSON으로 변환 할 수 있음

예제
{: .label .label-purple .mt-3}
```php
<?php
$myObj->name = "John";
$myObj->age = 30;
$myObj->city = "New York";

$myJSON = json_encode($myObj);

echo $myJSON;
?>
```

#### The Client JavaScript

AJAX 호출을 사용하여 PHP 파일을 요청하는 클라이언트의 JavaScript

예제: JSON.parse ()를 사용하여 PHP파일을 JavaScript 객체로 변환
{: .label .label-purple .mt-3}
```js
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    var myObj = JSON.parse(this.responseText);
    document.getElementById("demo").innerHTML = myObj.name;
  }
};
xmlhttp.open("GET", "demo_file.php", true);
xmlhttp.send();
```

### PHP Array

PHP 함수 `json_encode()` : PHP의 배열을 JSON으로 변환

예제
{: .label .label-purple .mt-3}
```php
<?php
$myArr = array("John", "Mary", "Peter", "Sally");

$myJSON = json_encode($myArr);

echo $myJSON;
?>
```

#### The Client JavaScript

PHP 파일을 요청하기 위해 AJAX 호출을 사용하는 클라이언트의 JavaScript

예제
{: .label .label-purple .mt-3}
```js
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    var myObj = JSON.parse(this.responseText);
    document.getElementById("demo").innerHTML = myObj[2];
  }
};
xmlhttp.open("GET", "demo_file_array.php", true);
xmlhttp.send();
```

### PHP Database

PHP는 **서버측 프로그래밍 언어이며 데이터베이스에 액세스하는 데 사용**할 수 있음

서버에 데이터베이스가 있고 "고객"이라는 테이블의 첫 10 행을 요청하는 클라이언트에서 데이터베이스로 요청을 보내려고한다고 가정하십시오.

클라이언트에서 리턴하려는 행 수를 설명하는 JSON 오브젝트를 작성하십시오.

요청을 서버로 보내기 전에 JSON 객체를 문자열로 변환하여 PHP 페이지의 URL에 매개 변수로 보내십시오.

예제: JavaScript 객체를 JSON으로 변환
{: .label .label-purple .mt-3}
```js
obj = { "limit":10 };                       // 1. "제한"속성 및 값을 포함하는 개체를 정의
dbParam = JSON.stringify(obj);              // 2. 객체를 JSON 문자열로 변환
xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {   // 3. JSON 문자열을 매개 변수로 사용하여 PHP 파일에 요청
  if (this.readyState == 4 && this.status == 200) { // 4. 요청이 결과와 함께 반환 될 때까지 기다림
    document.getElementById("demo").innerHTML = this.responseText;  // 5. PHP 파일에서받은 결과를 표시
  }
};
xmlhttp.open("GET", "json_demo_db.php?x=" + dbParam, true);
xmlhttp.send();
```

PHP 파일
{: .label .label-purple .mt-3}
```php
<?php
header("Content-Type: application/json; charset=UTF-8");
$obj = json_decode($_GET["x"], false);          // 1. PHP 함수 json_decode ()를 사용하여 요청을 객체로 변환

$conn = new mysqli("myServer", "myUser", "myPassword", "Northwind");    // 2. 데이터베이스에 액세스하고 요청 된 데이터로 배열을 채움
$stmt = $conn->prepare("SELECT name FROM customers LIMIT ?");
$stmt->bind_param("s", $obj->limit);
$stmt->execute();
$result = $stmt->get_result();
$outp = $result->fetch_all(MYSQLI_ASSOC);

echo json_encode($outp);        // 3. 배열을 객체에 추가하고 json_encode () 함수를 사용하여 객체를 JSON으로 반환
?>
```

### Loop Through the Result

PHP 파일에서받은 결과를 JavaScript 객체일 경우 JavaScript 배열로 변환

예제 : JSON을 JavaScript 객체로 변환
{: .label .label-purple .mt-3}
```js
...
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    myObj = JSON.parse(this.responseText);
    for (x in myObj) {
      txt += myObj[x].name + "<br>";
    }
    document.getElementById("demo").innerHTML = txt;
  }
};
...
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjson_php_db_loop){: .btn  .btn-outline .mt-2}
</span>

### PHP Method = POST

**서버로 데이터를 전송할 때 HTTP POST메소드를 사용하는 것이 가장 좋음**

POST메소드를 사용하여 AJAX 요청을 보내려면 메소드와 올바른 헤더를 지정해야 함

서버로 전송 된 데이터는 send()메소드에 대한 인수 여야함

예제
{: .label .label-purple .mt-3}
```js
obj = { "limit":10 };
dbParam = JSON.stringify(obj);
xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    myObj = JSON.parse(this.responseText);
    for (x in myObj) {
      txt += myObj[x].name + "<br>";
    }
    document.getElementById("demo").innerHTML = txt;
  }
};
xmlhttp.open("POST", "json_demo_db_post.php", true);
xmlhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xmlhttp.send("x=" + dbParam);
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjson_php_db_post){: .btn  .btn-outline .mt-2}
</span>

PHP 파일의 유일한 차이점은 전송 된 데이터를 가져 오는 방법임

PHP 파일
{: .label .label-purple .mt-3}
```php
<?php
header("Content-Type: application/json; charset=UTF-8");
$obj = json_decode($_POST["x"], false);

$conn = new mysqli("myServer", "myUser", "myPassword", "Northwind");
$stmt = $conn->prepare("SELECT name FROM customers LIMIT ?");
$stmt->bind_param("s", $obj->limit);
$stmt->execute();
$result = $stmt->get_result();
$outp = $result->fetch_all(MYSQLI_ASSOC);

echo json_encode($outp);
?>
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/js_json_arrays.as){: .btn  .btn-outline .mt-2}
</span>

---

## JSON HTML

### HTML Table

JavaScript는 웹 페이지에서 HTML을 만드는 데 사용될 수 있음

JSON으로받은 데이터로 HTML 테이블 만들기

예제
{: .label .label-purple .mt-3}
```js
var obj, dbParam, xmlhttp, myObj, x, txt = "";
obj = { table: "customers", limit: 20 };
dbParam = JSON.stringify(obj);
xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    myObj = JSON.parse(this.responseText);
    txt += "<table border='1'>"
    for (x in myObj) {
      txt += "<tr><td>" + myObj[x].name + "</td></tr>";
    }
    txt += "</table>"
    document.getElementById("demo").innerHTML = txt;
  }
}
xmlhttp.open("POST", "json_demo_db_post.php", true);
xmlhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xmlhttp.send("x=" + dbParam);
```

### Dynamic HTML Table

드롭 다운 메뉴의 값을 기준으로 HTML 테이블을 만들기

예제
{: .label .label-purple .mt-3}
```html
<select id="myselect" onchange="change_myselect(this.value)">
  <option value="">Choose an option:</option>
  <option value="customers">Customers</option>
  <option value="products">Products</option>
  <option value="suppliers">Suppliers</option>
</select>

<script>
function change_myselect(sel) {
  var obj, dbParam, xmlhttp, myObj, x, txt = "";
  obj = { table: sel, limit: 20 };
  dbParam = JSON.stringify(obj);
  xmlhttp = new XMLHttpRequest();
  xmlhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      myObj = JSON.parse(this.responseText);
      txt += "<table border='1'>"
      for (x in myObj) {
        txt += "<tr><td>" + myObj[x].name + "</td></tr>";
      }
      txt += "</table>"
      document.getElementById("demo").innerHTML = txt;
    }
  };
  xmlhttp.open("POST", "json_demo_html_table.php", true);
  xmlhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
  xmlhttp.send("x=" + dbParam);
}
</script>
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjson_html_table_dynamic){: .btn  .btn-outline .mt-2}
</span>

### HTML Drop Down List

JSON으로받은 데이터로 HTML 드롭 다운 목록을 만들기

예제
{: .label .label-purple .mt-3}
```js
obj = { table: "customers", limit: 20 };
dbParam = JSON.stringify(obj);
xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    myObj = JSON.parse(this.responseText);
    txt += "<select>"
    for (x in myObj) {
      txt += "<option>" + myObj[x].name;
    }
    txt += "</select>"
    document.getElementById("demo").innerHTML = txt;
  }
}
xmlhttp.open("POST", "json_demo_html_table.php", true);
xmlhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xmlhttp.send("x=" + dbParam);
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/js_json_html.asp){: .btn  .btn-outline .mt-2}
</span>

