---
layout: default
title: Selector
parent: CSS
nav_order: 3
---

# Selector
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Selector

### What is list?

CSS Selectors - ID selectors have a higher specificity than attribute selectors 
	CSS selectors are used to "find" (or select) the HTML elements you want to style.

    We can divide CSS selectors into five categories:

    ＊Simple selectors (select elements based on name, id, class)
    ＊Combinator selectors (select elements based on a specific relationship between them)
    ＊Pseudo-class selectors (select elements based on a certain state)
    ＊Pseudo-elements selectors (select and style a part of an element)
        A pseudo-class is used to define a special state of an element.
            Style an element when a user mouses over it
            Style visited and unvisited links differently
            Style an element when it gets focus
    ＊Attribute selectors (select elements based on an attribute or attribute value)
    * CSS [attribute] Selector : The [attribute] selector is used to select elements with a specified attribute. 문법 부가어적인 

쓰능방법 & 여기 짱마늠 : https://www.w3schools.com/css/css_attribute_selectors.asp

^= : 시작만 / &=: 끝만 / ~=: 단독으로 / |=: 시작으로 / *=: 만 있다면/ 


★ Pseudo-class
Note: a:hover MUST come after a:link and a:visited in the CSS definition in order to be effective! a:active MUST come after a:hover in the CSS definition in order to be effective! Pseudo-class names are not case-sensitive.

:link – unvisited site

hover로 나타나는 p 태그 만들기
	p {display: none; or visibility: hidden}

	div:hover p{display: block; or visibility: visible}

:lang pseudo-class allows you to define special rules for different languages.
q:lang(no) {quotes: "~" "~";}
 <q lang="no">A quote in a paragraph</q> 

★ Pseudo-element
A CSS pseudo-element is used to style specified parts of an element.

	Style the first letter, or line, of an element
	Insert content before, or after, the content of an element

Notice the double colon notation - ::first-line versus :first-line

The double colon replaced the single-colon notation for pseudo-elements in CSS3. This was an attempt from W3C to distinguish between pseudo-classes and pseudo-elements.
The single-colon syntax was used for both pseudo-classes and pseudo-elements in CSS2 and CSS1.
For backward compatibility, the single-colon syntax is acceptable for CSS2 and CSS1 pseudo-elements.

::first-line / ::first-letter (only be applied to block-level elements)
Several pseudo-elements can also be combined.

::before pseudo-element can be used to insert some content before the content of an element.
::after pseudo-element can be used to insert some content after the content of an element.
::selection pseudo-element matches the portion of an element that is selected by a user.


*<name<class<id 순으로 우선순위
● 태그이름 셀렉터 : 여러개일 경우 ,로 구분 
		h3, li{color:brown;}
● id 셀렉터 : # - id
		#앞에 태그 이름을 사용해 특정 태그에만 적용되도록 할 수 있다
		특정 태그에만 사용되는 경우 다른 태그에 중복 불가능 함
		case-sensitive
		The id of an element is unique within a page, so the id selector is used to select one unique element!


The id value can be used by CSS and JavaScript to perform certain tasks for the element with the specific id value.

Note: The id value is case-sensitive.
Note: The id value must contain at least one character, and must not contain whitespace (spaces, tabs, etc.).

JavaScript can access an element with a specified id by using the getElementById()

● class 셀렉터 : . - class
		.으로 시작하는 셀렉터는 어떤 셀렉터에서도 사용 가능
		태그 이름과 같이 만들어진 경우 (body.main) 해당 태그(body)에 제한됨 
		To select elements with a specific class, write a period (.) character, followed by the class name.
		case-sensitive
Multiple Classes
HTML elements can have more than one class name, each class name must be separated by a space.

JavaScript can access elements with a specified class name by using the getElementsByClassName()

		In this example only <p> elements with class="center" will be center-aligned: 

		p.center {
		  text-align: center;
		  color: red;
		}

▶ Difference Between Class and ID
An HTML element can only have one unique id that belongs to that single element, while a class name can be used by multiple elements:

● 자식 셀렉터 : 부모 자식 관계를 >로 조합한 형태 (A태그 자손 B태그에 걸어주세요) child selector (exactly my child)
● 자손 셀렉터 : 자손 관계인 태그를 나열 (A태그 안에 B태그에 걸어주세요) descendant selector (everything)
● The CSS Universal Selector : *(와일드 카드 문자)를 사용해 모든 태그에 적용
● General Sibling Selector ~
The general sibling selector selects all elements that are siblings of a specified element.
● Adjacent Sibling Selector + : selects all elements that are the adjacent siblings of a specified element.
Sibling elements must have the same parent element, and "adjacent" means "immediately following".
● 속성 셀렉터 : 특정 속성(attribute)에 일치하는 태그에만 적용
		input[type=text]{color:red;}
● 가상클래스 셀렉터 : 어떤 상황이 발생했을때만 적용하는 셀렉터(40여종)
		a:visited{color:green;}
		:뒤에 빈칸이 오면 안됨

유형
셀렉터
설명
마우스
:hover
마우스가 올라갈 때 스타일 적용
:active
마우스로 누르고 있는 상황에서 스타일 적용
폼요소
:focus
폼 요소가 키보드나 마우스 클릭으로 포커스를 받을 때 적용
링크
:link
방문하지 않은 링크에 스타일 적용
:visited
방문한 링크에 스타일 적용
블록
:first-letter
블록형 태그 첫글자에 적용, 인라인 태그에는 적용안됨
:first-line
블록형 태크 첫라인에 적용
구조
:nth-child(even)
짝수 번재 모든 자식 태그에 적용
:nth-child(1)
첫 번째 자식 태그에 스타일 적용


nth-of-type : 선택자로 셀렉한 타입의 개수만 순차적으로 센다!!!(중간에 뭐 끼어들어가면 그건 무시)
child 는 형제태그들 중에서 시작이 누군지 중요함// 시작아니면 안나옴 ㅡㅡ