---
layout: default
title: Data types
parent: JavaScript
nav_order: 5
has_children: true
---

# JavaScript Data types
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Data type Basic

### The Concept of Data Types

&#9656; 프로그래밍에서 데이터 타입은 중요한 개념

&#9656; 변수를 조작하려면 그 변수가 어떤 데이터 타입인지 알아야 함

&#9656; numbers, strings(text values), object{}, booleans, arrays등이 있음

### [Primitive Data](https://gekdev.github.io/docs/javascript/datatypes/primitive_complex/#primitive-data-1)

추가적인 속성이나 메소드가 없는 단순한 기본 데이터

&#9656; string, number, boolean, undefined, empty values가 있음

```js
typeof "John"              // Returns "string"
typeof 3.14                // Returns "number"
typeof true                // Returns "boolean"
typeof false               // Returns "boolean"
typeof x                   // Returns "undefined" (if x has no value)
```

### [Complex Data](https://gekdev.github.io/docs/javascript/datatypes/primitive_complex/#complex-data)

기본 데이터보다 좀더 복잡한 형식으로 되어있는 데이터들 

&#9656; function, object (objects, arrays, and null)가 있음

```js
typeof {name:'John', age:34} // Returns "object"
typeof [1,2,3,4]             // Returns "object" (not "array", see note below)
typeof null                  // Returns "object"
typeof function myFunc(){}   // Returns "function"
```
