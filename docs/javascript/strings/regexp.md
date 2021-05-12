---
layout: default
title: RegExp
parent: Strings
grand_parent: JavaScript
nav_order: 2
---

# RegExp
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Regular Expressions Basic

### What Is a Regular Expression?

**정규식은 검색패턴 을 형성하는 일련의 문자**

&#9656; 텍스트에서 데이터를 검색할때 이 RegExp을 사용하여 검색중인 내용을 설명할 수 있음

&#9656; RegExp을 사용하여 모든 유형의 텍스트 검색 및 텍스트 바꾸기 작업을 수행 

### Syntax

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
/pattern/modifiers;
</div>
```js
var patt = /w3schools/i;
```

### Modifier

* i : [case-insensitive](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_i)

* g : [global match](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_g)

* m : [multiline matching](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_m)

#### Pattern Expression

**대괄호는 문자 범위를 찾는 데 사용**

* [abc]	: 괄호 안에 있는 [문자들 중 맞는걸](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_abc) 찾음	

* [0-9]	: 괄호 안에 있는 [숫자 사이에 속하는 숫자](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_0-9)를 찾음 

* (x|y)	: `|`로 구분해서 [x 나 y 값이 있는걸](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_xy) 찾음

#### Pattern Metacharacter

**메타 문자 는 특별한 의미를 가진 문자**

*\d : [Find a digit](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_d)

*\s : [Find a whitespace character](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_s)

*\b : Find a match at the beginning of a word like [this: \bWORD](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_b), or at the end of a word like [this: WORD\b](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_b2)

*\uxxxx	: [Find the Unicode character specified by the hexadecimal number xxxx](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_ux)

#### Pattern Quantifier

**수량을 정의**

* n+ : [Matches any string that contains at least one n](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_n1)

* n* : [Matches any string that contains zero or more occurrences of n](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_n2)

* n? : [Matches any string that contains zero or one occurrences of n](https://www.w3schools.com/js/tryit.asp?filename=tryjs_regexp_n3)

---

## Using String Method

### search() With a Regular Expression

search()메서드 : 식을 사용하여 일치 항목을 검색하고 일치 항목의 위치를 반환

예제
{: .label .label-purple .mt-2}
```js
var str = "Visit W3Schools";
var n = str.search(/w3schools/i);

// n = 6
```

### With a Regular Expression

replace()메서드 : 패턴이 대체 된 수정 된 문자열을 반환

예제
{: .label .label-purple .mt-2}
```js
var str = "Visit Microsoft!";
var res = str.replace(/microsoft/i, "W3Schools");

// res = Visit W3Schools!
```

---

## RegExp Object 

**RegExp 개체는 미리 정의된 속성 및 메서드가 있는 정규식 개체**

### Using test() 

**문자열에서 패턴을 검색하고 결과에 따라 true 또는 false를 반환**

정규식 표현 방법

예제
{: .label .label-purple .mt-2}
```js
var patt = /e/;
patt.test("The best things in life are free!");
// 정규식을 변수에 넣을 필요가 없음 : /e/.test("The best things in life are free!");

// true
```

### Using exec() 

**문자열에서 지정된 패턴을 검색하고 찾은 텍스트를 객체로 반환**

정규식 표현 방법

일치하는 항목이 없으면 빈 (null) 개체를 반환

예제
{: .label .label-purple .mt-2}
```js
var obj = /e/.exec("The best things in life are free!");
document.getElementById("demo").innerHTML =
"Found " + obj[0] + " in position " + obj.index + " in the text: " + obj.input;

//Found e in position 2 in the text: The best things in life are free!
```

---

## Complete RegExp Reference

The reference contains descriptions and examples of all RegExp properties and methods

<span class="fs-2">
[W3School](https://www.w3schools.com/jsref/jsref_obj_regexp.asp){: .btn .btn-outline .mt-2}
</span>

