---
layout: default
title: Definitions
parent: Functions
grand_parent: JavaScript
nav_order: 1
---

# Functions Definitions
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Definitions

### Declarations

함수 선언은 앞서 보인것처럼 아래 문법으로 선언됨

Syntax
{: .label}
<div class="code-example" markdown="1">
function functionName(parameters) { <br>
  // code to be executed            <br>
}                               
</div>
```js
function myFunction(a, b) {
  return a * b;
}
```

정의된 함수는 바로 실행되는게 아니라 **나중에 호출되면 실행**되는것

### Expressions

JavaScript 함수는 표현식을 사용하여 정의 할수도 있음

