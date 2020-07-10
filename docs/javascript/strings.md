---
layout: default
title: Strings
parent: JavaScript
nav_order: 3
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

used for storing and manipulating text

문자열을 둘러싼 따옴표와 일치하지 않는 한 문자열 안에 따옴표를 사용할 수 있음

```js
var answer1 = "It's alright";
var answer2 = "He is called 'Johnny'";
var answer3 = 'He is called "Johnny"';
```

&#8594; 만약 두개 다 같은 따옴표를 쓰고싶다면 **backslash escape character**를 사용해야함

### Escape Character

위에서 말한것처럼 문자열을 둘러싼 따옴표와 일치하지 않는 따옴표를 문자열에 사용해야 하지만

같은 따옴표를 사용해야 할 때 escape character을 사용함

그러면 자바스크립트는 문자열에 쓰여있는 따옴표를 문자열이라고 인지함

| Code        | Result      | Description           |
|:------------|:------------|:----------------------|
| \'          | '           | Single quote          |
| \"          | "           | Double quote          |
| \\          | \           | Backslash             |

위의 3가지가 자주 쓰이는 escape characters

예제
{: .label .label-purple .mt-2}
```js
var x = "We are the so-called \"Vikings\" from the north.";

//결과물로 We are the so-called "Vikings" from the north 가 나옴
```

| Code        | Result      | Description           |
|:------------|:------------|:----------------------|
| \b          | .           | Backspace             |
| \f          | .           | Form Feed             |
| \n          | .           | New Line              |
| \r          | .           | Carriage Return       |
| \t          | .           | Horizontal Tabulator  |
| \v          | .           | Vertical Tabulator    |

위 6가지 문자들은 원래 타자기, 텔레타이프 및 팩스기를 제어하도록 설계되었음

&#8594; html에서는 의미가 없다

### Breaking Long Code Lines

`=`, `+` 오퍼레이터에서 끊거나, `\`에서 끊음

**`\` 메소드는 지원이 안되는 브라우저도 있어서 사용권장하지 않음**

&#8594; 꼭 문자열 안 `\`로 사용해야함!

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

`new` 키워드는 복잡한 코드라서 계산속도를 늦추기때문에 권장되지 않음

아래 예제는 `==` 는 true지만 `===`는 false

또한 둘다 객체로 선언될 경우 **객체는 비교될수 없기 때문에 모두 false**가 나온다

```js
var x = "John";
var y = new String("John");

// typeof x will return string, value "John"
// typeof y will return object, value "John"
```

---

## JavaScript String Methods

원래 primitive values 즉 [기본값](https://gekdev.github.io/docs/javascript/4.datatypes/#primitive-data)들은 속성이나 메소드들을 가질 수 없지만 **자바스크립트에서는 기본값도 object라고 취급**하기 때문에 그에 관련된 속성과 메소드들을 제공함

### String Length

built-in length property : **returns the length of a string**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var ttt = txt.length;
</div>

예제
{: .label .label-purple .mt-2}
```js
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
var sln = txt.length;

