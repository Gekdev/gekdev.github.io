---
layout: default
title: Call & Apply
parent: Functions
grand_parent: JavaScript
nav_order: 4
---

# Functions Call & Apply
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Method Reuse

### All Functions are Methods

**모든 함수는 메소드**

함수가 자바스크립트 객체의 메소드가 아니라면, [전역 객체(window)의 함수]()가 됨

아래 예제는 firstName, lastName, fullName이라는 3 개의 속성을 가진 객체를 만듦

예제
{: .label .label-purple .mt-3}
```js
var person = {
  firstName:"John",
  lastName: "Doe",
  fullName: function () {
    return this.firstName + " " + this.lastName;
  }
}
person.fullName();   // Will return "John Doe"
```

### The JavaScript call() Method

**소유자 객체를 인수로 사용하여 메소드를 호출**하는 데 사용할 수 있음

자바스크립트의 미리 정의된 메소드

* 객체가 다른 객체에 속하는 메소드를 사용하기

    예제
    {: .label .label-purple .mt-3}
    ```js
    var person = {
      fullName: function() {
        return this.firstName + " " + this.lastName;
      }
    }
    var person1 = {
      firstName:"John",
      lastName: "Doe"
    }
    var person2 = {
      firstName:"Mary",
      lastName: "Doe"
    }

    person.fullName.call(person1);  // "John Doe"
    person.fullName.call(person2);  // "Mary Doe"
    ```

* call()메소드는 인수를 받음

    예제
    {: .label .label-purple .mt-3}
    ```js
    var person = {
      fullName: function(city, country) {
        return this.firstName + " " + this.lastName + "," + city + "," + country;
      }
    }
    var person1 = {
      firstName:"John",
      lastName: "Doe"
    }
    person.fullName.call(person1, "Oslo", "Norway"); // John Doe,Oslo,Norway
    ```

### The JavaScript apply() Method

call() 메소드와 비슷함

하지만 인수를 어떤 형식으로 받느냐에 따라 다름!

* 객체가 다른 객체에 속하는 메소드를 사용하기

    예제
    {: .label .label-purple .mt-3}
    ```js
    var person = {
      fullName: function() {
        return this.firstName + " " + this.lastName;
      }
    }
    var person1 = {
      firstName: "Mary",
      lastName: "Doe"
    }
    person.fullName.apply(person1);  // Will return "Mary Doe"
    ```

* apply() 메소드는 인수를 받음

    예제
    {: .label .label-purple .mt-3}
    ```js
    var person = {
      fullName: function(city, country) {
        return this.firstName + " " + this.lastName + "," + city + "," + country;
      }
    }
    var person1 = {
      firstName:"John",
      lastName: "Doe"
    }
    person.fullName.apply(person1, ["Oslo", "Norway"]); // John Doe,Oslo,Norway
    ```

The Difference Between call() and apply()
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">

**두번째 매개변수를 어떤 형식으로 받느냐**에 따라 달라짐

* call() method : takes arguments separately

* apply() method : takes arguments as an array

    &#8594; very handy if you want to use an array instead of an argument list
</div>

JavaScript Strict Mode
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
JavaScript의 엄격한 모드에서 apply()메소드 의 첫 번째 인수가 오브젝트가 아닌 경우, 호출 된 함수의 소유자 (오브젝트)가됨 

"엄격하지 않은"모드에서는 전역 객체가됩
</div>

### Simulate a Max Method on Arrays

단일 인수로 최대값을 찾을때에는 Math.max()를 사용하면 되지만, 배열일때는 사용할 수 없음

따라서 apply() 메소드를 활용해 배열을 인수로 활용해 최대값을 찾을 수 있음

```js
Math.max(1,2,3);  // Will return 3

Math.max.apply(null, [1,2,3]); // Will also return 3
```

최대값을 계산할 값들이 두번째 매개변수에 배열로 들어가있어서 첫 번째 인수 (null)는 중요하지 않음

&#8594; null, "", grace, 0 다 가능함 (공백은 안됨)

