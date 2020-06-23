---
layout: default
title: Box Model
parent: CSS
nav_order: 3
---

# Box Model
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Box Model basic 

### What is Box Model?

5. 박스 모델
html 태그 요소를 하나의 박스로 보고, 박스크기, 박스 배경색, 박스 여백 등 html태그를 박스로 다루는 체계를 뜻함
박스 구성 : margin, border, padding, contents
property : contents = width, height
	   margin = margin-(top, right, bottom, left) 
		ex) margin: 0 auto; 위 아래 여백 0, 좌우 여백 같게 – width 값 설정 필수
		    margin: auto 0; 위 아래 자동, 좌우 여백 0
	   border = border-()-width, border-()-style, border-()-color
		★단축 프로퍼티 border: width style color (뒤에 더 자세하게 작성해놓음)
	   padding = padding-(top, right, bottom, left)
// height: auto는 원래 기본값으로 돌아가라는 의미
고급 테두리 꾸미기
property : border-radius: px px px px;
           border-image:url('이미지url') 모서리 에지;
	   	필수사항 → border: width(0아닌값) style(지정)
		ex) border-image:url('border.png') 30(30픽셀 조각) round(반복이미지)

### CSS Margins
border랑 비슷하게 운용됨
● The auto Value
You can set the margin property to auto to horizontally center the element within its container.

The element will then take up the specified width, and the remaining space will be split equally between the left and right margins.

● The inherit Value
This example lets the left margin of the <p class="ex1"> element be inherited from the parent element (<div>):

	div {
	  border: 1px solid red;
	  margin-left: 100px;
	}

	p.ex1 {
	  margin-left: inherit;
	}

● Margin Collapse
Top and bottom margins of elements are sometimes collapsed into a single margin that is equal to the largest of the two margins.

This does not happen on left and right margins! Only top and bottom margins!
	h1 {
	  margin: 0 0 50px 0;
	}

	h2 {
	  margin: 20px 0 0 0;
	}


### CSS Border Style
The border-style property specifies what kind of border to display.

The following values are allowed:

● 	dotted - Defines a dotted border
● 	dashed - Defines a dashed border
● 	solid - Defines a solid border
● 	double - Defines a double border
● 	groove - Defines a 3D grooved border. The effect depends on the border-color value
● 	ridge - Defines a 3D ridged border. The effect depends on the border-color value
● 	inset - Defines a 3D inset border. The effect depends on the border-color value
● 	outset - Defines a 3D outset border. The effect depends on the border-color value
● 	none - Defines no border
● 	hidden - Defines a hidden border
● 	The border-style property can have from one to four values (for the top border, right border, bottom border, and the left border).

![](border.png)
![](border2.png)

▶ If the border-style property has four values:

		border-style: dotted solid double dashed;
		top border is dotted
		right border is solid
		bottom border is double
		left border is dashed

		If the border-style property has three values:

		border-style: dotted solid double;
		top border is dotted
		right and left borders are solid
		bottom border is double

		If the border-style property has two values:
		border-style: dotted solid;
		top and bottom borders are dotted
		right and left borders are solid
		If the border-style property has one value:

		border-style: dotted;
		all four borders are dotted

	more about this...
	https://www.w3schools.com/css/css_background.asp
    
    
### CSS Padding
The CSS padding properties are used to generate space around an element's content, inside of any defined borders.

	All the padding properties can have the following values:

	a. length - specifies a padding in px, pt, cm, etc.
	b. % - specifies a padding in % of the width of the containing element
	c. inherit - specifies that the padding should be inherited from the parent element

box-sizing: border-box;

box-sizing property. This causes the element to maintain its width; if you increase the padding, the available content space will decrease.


### CSS Outline
border랑 다른것!!  the element's total width and height is not affected by the width of the outline.
An outline is a line that is drawn around elements, OUTSIDE the borders, to make the element "stand out".

![](outline.png)

● outline-style
● outline-color
● outline-width
● outline-offset
CSS Outline Offset
The outline-offset property adds space between an outline and the edge/border of an element. The space between an element and its outline is transparent.
  outline-offset: 15px;

// 단축 프로퍼티 - border와 똑같음

### CSS Height and Width

The height and width properties do not include padding, borders, or margins. It sets the height/width of the area inside the padding, border, and margin of the element.

	CSS height/width Values
● 	auto - This is default. The browser calculates the height and width
● 	length - Defines the height/width in px, cm etc.
● 	% - Defines the height/width in percent of the containing block
● 	initial - Sets the height/width to its default value
● 	inherit - The height/width will be inherited from its parent value

Note: Remember that the height and width properties do not include padding, borders, or margins! They set the height/width of the area inside the padding, border, and margin of the element!

★ Setting max-width (good at small windows)
어떤 요소의 최대 너비와 높이값을 설정하는 속성
max-width: none|length|initial|inherit
	length - px, cm, em 등	
	initial - 초기화
width 속성값을 무효화 시킨다

The max-width can be specified in length values, like px, cm, etc., or in percent (%) of the containing block, or set to none (this is default. Means that there is no maximum width).

The problem with the <div> above occurs when the browser window is smaller than the width of the element (500px). The browser then adds a horizontal scrollbar to the page.

Using max-width instead, in this situation, will improve the browser's handling of small windows.

Tip: Drag the browser window to smaller than 500px wide, to see the difference between the two divs!

  max-width: 500px;
  margin: auto;
