---
layout: default
title: Basic
parent: CSS
nav_order: 2
---

# CSS Basic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Syntax Basic

### Syntax 

선택자와 선택자를 정의하는 정의블록(속성:값)의 일렬

![](https://gekdev.github.io/assets/images/selector.gif){: .my-1 }

* selector : **선택자** 

    선택자는 스타일 시트의 이름이나 규칙, 같은 이름의 모든 html태그에 스타일 시트가 적용되게 함

* property: **속성** 

    약 200개
    
---

## Comments

### Comment Basic

**주석**

&#9656; 여러줄도 가능

```html
/* This is a single-line comment */

/* This is
a multi-line
comment */
```

---

## Links

### Styling Links

* External CSS

    **&#60;link&#62; tag**

    &#9656; style sheet을 별도로 작성해서 추가하는 방법

    &#9656; 여러번 사용해 다양한 CSS파일을 불러올 수 있음

    &#9656; CSS파일에는 &#60;style&#62; tag 없이 저장해야함

    ```html
    <head>
        <link href="주소/A.css" type="text/css" rel="stylesheet">  
    </head>
    ```
        
    * href : 주소/A.css파일을 불러올 것을 지시

    * type : 불러오는 파일이 CSS언어로 작성된 파일임을 알려줌

    * rel : 불러오는 파일이 stylesheet라는걸 알려줌

* Internal CSS

    * &#60;style&#62;&#60;/style&#62; 태그에 스타일 시트 작성

        &#9656; 반드시 &#60;head&#62; 태그 안에 작성해야함

        &#9656; 여러번 작성 가능, 합쳐 적용됨
        
        &#9656; &#60;style&#62;에 작성된 스타일 시트는 웹 페이지 전체에서 적용됨

    * @import

        **불러오기**

        &#8594; 여러번 사용해 다양한 CSS파일을 불러올 수 있음

        ```html
        <style>
            @import url('A.css');
        </style>	
        ```

* Inline CSS

    **style attribute**

    &#9656; 각 태그(요소)별로 스타일 지정
    
    &#9656; 해당 태그에만 스타일 적용됨    
        
### Cascading Order

* 스타일 우선순위
    
    1. Inline style (inside an HTML element)
    
    2. internal style sheets (in the head section)
    
    3. External file 
    
    4. Browser default

&#8594; 스타일은 부모로부터 상속된다

---

## Colors

### Color Values

* RGB Value 
    
    **rgb(red, green, blue)**

* RGBA Value 

    **rgba(red, green, blue, alpha)**
    
    &#9656; alpha : 0.0 (fully transparent) and 1.0 (not transparent at all)

* HEX Value

    **#rrggbb**
    
* HSL Value 

    **hsl(hue, saturation, lightness)**
    
    &#9656; Hue : 0-360
    
    &#9656; Saturation : 0~100%
    
    &#9656; Lightness : 0~100%
    
* HSLA Value 

    **hsla(hue, saturation, lightness, alpha)**
    
    &#9656; alpha : 0.0 (fully transparent) and 1.0 (not transparent at all)

