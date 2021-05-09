---
layout: default
title: Properties and Technics
parent: Arrays
grand_parent: JavaScript
nav_order: 1
---

# Array Properties and Technics
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Array Property

배열에는 정말 좋은 built-in 속성과 메소드가 있음

### Array length

#### length

**배열의 길이(배열 요소 수)를 반환**

&#9656; index가 0부터 시작하기 때문에 항상 가장 높은 배열 인덱스보다 하나 이상임

&#9656; for문으로 요소를 추출할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.length; 
</div>
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.length;   // the length of fruits is 4
```

Accessing the Last Array Element
{: .label .label-purple .mt-2}
```js
fruits = ["Banana", "Orange", "Apple", "Mango"];
var last = fruits[fruits.length - 1];
```

---

## Array Technics

### Creating an Array

**배열 리터럴을 사용하는 것이 JavaScript 배열을 만드는 가장 쉬운 방법**

&#9656; 줄바꿈과 공백은 규칙만 지킨다면 여러줄에 걸쳐 사용가능

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var array_name = [item1, item2, ...];
</div>

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
var a = new Array(“”,“”,“”...); 도 위와 같이 정확하게 동일한 배열을 만드는 방법

하지만 단순성, 가독성, 실행속도를 위해 사용 자제해야 함
</div>

### Accessing the Elements

**인덱스 번호로 배열 값에 접근하기**

&#9656; 인덱스는 0부터 시작

&#9656; 배열 전체로 접근하려면 []없이 이름만 사용

syntax
{: .label .mt-2}
```js
var name = a[0];    //0번째 값 가져오기
var name = a;       //a배열 전체 가져오기
```

#### Looping Array Elements

1. length (for loop)

    ```js
    text = "<ul>";
    for (i = 0; i < fruits.length ; i++) {
      text += "<li>" + fruits[i] + "</li>";
    }
    text += "</ul>";
    ```

2. Array.forEach()

    ```js
    var fruits, text;
    fruits = ["Banana", "Orange", "Apple", "Mango"];

    text = "<ul>";
    fruits.forEach(myFunction);
    text += "</ul>";

    function myFunction(value) {
      text += "<li>" + value + "</li>";
    }
    ```

#### Changing Elements

**인덱스 번호를 사용하여 액세스한 후 변경**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr[0] = "";
</div>
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits[0] = "Kiwi";        // Changes the first element of fruits to "Kiwi"
```

