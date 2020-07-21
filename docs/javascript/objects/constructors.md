---
layout: default
title: Constructors
parent: Objects
grand_parent: JavaScript
nav_order: 6
---

# Objects Constructors
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Object Types (Blueprints) (Classes)

이전 장의 예는 제한되어 있습니다. 단일 객체 만 생성합니다.

때로는 같은 "유형"의 많은 객체를 생성하기 위해 " 청사진 "이 필요합니다 .

"객체 유형"을 생성하는 방법은 객체 생성자 함수 를 사용하는 것 입니다.

위의 예 function Person()에서 객체 생성자 함수입니다.

new키워드 와 함께 생성자 함수를 호출하여 동일한 유형의 객체를 만듭니다.

var myFather = new Person("John", "Doe", 50, "blue");
var myMother = new Person("Sally", "Rally", 48, "green");
이 키워드
JavaScript에서 호출되는 것은 this코드를 "소유"하는 객체입니다.

this객체에 사용될 때 의 값은 객체 자체입니다.

생성자 함수 this에는 값이 없습니다. 새 객체를 대체합니다. this새 개체를 만들 때 의 값은 새 개체가됩니다.

참고 this변수가 아닙니다. 키워드입니다. 의 값을 변경할 수 없습니다 this.

객체에 속성 추가
기존 객체에 새 속성을 추가하는 것은 쉽습니다.

예
myFather.nationality = "English";
속성이 myFather에 추가됩니다. myMother가 아닙니다. (다른 사람에게는 해당되지 않음).

객체에 메소드 추가
기존 객체에 새로운 방법을 추가하는 것은 쉽습니다.

예
myFather.name = function () {
  return this.firstName + " " + this.lastName;
};
메소드가 myFather에 추가됩니다. myMother가 아닙니다. (다른 사람에게는 해당되지 않음).

생성자에 속성 추가
기존 객체에 새 속성을 추가하는 것과 같은 방식으로 객체 생성자에 새 속성을 추가 할 수 없습니다.

예
Person.nationality = "English";
생성자에 새 속성을 추가하려면 생성자 함수에 추가해야합니다.

예
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
  this.nationality = "English";
}
이 방법으로 객체 속성에 기본값이있을 수 있습니다.

생성자에 메소드 추가
생성자 함수는 메소드를 정의 할 수도 있습니다.

예
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
  this.name = function() {return this.firstName + " " + this.lastName;};
}
기존 객체에 새 메소드를 추가하는 것과 같은 방법으로 객체 생성자에 새 메소드를 추가 할 수 없습니다.

생성자 함수 내에서 객체 생성자에 메소드를 추가해야합니다.

예
function Person(firstName, lastName, age, eyeColor) {
  this.firstName = firstName; 
  this.lastName = lastName;
  this.age = age;
  this.eyeColor = eyeColor;
  this.changeName = function (name) {
    this.lastName = name;
  };
}
changeName () 함수는 name 값을 사람의 lastName 속성에 할당합니다.

이제 시도해 볼 수 있습니다 :
myMother.changeName("Doe");
JavaScript는 이것을 myMother 로 "대체" 하여 대화 상대 를 알고 있습니다.

내장 JavaScript 생성자
JavaScript에는 기본 객체에 대한 생성자가 내장되어 있습니다.

예
var x1 = new Object();    // A new Object object
var x2 = new String();    // A new String object
var x3 = new Number();    // A new Number object
var x4 = new Boolean();   // A new Boolean object
var x5 = new Array();     // A new Array object
var x6 = new RegExp();    // A new RegExp object
var x7 = new Function();  // A new Function object
var x8 = new Date();      // A new Date object
Math()개체가 목록에 없습니다. Math전역 객체입니다. 에 new키워드를 사용할 수 없습니다 Math.

알고 계십니까?
위에서 볼 수 있듯이, 자바 스크립트는 기본 데이터 형의 객체 버전이 String, Number하고 Boolean. 그러나 복잡한 객체를 만들 이유가 없습니다. 기본 값이 훨씬 빠릅니다.

또한:

{}대신 객체 리터럴을 사용하십시오 new Object().

""대신 문자열 리터럴을 사용하십시오 new String().

12345대신 숫자 리터럴을 사용하십시오 new Number().

true / false대신 부울 리터럴을 사용하십시오 new Boolean().

[]대신 배열 리터럴을 사용하십시오 new Array().

/()/대신 패턴 리터럴을 사용하십시오 new RegExp().

() {}대신 함수 표현식을 사용하십시오 new Function().

예
var x1 = {};            // new object
var x2 = "";            // new primitive string
var x3 = 0;             // new primitive number
var x4 = false;         // new primitive boolean
var x5 = [];            // new array object
var x6 = /()/           // new regexp object
var x7 = function(){};  // new function object
문자열 객체
일반적으로 문자열은 기본 요소로 작성됩니다. var firstName = "John"

그러나 new키워드를 사용하여 문자열을 객체로 만들 수도 있습니다 .var firstName = new String("John")

JS 문자열 장에서 문자열 을 객체로 생성하지 않아야하는 이유를 알아 봅니다 .

숫자 객체
일반적으로 숫자는 기본 요소로 작성됩니다. var x = 123

그러나 new키워드를 사용하여 숫자를 객체로 만들 수도 있습니다 .var x = new Number(123)

JS Numbers 장에서 숫자 를 객체로 생성하지 않아야하는 이유를 알아 봅니다 .

부울 객체
일반적으로 부울은 기본 요소로 작성됩니다. var x = false

그러나 new키워드를 사용하여 부울을 객체로 만들 수도 있습니다 .var x = new Boolean(false)

JS 부울 장에서 부울 을 객체로 생성하지 않아야하는 이유를 알아 봅니다 .

