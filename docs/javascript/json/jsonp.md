---
layout: default
title: JSONP
parent: JSON
grand_parent: JavaScript
nav_order: 5
---

# JSONP
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSONP

### JSONP Intro

JSONP는 **도메인 간 문제에 대한 걱정없이 JSON 데이터를 전송하는 방법**, **JSON with Padding** 의 약자

XMLHttpRequest객체를 사용하지 않고 <script> 태그를 사용

도메인 간 정책으로 인해 다른 도메인에서 파일을 요청하면 문제가 발생할 수 있지만, 다른 도메인에서 외부 스크립트 를 요청하면 이 문제가 발생하지 않음

JSONP는 이걸 활용해 XMLHttpRequest객체 대신 스크립트 태그를 사용하여 파일을 요청

```html
<script src="demo_jsonp.php">
```

### The Server File

서버의 파일은 결과를 함수 호출로 래핑함


예제
{: .label .label-purple .mt-3}
```php
<?php
$myJSON = '{ "name":"John", "age":30, "city":"New York" }';

echo "myFunc(".$myJSON.");";
?>
```

결과는 JSON 데이터를 매개 변수로 사용하여 "myFunc"라는 함수에 대한 호출을 리턴합니다.

기능이 클라이언트에 존재하는지 확인하십시오.

### The JavaScript function

"myFunc"라는 함수는 클라이언트에 있으며 JSON 데이터를 처리 할 준비가 됨

예제
{: .label .label-purple .mt-3}
```js
function myFunc(myObj) {
  document.getElementById("demo").innerHTML = myObj.name;
}
```

### Creating a Dynamic Script Tag

위의 예제는 스크립트 태그를 넣은 위치에 따라 페이지가 로드 될 때 "myFunc"함수를 실행합니다. 이는 매우 만족스럽지 않습니다.

스크립트 태그는 필요한 경우에만 작성해야 함

예제 : 버튼을 클릭하면 `<script>` 태그를 작성하고 삽입
{: .label .label-purple .mt-3}
```js
function clickButton() {
  var s = document.createElement("script");
  s.src = "demo_jsonp.php";
  document.body.appendChild(s);
}
```

### Dynamic JSONP Result

위의 예는 여전히 매우 정적임

JSON을 PHP 파일로 전송하여 예제를 동적으로 만들고 PHP 파일이 정보를 기반으로 JSON 객체를 반환하도록합니다.

```php
<?php
header("Content-Type: application/json; charset=UTF-8");
$obj = json_decode($_GET["x"], false);

$conn = new mysqli("myServer", "myUser", "myPassword", "Northwind");
$result = $conn->query("SELECT name FROM ".$obj->$table." LIMIT ".$obj->$limit);
$outp = array();
$outp = $result->fetch_all(MYSQLI_ASSOC);

echo "myFunc(".json_encode($outp).")";
?>
```

PHP 파일 설명 :
PHP 함수 json_decode ()를 사용하여 요청을 객체로 변환하십시오 .
데이터베이스에 액세스하고 요청 된 데이터로 배열을 채 웁니다.
배열을 객체에 추가하십시오.
json_encode () 함수를 사용하여 배열을 JSON으로 변환하십시오 .
리턴 오브젝트 주위에 "myFunc ()"를 랩핑하십시오.

자바 스크립트 예제 "myFunc"함수는 PHP 파일에서 호출
{: .label .label-purple .mt-3}
```js
function clickButton() {
  var obj, s
  obj = { table: "products", limit: 10 };
  s = document.createElement("script");
  s.src = "jsonp_demo_db.php?x=" + JSON.stringify(obj);
  document.body.appendChild(s);
}
function myFunc(myObj) {
  var x, txt = "";
  for (x in myObj) {
    txt += myObj[x].name + "<br>";
  }
  document.getElementById("demo").innerHTML = txt;
}
```

### Callback Function

서버 파일을 제어 할 수없는 경우 서버 파일이 올바른 함수를 호출하도록하려면 어떻게해야합니까?

때때로 서버 파일은 매개 변수로 콜백 함수를 제공합니다.

예
PHP 파일은 콜백 매개 변수로 전달한 함수를 호출합니다.

function clickButton() {
  var s = document.createElement("script");
  s.src = "jsonp_demo_db.php?callback=myDisplayFunction";
  document.body.appendChild(s);
}
