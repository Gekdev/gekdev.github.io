---
layout: default
title: Properties
parent: Objects
grand_parent: JavaScript
nav_order: 2
---

# Objects Properties
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

--- 

## JavaScript Properties

속성은 자바스크립트 객체에서 가장 중요한 부분!

**JavaScript 객체는 정렬되지 않은 속성의 모음이고 속성은 JavaScript 객체와 관련된 값** 

속성은 일반적으로 변경, 추가 및 삭제할 수 있지만 일부는 읽기 전용임

### Accessing JavaScript Properties

객체의 속성에 액세스하는 3가지 구문

1. objectName.property         // person.age

2. objectName["property"]      // person["age"]

3. objectName[expression]      // x = "age"; person[x]

### JavaScript for...in Loop


### Adding New Properties

**단순히 값을 지정하여 기존 객체에 새 속성을 추가** 할 수 있음

예제
{: .label .label-purple .mt-3}
```js
person.nationality = "English";
```

### Deleting Properties

delete키워드는 **객체로부터 속성 값과 속성 자체를 모두 삭제함**

&#9656; 삭제 후에는 속성을 다시 추가하기 전에 사용할 수 없음

&#9656; delete연산자는 객체 속성에 사용되도록 설계되었음, 변수 나 함수에는 영향을 미치지 않음

&#9656; delete연산자는 미리 정의 된 자바 스크립트 객체 속성에 사용할 수 없음. 응용 프로그램이 중단 될 수 있음

예제
{: .label .label-purple .mt-3}
```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
delete person.age;   // or delete person["age"];
```

### Property Attributes

모든 속성에는 이름과 값이 있음, 값(value)은 property's attributes

다른 속성들 : enumerable, configurable, and writable

&#9656; 이러한 속성은 속성에 액세스하는 방법을 정의함

&#9656; JavaScript에서는 모든 속성을 읽을 수 있지만 value 속성 만 변경할 수 있음 (속성이 쓰기 가능한 경우에만)