//return 26
```

### Finding a String in a String

* indexOf() 

    **문자열에서 지정된 텍스트 의 첫번째 발생 위치 를 리턴**

    Syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    str.indexOf("string", starting position parameter);
    </div>
    
    &#9656; 앞에서 먼저 찾고, 숫자도 앞에서부터 셈
    
    &#9656; 찾을 수 없을경우 **-1** 리턴
    
    &#9656; 두번째 매개변수(optional)를 검색 시작 위치로 사용, 숫자 카운트도 변하지 않음

    ```js
    var str = "Please locate where 'locate' occurs!";
    var pos = str.indexOf("locate");
    //return 7

    var str = "Please locate where 'locate' occurs!";
    var pos = str.indexOf("locate",15);
    //return 21
    ```

* `lastIndexOf()` : **문자열에서 지정된 텍스트 의 마지막 발생 위치 를 리턴**
    
    Syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    str.lastIndexOf("string", starting position parameter);
    </div>
    
    &#9656; 뒤에서 먼저 찾고, 숫자는 앞에서부터 셈
    
    &#9656; 찾을 수 없을경우 **-1** 리턴
    
    &#9656; 두번째 매개변수(optional)를 검색 시작 위치로 사용, 숫자도 매개변수 뒤부터 카운트 시작
    
    ```js
    var str = "Please locate where 'locate' occurs!";
    var pos = str.lastIndexOf("locate");
    //return 21

    var str = "Please locate where 'locate' occurs!";
    var pos = str.lastIndexOf("locate", 15);
    //return 7
    ```

* `search()` : **문자열에서 지정된 값을 검색하고 일치하는 위치를 리턴**

    ```js
    var str = "Please locate where 'locate' occurs!";
    var pos = str.search("locate");
    ```

indexOf와 search 메소드의 다른점
{: .label .labe-yellow .mt-2}
<div class="code-example" markdown="1">
indexOf()는 정규표현식과 같은 강력한 검색 값을 사용할 수 없음

search()는 두번째 시작 위치 인수를 사용할 수 없음
</div>

### Extracting String Parts

* `slice(start, end)`

* `substring(start, end)`

* `substr(start, length)`

### Replacing String Content

* `replace()`




All string methods return a new string. They don't modify the original string.
Formally said: Strings are immutable: Strings cannot be changed, only replaced.




### Replacing String Content 

//원래 변수를 바꾸지는 않음
var n = str.replace("Microsoft", "W3Schools");
* replaces only the first match (To replace all matches, use a regular expression with a /g flag (global match))
	var n = str.replace(/Microsoft/g, "W3Schools");
* case sensitive (To replace case insensitive, use a regular expression with an /i flag (insensitive))
	var n = str.replace(/MICROSOFT/i, "W3Schools");

// Note that regular expressions are written without quotes.

### Converting to Upper and Lower Case
var text2 = text1.toUpperCase();  // text2 is text1 converted to upper
var text2 = text1.toLowerCase();  // text2 is text1 converted to lower

### The concat() Method
: joins two or more strings – 뒤에 ,로 계속 추가 가능 or +...
var text3 = text1.concat(" ", text2);
can be used instead of the plus operator. -- var text = "Hello".concat(" ", "World!");

### String.trim():  removes whitespace from both sides of a string:
var str = "       Hello World!        ";
alert(str.trim());

// The trim() method is not supported in Internet Explorer 8 or lower. 
	use this : alert(str.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, ''));

동시에 같이 쓰려면 이거 쓰세영
if (!String.prototype.trim) {
  String.prototype.trim = function () {
    return this.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, '');
  };
}
var str = "       Hello World!        ";
alert(str.trim());

### Extracting String Characters
* charAt(position): returns the character at a specified index (position) in a string:
	var str = "HELLO WORLD";
	str.charAt(0);            // returns H
* charCodeAt(position): returns the unicode of the character at a specified index in a string
The method returns a UTF-16 code (an integer between 0 and 65535).
	var str = "HELLO WORLD";
	str.charCodeAt(0);         // returns 72
* Property access [ ]: allows property access [ ] on strings:
	var str = "HELLO WORLD";
	str[0];                   // returns H

Property access might be a little unpredictable
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
&#9656; It does not work in Internet Explorer 7 or earlier

&#9656; It makes strings look like arrays (but they are not)

&#9656; If no character is found, [ ] returns undefined, while charAt() returns an empty string.

&#9656; It is read only. str[0] = "A" gives no error (but does not work!)
</div>

Converting a String to an Array
split(“seperator”) method:
	var txt = "a,b,c,d,e";   // String
	txt.split(",");          // Split on commas

If the separator is omitted, the returned array will contain the whole string in index [0]
If the separator is "", the returned array will be an array of single characters:
