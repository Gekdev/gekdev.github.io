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

## Strings

### JavaScript Programs

16. JavaScript Strings
: are used for storing and manipulating text.

17. JavaScript String Methods
Primitive values, like "John Doe", cannot have properties or methods (because they are not objects).
But with JavaScript, methods and properties are also available to primitive values, because JavaScript treats primitive values as objects when executing methods and properties.

All string methods return a new string. They don't modify the original string.
Formally said: Strings are immutable: Strings cannot be changed, only replaced.

String Length
var sln = txt.length;

Finding a String in a String – indexOf()
var pos = str.indexOf("locate", starting position parameter); 앞에서 먼저 찾음(숫자는 앞에서부터 센담)
var pos = str.lastIndexOf("locate", starting position parameter); 뒤에서 먼저 찾음(숫자는 앞에서부터 세지만)
	* Both indexOf(), and lastIndexOf() return -1 if the text is not found.
	* starting position parameter can be omitted

Both methods accept a second parameter as the starting position for the search: 
	var pos = str.indexOf("locate", 15); 하면 처음부터 숫자를 세서 15+.. 가 나오는데 
		  lastIndexOf("location", 15); 하면 15 다음부터 숫자를 세서 1,2,3.. 이렇게 샌다

Searching for a String in a String – search()
var pos = str.search("locate"); - indexOf와 비슷함
//but this is difference
● The search() method cannot take a second start position argument.
● The indexOf() method cannot take powerful search values (정규식 불가 regular expressions).

Extracting String Parts
● slice(start, end): extracts a part of a string and returns the extracted part in a new string.
● substring(start, end): similar with slice() but the difference is that substring() cannot accept negative indexes.
● substr(start, length): similar with slice() but the difference is that the second parameter specifies the length of the extracted part.

* last parameter can be omitted
* If a parameter is negative(by slice method or substr method), the position is counted from the end of the string. (but Negative positions do not work in Internet Explorer 8 and earlier)
	var str = "Apple, Banana, Kiwi";
	var res = str.slice(-12, -6);

Replacing String Content //원래 변수를 바꾸지는 않음
var n = str.replace("Microsoft", "W3Schools");
* replaces only the first match (To replace all matches, use a regular expression with a /g flag (global match))
	var n = str.replace(/Microsoft/g, "W3Schools");
* case sensitive (To replace case insensitive, use a regular expression with an /i flag (insensitive))
	var n = str.replace(/MICROSOFT/i, "W3Schools");

// Note that regular expressions are written without quotes.

Converting to Upper and Lower Case
var text2 = text1.toUpperCase();  // text2 is text1 converted to upper
var text2 = text1.toLowerCase();  // text2 is text1 converted to lower

The concat() Method: joins two or more strings – 뒤에 ,로 계속 추가 가능 or +...
var text3 = text1.concat(" ", text2);
can be used instead of the plus operator. -- var text = "Hello".concat(" ", "World!");

String.trim():  removes whitespace from both sides of a string:
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

Extracting String Characters
● charAt(position): returns the character at a specified index (position) in a string:
	var str = "HELLO WORLD";
	str.charAt(0);            // returns H
● charCodeAt(position): returns the unicode of the character at a specified index in a string
The method returns a UTF-16 code (an integer between 0 and 65535).
	var str = "HELLO WORLD";
	str.charCodeAt(0);         // returns 72
● Property access [ ]: allows property access [ ] on strings:
	var str = "HELLO WORLD";
	str[0];                   // returns H

Property access might be a little unpredictable
● It does not work in Internet Explorer 7 or earlier
● It makes strings look like arrays (but they are not)
● If no character is found, [ ] returns undefined, while charAt() returns an empty string.
● It is read only. str[0] = "A" gives no error (but does not work!)

Converting a String to an Array
split(“seperator”) method:
	var txt = "a,b,c,d,e";   // String
	txt.split(",");          // Split on commas

If the separator is omitted, the returned array will contain the whole string in index [0]
If the separator is "", the returned array will be an array of single characters:
