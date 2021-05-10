---
layout: default
title: Objects
parent: JavaScript
nav_order: 6
has_children: true
---

# JavaScript Objects Basic 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Objects Basic 

### What is Object?

**자바스크립트의 객체는 키(key)과 값(value)으로 구성된 데이터를 의미하는 프로퍼티(Property)와 데이터를 참조하고 조작할 수 있는 동작(behavior)을 의미하는 메소드(method)로 구성된 집합**

&#9656; 자바스크립트는 객체(object) 기반의 스크립트 언어이며 자바스크립트를 이루고 있는 거의 “모든 것”이 객체 (원시 타입(Primitives)을 제외한 나머지 값들(함수, 배열, 정규표현식 등)은 모두 객체)

&#9656; **자바스크립트의 최상위 부모**

&#9656; 객체는 데이터(프로퍼티)와 그 데이터에 관련되는 동작(메소드)을 모두 포함할 수 있기 때문에 데이터와 동작을 하나의 단위로 구조화할 수 있어 유용

&#9656; 프로퍼티의 값으로 자바스크립트에서 사용할 수 있는 모든 값을 사용할 수 있음

&#9656; 자바스크립트의 함수는 일급 객체이므로 값으로 취급할 수 있음

&#9656; 프로퍼티 값으로 함수를 사용할 수도 있으며 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 메소드라 부름

&#9656; 자바스크립트의 객체는 객체지향의 상속을 구현하기 위해 “프로토타입(prototype)”이라고 불리는 객체의 프로퍼티와 메소드를 상속받을 수 있음(프로토타입은 타 언어와 구별되는 중요한 개념)

&#9656; 객체는 많은 값을 담을 수 있음, 속성이나 메소드의 컨테이너라고 생각하면 됨

<span class="fs-2">
[더 알아보기](https://poiemaweb.com/js-object){: .btn  .btn-outline .mt-2}
</span>

### Object Syntax

값은 주로 **name:value** 쌍으로 나타남 (name and value separated by a colon)

object literal로 객체 생성하기
{: .label .mt-3 }
```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};

or

var person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};
//object definition can span multiple lines
```

### All data types can be Object

**JavaScript에서 거의 모든 것은 객체**

&#9656; 불린값은 객체 일 수 있음 (new키워드로 정의 된 경우)

&#9656; 숫자는 객체가 될 수 있음 (new키워드로 정의 된 경우)

&#9656; 문자열은 객체가 될 수 있음 (new키워드로 정의 된 경우)

&#9656; 날짜는 항상 객체

&#9656; 수학은 항상 객체

&#9656; 정규 표현식은 항상 객체

&#9656; 배열은 항상 객체

&#9656; 함수는 항상 객체

&#9656; 객체는 항상 객체

&#8594; **primitive를 제외한 모든 JavaScript 값은 객체**

### JavaScript Objects are Mutable

**객체는 변경 가능하며, 사본을 생성하지 않고 그 자체가 됨!!**

예제
{: .label .label-purple .mt-3}
```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}

var x = person;
x.age = 10;           // This will change both x.age and person.age

//만약 person이 객체라면, x는 person과 같은 객체가 됨(사본이 아님!)
//x와 person은 동일한 객체이므로 x를 변경하면 사람도 변경된다
```

