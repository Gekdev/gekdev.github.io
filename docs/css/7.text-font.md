---
layout: default
title: Text & Font
parent: CSS
nav_order: 7
---

# CSS Text & Font
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Text

### Text Color

* color name : red

* HEX value : #ff0000

* RGB value : rgb(255,0,0)

### Text Alignment

* text-align 

    **horizontal alignment of a text**

    &#9656; value : left, right, center, justify

    ```css
    img.top {
      text-align: top;
    }
    ```
    
* vertical-align

    **vertical alignment of a text**

    &#9656; value : top, middle, bottom
    
    ```css
    img.top {
      vertical-align: top;
    }
    ```

### Text Direction

기본적으로 왼쪽으로 오른쪽으로 진행됨

* direction:rtl 

    **right-to-left (like japanese)**

    ```css
    direction: rtl;
    unicode-bidi: bidi-override;
    ```

### Text Decoration

* text-decoration

    **set or remove decorations from text**

    &#9656; value : none, overline, line-through, underline

    <div class="code-example" markdown="1">
    <p style="text-decoration: overline">
        This is a rather unusual glossary
    </p>
    </div>
    ```html
    <p style="text-decoration: overline">
        This is a rather unusual glossary
    </p>
    ```

### Text Transformation

* text-transform

    **uppercase and lowercase letters**

    &#9656; value : uppercase, lowercase, capitalize

### Text Spacing

* text-indent

    **indentation of the first line**
    
    &#9656; px이나 % 사용
    
    ```css
    p {
      text-indent: 50px;
    }
    ```

* letter-spacing

    **space between the characters in a text**

    ```css
    h1 {
      letter-spacing: 3px;
    }
    ```
    
* line-height

    **specify the space between lines**
    
    ```css
    p.small {
      line-height: 0.8;
    }
    ```

* word-spacing

    **space between the words in a text**

    ```css
    h1 {
      word-spacing: 10px;
    }
    ```

* white-space

    **how white-space inside an element is handled**

    ```css
    p {
      white-space: nowrap;
    }

    /* 문장이 길 경우 줄바꿈이 되지않고 가로 스크롤이 생기면서 한문장으로 나타남*/
    ```

### Text Shadow

* text-shadow

    Syntax
    {: .label mt-2}
    <div class="code-example" markdown="1">
    text-shadow: X Y Blur(optional) Color(optional);
    </div>
    
    <div class="code-example" markdown="1">
    <div style="text-shadow: 3px 3px">drop shadow</div>
    <div style="text-shadow: 3px 3px red">color shadow</div>
    <div style="text-shadow: 3px 3px 5px skyblue">blur shadow</div>
    <div style="text-shadow: 0px 0px 3px red">glow shadow</div>
    <div style="text-shadow: 0px 0px 3px darkblue; color: white">wordart effect</div>
    <div style="text-shadow: 2px 2px 4px black; color: white">3d effect</div>
    <div style="text-shadow: 2px 2px 2px black, 0px 0px 25px blue, 0px 0px 5px darkblue;
            color:yellow">multiple shadow effect</div>
    </div>
    ```css
    <div style="text-shadow: 3px 3px">drop shadow</div>
    <div style="text-shadow: 3px 3px red">color shadow</div>
    <div style="text-shadow: 3px 3px 5px skyblue">blur shadow</div>
    <div style="text-shadow: 0px 0px 3px red">glow shadow</div>
    <div style="text-shadow: 0px 0px 3px darkblue; color: white">wordart effect</div>
    <div style="text-shadow: 2px 2px 4px black; color: white">3d effect</div>
    <div style="text-shadow: 2px 2px 2px black, 0px 0px 25px blue, 0px 0px 5px darkblue;
            color:yellow">multiple shadow effect</div>
    ```
    
### Text Effects

