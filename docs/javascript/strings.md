---
layout: default
title: Strings
parent: JavaScript
nav_order: 7
has_children: true
---

# JavaScript Strings
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Strings Basic

### What is String?

**(쌍)따옴표안에 쓰여있는 아무것도 없거나 그 이상인 문자들**

&#9656; used for storing and manipulating text

&#9656; 문자열을 둘러싼 따옴표와 일치하지 않는 한 문자열 안에 따옴표를 사용할 수 있음

예시
{: .label .mt-2}
```js
var answer1 = "It's alright";
var answer2 = "He is called 'Johnny'";
var answer3 = 'He is called "Johnny"';
```

&#8594; 만약 두개 다 같은 따옴표를 쓰고싶다면 **backslash escape character**를 사용해야함

### Escape Character

위에서 말한것처럼 문자열을 둘러싼 따옴표와 일치하지 않는 따옴표를 문자열에 사용해야 하지만

같은 따옴표를 사용해야 할 때는 escape character을 사용함

그러면 자바스크립트는 문자열에 쓰여있는 따옴표를 문자열이라고 인지한다

| Code        | Result      | Description           |
|:------------|:------------|:----------------------|
| \'          | '           | Single quote          |
| \"          | "           | Double quote          |
| \\          | \           | Backslash             |

```js
var x = "We are the so-called \"Vikings\" from the north.";

//결과물로 We are the so-called "Vikings" from the north 가 나옴
```

&#8594; 위의 3가지가 자주 쓰이는 escape characters

| Code        | Result      | Description           |
|:------------|:------------|:----------------------|
| \b          | .           | Backspace             |
| \f          | .           | Form Feed             |
| \n          | .           | New Line              |
| \r          | .           | Carriage Return       |
| \t          | .           | Horizontal Tabulator  |
| \v          | .           | Vertical Tabulator    |

&#8594; 위 6가지 문자들은 원래 타자기, 텔레타이프 및 팩스기를 제어하도록 설계되었음

&#8594; html에서는 의미가 없다

### Breaking Long Code Lines

`=`, `+` 오퍼레이터에서 끊거나, `\`에서 끊음

&#9656; **`\` 메소드는 지원이 안되는 브라우저도 있어서 사용권장하지 않음**

&#9656; 꼭 문자열 안 `\`로 사용해야함!

예제
{: .label .label-purple .mt-2}
```js
document.getElementById("demo").innerHTML =
"Hello Dolly!";

document.getElementById("demo").innerHTML = "Hello \
Dolly!";
```

### Strings Can be Objects

문자열을 객체로 선언할 수 있음

&#9656; `new` 키워드는 복잡한 코드라서 계산속도를 늦추기때문에 권장되지 않음

예제
{: .label .label-purple .mt-2}
```js
var x = "John";
var y = new String("John");

// typeof x will return string, value "John"
// typeof y will return object, value "John"
```
위 예제는 `x==y` 는 true지만 `x===y`는 false

또한 둘다 객체로 선언될 경우 **객체는 비교될수 없기 때문에 모두 false**가 나온다
