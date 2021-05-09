---
layout: default
title: Properties and Methods
parent: Strings
grand_parent: JavaScript
nav_order: 1
---

# String Methods and Properties
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## String Property

원래 primitive values 즉 [기본값](https://gekdev.github.io/docs/javascript/basic/data_types/#primitive-data-1)들은 속성이나 메소드들을 가질 수 없지만 **자바스크립트에서는 기본값도 object라고 취급**하기 때문에 그에 관련된 속성과 메소드들을 제공함

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
모든 문자열 메서드는 새 문자열을 반환하고 원래 문자열을 수정하지 않음

문자열은 불변이고 문자열은 바꿀 수 없으며 교체만 가능함!
</div>

### String Length

#### length

**returns the length of a string**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var ttt = txt.length;
</div>
```js
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
var sln = txt.length;

//return 26
```

---

## String Methods

원래 primitive values 즉 [기본값](https://gekdev.github.io/docs/javascript/basic/data_types/#primitive-data-1)들은 속성이나 메소드들을 가질 수 없지만 **자바스크립트에서는 기본값도 object라고 취급**하기 때문에 그에 관련된 속성과 메소드들을 제공함

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
모든 문자열 메서드는 새 문자열을 반환하고 원래 문자열을 수정하지 않음

문자열은 불변이고 문자열은 바꿀 수 없으며 교체만 가능함!
</div>

### Finding a String in a String

#### indexOf() 

**문자열에서 지정된 텍스트 의 첫번째 발생 위치 를 리턴**

&#9656; 앞에서 먼저 찾고, 숫자도 앞에서부터 셈

&#9656; 찾을 수 없을경우 **-1** 리턴

&#9656; 두번째 매개변수(optional)를 검색 시작 위치로 사용, 숫자 카운트도 변하지 않음

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
str.indexOf("string", starting position parameter);
</div>
```js
var str = "Please locate where 'locate' occurs!";
var pos = str.indexOf("locate");
//return 7

var str = "Please locate where 'locate' occurs!";
var pos = str.indexOf("locate",15);
//return 21
```

#### lastIndexOf() 

**문자열에서 지정된 텍스트 의 마지막 발생 위치 를 리턴**

&#9656; 뒤에서 먼저 찾고, 숫자는 앞에서부터 셈

&#9656; 찾을 수 없을경우 **-1** 리턴

&#9656; 두번째 매개변수(optional)를 검색 시작 위치로 사용, 숫자도 매개변수 뒤부터 카운트 시작

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
str.lastIndexOf("string", starting position parameter);
</div>
```js
var str = "Please locate where 'locate' occurs!";
var pos = str.lastIndexOf("locate");
//return 21

var str = "Please locate where 'locate' occurs!";
var pos = str.lastIndexOf("locate", 15);
//return 7
```

#### search()

**문자열에서 지정된 값을 검색하고 일치하는 위치를 리턴**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
str.search("string")
</div>
```js
var str = "Please locate where 'locate' occurs!";
var pos = str.search("locate");
```    

indexOf와 search 메소드의 다른점
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
indexOf()는 정규표현식과 같은 강력한 검색 값을 사용할 수 없음

search()는 두번째 시작 위치 인수를 사용할 수 없음
</div>

### Extracting String Parts

#### slice(start, end)

**문자열의 일부를 추출하고 추출 된 부분을 새 문자열로 반환**

&#9656; 두 번째 매개 변수를 생략하면 나머지 문자열 끝까지 분리

&#9656; 매개 변수가 음수이면 위치는 문자열 끝에서 계산됨

&#8594; Internet Explorer 8 이하에서는 음수 위치가 작동하지 않음
    
Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var res = str.slice(start position, end position);
</div>
```js
var str = "Apple, Banana, Kiwi";
var res = str.slice(7, 13);
//Banana

var res = str.slice(7);
//Banana, Kiwi

var res = str.slice(-12, -6);
//Banana

var res = str.slice(-12);
//Banana, Kiwi
```

#### substring(start, end)

&#9656; slice()와 비슷하게 동작하지만 음수 매개변수를 승인하지 않음

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var res = str.substring(start position, end position);
</div>
```js
var str = "Apple, Banana, Kiwi";
var res = str.substring(7, 13);
//Banana
```

#### substr(start, length)

&#9656; slice()와 비슷하게 동작하지만 substr의 두번째 매개 변수는 길이를 지정함

&#9656; 첫 번째 매개 변수가 음수이면 위치는 끝에서부터 계산

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var res = str.substr(start position, length);
</div>
```js
var str = "Apple, Banana, Kiwi";
var res = str.substr(7, 6);
//Banana

var str = "Apple, Banana, Kiwi";
var res = str.substr(7);
//Banana, Kiwi

var str = "Apple, Banana, Kiwi";
var res = str.substr(-4);
//Kiwi
```

### Replacing String 

#### replace() 

**지정된 값을 문자열의 다른 값으로 바꿈**

&#9656; 원래 문자열을 변경하지 않고, 새 문자열로 반환

&#9656; 첫번째로 매치된 값만 바꿈, 표현 정규식으로 바꿀 수 있음

&#9656; case-sensitive함, 표현 정규식으로 바꿀 수 있음

&#9656; 표현 정규식은 따옴표 없이 사용됨

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var n = str.replace("찾는 문자열", "바꿀 문자열");
</div>
```js
str = "Please visit Microsoft!";
var n = str.replace("Microsoft", "W3Schools");
//Microsoft → W3Schools

str = "Please visit Microsoft!";
var n = str.replace(/MICROSOFT/i, "W3Schools");
//insensitive

str = "Please visit Microsoft and Microsoft!";
var n = str.replace(/Microsoft/g, "W3Schools");
//모든 문자열 변환
```

### Converting to Upper and Lower Case

#### toUpperCase()

**converted to upper case**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var text2 = text1.toUpperCase();
</div>
```js
var text1 = "Hello World!";       // String
var text2 = text1.toUpperCase();  // text2 is text1 converted to upper
//HELLO WORLD!
```

#### toLowerCase()

**converted to upper case**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var text2 = text1.toUpperCase();
</div>
```js
var text1 = "Hello World!";       // String
var text2 = text1.toLowerCase();  // text2 is text1 converted to lower
//hello world!
```

### Join Strings

#### concat()

**두 개 이상의 문자열을 조인**

&#9656; 문자열의 결합이니까 `+` operator 대신 사용해도 됨

&#9656; 뒤에 ,로 계속 추가 가능 or +...

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var text3 = text1.concat(" ", text2);
</div>
```js
var text1 = "Hello";
var text2 = "World";
var text3 = text1.concat(" ", text2);
//Hello World!

var text = "Hello" + " " + "World!";
var text = "Hello".concat(" ", "World!");
//이와 같이 표현하기도 함
```

### Repeating Strings

#### repeat 

**요소를 반복시키기**

&#9656; 매개변수는 얼마나 반복시킬지 결정

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
string.repeat(count)
</div>
```js
var str = "Hello world!";
str.repeat(2);
//result is Hello world!Hello world!
```

### Removing whitespace

#### trim()

**양쪽에 공백 지우기**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
str.trim()
</div>
```js
var str = "       Hello World!        ";
alert(str.trim());
```

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
trim()은 Internet Explorer 8 or lower에는 지원하지 않음

그 아래에서 지원하고 싶게 만들려면 replace() 와 정규표현식으로 사용해야함
</div>
```js
var str = "       Hello World!        ";
alert(str.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, ''));

//string.prototype을 사용해서 trim function을 정의할수도 있음
String.prototype.trim = function () {
    return this.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, '');
  };
}
var str = "       Hello World!        ";
alert(str.trim());
```

### Extracting String Characters

#### charAt(position)

**문자열의 지정된 인덱스에있는 문자를 반환**

```js
var str = "HELLO WORLD";
str.charAt(0);            

// returns H
```

#### charCodeAt(position)

**문자열의 지정된 인덱스에서 문자의 유니 코드를 리턴**

&#9656; 이 메소드는 UTF-16 코드 (0과 65535 사이의 정수)를 리턴

```js
var str = "HELLO WORLD";
str.charCodeAt(0);     

// returns 72
```

#### Property access [ ]

**allows property access [ ] on strings**

```js
var str = "HELLO WORLD";
str[0];                   
// returns H
```

Property access might be a little unpredictable
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
&#9656; It does not work in Internet Explorer 7 or earlier

&#9656; It makes strings look like arrays (but they are not)

&#9656; If no character is found, [ ] returns undefined, while charAt() returns an empty string.

&#9656; It is read only. str[0] = "A" gives no error (but does not work!)
</div>
```js
var str = "HELLO WORLD";
str[0] = "A";             // Gives no error, but does not work
str[0];                   // returns H
```

### Converting a String to an Array

#### split(“seperator”)

**문자열을 배열로 바꾸는 메소드**

&#9656; separator가 생략되면 전체 문자열을 배열 0번째에 넣어버림

```js
var txt = "a,b,c,d,e";   // String
var arr = txt.split(",");          // Split on commas
//arr = [a,b,c,d,e]

txt.split(" ");          // Split on spaces
txt.split("|");          // Split on pipe
txt.split("");           // Split in characters
```

---

## Complete String Reference

The reference contains descriptions and examples of all string properties and methods

<span class="fs-2">
[더 찾아보기](https://www.w3schools.com/jsref/jsref_obj_string.asp){: .btn  .btn-outline}
</span>