* text-overflow
    
    **overflowed content that is not displayed should be signaled to the user**
    
    * clip : 짤려서 보이지 않게
    
    ![](https://gekdev.github.io/assets/images/to1.JPG)
    
    * ellipsis : 짤려서 ...로 표시
    
    ![](https://gekdev.github.io/assets/images/to2.JPG)

    ```css
    p.test2 {
          overflow: hidden;
           text-overflow: clip;
        }    

    p.test2 {
      overflow: hidden;
      text-overflow: ellipsis;
    }
    ```

* word-wrap

    **긴 단어 자를건지 말건지**
    
    &#9656; break-word하면 잘림
    
    ```css
    p {
      word-wrap: break-word;
    }
    ```
    
* word-break

    **다음줄로 넘어갈때 걸리는 단어를 언제 자를건지**
    
    &#9656; keep-all은 자르지 않는것, break-all은 모두 자르는것
    
    ```css
    p.test1 {
      word-break: keep-all;
    }

    p.test2 {
      word-break: break-all;
    }
    ```

* writing-mode

    **가로로 쓸건지 세로로 쓸건지**
    
    &#9656; horizontal : 가로, vertical : 세로
    
    &#9656; tb : top to bottom , rl : right to left로 방향을 정할 수 있음
    
    ```css
    writing-mode: horizontal-tb;

    writing-mode: vertical-rl;
    ```
    
    <span class="fs-2">
    [W3C Example](https://www.w3schools.com/css/tryit.asp?filename=trycss3_writing-mode){: .btn .btn-outline }
    </span>
    
---

## Font

### Serif and Sans-serif

셰리프 = 뾰족한 꾸밈

&#8594; 산세리프가 세리프체보다 스크린에서 가독성이 좋다

![](https://www.w3schools.com/css/serif.gif)

### Font Family

* font family names

    &#9656; generic family : a group of font families with a similar look

    &#9656; font family : a specific font family

    | Generic family	  | Font family	                  | Description                                                                              |
    |:--------------------|:------------------------------|:-----------------------------------------------------------------------------------------|
    | Serif               | Times New Roman,  Georgia     | Serif fonts have small lines at the ends on some characters                              |
    | Sans-serif	      | Arial, Verdana                | "Sans" means without - these fonts do not have the lines at the ends of characters       |
    | Monospace           | Courier New, Lucida Console   | All monospace characters have the same width                                             |

* fallback 시스템

    여러개 폰트를 지정해놓고 지원 정도에 따라 출력하는 폰트를 다르게 할 수 있음

    따라서 내가 원하는 폰트로 시작하고, 공용으로 사용하는 폰트를 제일 마지막으로 지정해준다

    ```css
    .serif {
      font-family: "Times New Roman", Times, serif;
    }

    .sansserif {
      font-family: Arial, Helvetica, sans-serif;
    }

    .monospace {
      font-family: "Lucida Console", Courier, monospace;
    }
    ```

* @font-face

    가지고 있는 폰트 사용할때 사용
    
    ```css
    @font-face {
      font-family: myFirstFont;
      src: url(sansation_light.woff);
    }
    ```

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
If the name of a font family is more than one word, it must be in quotation marks, like: "Times New Roman"
</div>

### Font Style

* font-style

    **specify italic text**
    
    &#9656; value : normal, italic, oblique(leaning)

    !Difference with italic and oblique
    {: .label .label-yellow .mt-2}
    <div class="code-example" markdown="1">
    oblique is very similar to italic, but less supported
    </div>

* font-weight

    **weight of a font**
    
    &#9656; value : lighter, light, normal, bold, bolder, 100~900

* font-variant

    **whether or not a text should be displayed in a small-caps font**
    
    &#9656; value : normal, small-caps
    
    small-caps : 소문자로 씌여진 영어가 대문자로 보이지만, 원래 대문자크기보다는 작게보임
    
    <div class="code-example" markdown="1">
    ![](https://gekdev.github.io/assets/images/small-caps.JPG)
    </div>

### Font Size

**글자크기 설정은 웹 디자인에서 매우 중요한 요소**

&#9656; 하지만 문단을 제목처럼 만들기 위해 설정하면 안됨

&#9656; 아무것도 설정하지 않은 기본폰트 사이즈 16px = 1em

&#9656; 절대 크기 : 지정된 크기로 설정, 접근성에 나쁨, 실제 크기를 알때 유용

&#9656; 상대 크기 : 주변 요소를 기준으로 설정, 사용자가 브라우저에서 텍스트 크기를 변경 가능

* Set Font Size With Pixels

    full control over the text size

* Set Font Size With Em
    
    사용자의 텍스트 조정을 위해서 많이 사용함
    
    Recommended by the W3C
    
    formula: pixels/16=em (1em = 16px)
        
    <span class="fs-2">
    [변환사이트](http://pxtoem.com/){: .btn .btn-outline }
    </span>
    
    !Warning
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    오래된 브라우저에서는 폰트 크기를 지정된 크기로 보여주지 않음.
    
    해결방법 : Combination of Percent and Em
    
    body의 font-size: 100%; 후 자손들을 em 사용하면 끝!
    </div>

* Responsive Font Size With Vw

    **viewport width**
    
    &#9656; Viewport is the browser window size. 1vw = 1% of viewport width. If the viewport is 50cm wide, 1vw is 0.5cm.

    <div class="code-example" markdown="1">
    <h1 style="font-size:10vw;">Responsive Text</h1>
    <p style="font-size:5vw;">Resize the browser window to see how the text size scales.</p>
    </div>
    ```html
    <h1 style="font-size:10vw;">Responsive Text</h1>
    <p style="font-size:5vw;">Resize the browser window to see how the text size scales.</p>
    ```

Shorthand Font Property
{: .label .label-blue .mt-3}
<div class="code-example" markdown="1">
1. font-style

2. font-variant

3. font-weight

4. font-size/line-height

5. font-family
</div>
```css
example)

font: italic small-caps bold 12px/30px Georgia, serif;
```

### Web Fonts

* [Google Fonts API](https://fonts.google.com/) 

    원하는 폰트를 다운로드 받거나 embed 할 수 있음

    사용방법은 홈페이지에 나와있음
