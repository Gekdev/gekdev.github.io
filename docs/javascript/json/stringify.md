---
layout: default
title: Stringify
parent: JSON
grand_parent: JavaScript
nav_order: 4
---

# JSON.stringify()
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSON.stringify()

### Stringify a JavaScript Object

**JavaScript 객체를 문자열로 변환**

사용하면 객체는 JSON 표기법을 따르는 문자열이 됨

JSON의 일반적인 용도는 웹 서버와 데이터를 주고받는것

**웹 서버로 데이터를 보낼 때 데이터는 문자열**이어야함

`JSON.stringify()`으로 자바스크립트 객체를 문자열로 변환

#### Example

1. 이 객체가 JavaScript에 있음

    ```js
    var obj = { name: "John", age: 30, city: "New York" };
    ```

2. JavaScript 함수 JSON.stringify()를 사용하여 문자열로 변환

    ```js
    var myJSON = JSON.stringify(obj);
    ```
    
3. myJSON이 문자열이 되고 서버로 보낼 준비가 됨

    ```js
    var obj = { name: "John", age: 30, city: "New York" };
    var myJSON = JSON.stringify(obj);
    document.getElementById("demo").innerHTML = myJSON;

    //{"name":"John","age":30,"city":"New York"}
    ```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjson_stringify){: .btn  .btn-outline .mt-2}
</span>

### Stringify a JavaScript Array

1. 이 객체가 JavaScript에 있음

    ```js
    var arr = [ "John", "Peter", "Sally", "Jane" ];
    ```

2. JavaScript 함수 JSON.stringify()를 사용하여 문자열로 변환
    
    ```js
    var myJSON = JSON.stringify(arr);
    ```
    
3. myJSON이 문자열이 되고 서버로 보낼 준비가 됨

    ```js
    var arr = [ "John", "Peter", "Sally", "Jane" ];
    var myJSON = JSON.stringify(arr);
    document.getElementById("demo").innerHTML = myJSON;

    //["John","Peter","Sally","Jane"]       
    ```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjson_stringify_array){: .btn  .btn-outline .mt-2}
</span>


### Exceptions - Stringify Dates

날짜 객체는 JSON에서 허용되지 않음

날짜를 포함해야하는 경우 모든 날짜를 문자열로 변환해야함 (수신자로 문자열을 다시 날짜 객체로 변환 할 수 있음)

예제 
{: .label .label-purple .mt-3}
```js
var obj = { name: "John", today: new Date(), city : "New York" };
var myJSON = JSON.stringify(obj);

document.getElementById("demo").innerHTML = myJSON;
```

### Exceptions - Stringify Functions

JSON에서 함수는 객체 값으로 허용되지 않음

함수를 포함해야 할 경우 **문자열로 작성**해야함 (나중에 함수로 다시 변환 할 수 있음)

`JSON.stringify()` 메소드는 JavaScript 객체에서 함수를 제거(키와 값 모두)

함수를 제거하고 싶지 않으면 `toString()` 메소드를 사용해야 함

예제 : stringify 메소드 사용
{: .label .label-purple .mt-3}
```js
var obj = { name: "John", age: function () {return 30;}, city: "New York"};
var myJSON = JSON.stringify(obj);

document.getElementById("demo").innerHTML = myJSON;
```

예제 : toString 메소드 사용
{: .label .label-purple .mt-3}
```js
var obj = { name: "John", age: function () {return 30;}, city: "New York" };
obj.age = obj.age.toString();
var myJSON = JSON.stringify(obj);

document.getElementById("demo").innerHTML = myJSON;
```

!warning
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
최대한 함수를 사용하는걸 줄여야 함. 함수의 범위가 없어지고, eval() 메소드로 함수로 다시 변환하는데에 사용해야 하기 때문
</div>

### 브라우저 지원

`JSON.stringify()`은 **모든 주요 브라우저와 최신 ECMAScript (JavaScript) 표준에 포함**

