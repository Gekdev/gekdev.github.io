---
layout: default
title: Typography
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 1
---

# Basic Typography
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Text/Typography Basic

### Bootstrap's Default Settings

**부트스트랩 기본 CSS는 브라우저 기본값과 약간 다름**

* 전역 기본 글꼴 크기는 14px이고 줄 높이는 1.428

* <p>요소에는 계산 된 선 높이의 절반(기본적으로 10px)에 해당하는 아래쪽 여백이 있음

---

## Text/Typography Elements

### <h1>-<h6>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_heading.html" height="280" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>h1 Bootstrap heading (36px)</h1>
  <h2>h2 Bootstrap heading (30px)</h2>
  <h3>h3 Bootstrap heading (24px)</h3>
  <h4>h4 Bootstrap heading (18px)</h4>
  <h5>h5 Bootstrap heading (14px)</h5>
  <h6>h6 Bootstrap heading (12px)</h6>
</div>
```

#### &#60;small&#62;

**모든 제목에 더 가벼운 보조 텍스트를 만드는 데 사용**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_small.html" height="340" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Lighter, Secondary Text</h1>
  <p>The small element is used to create a lighter, secondary text in any heading:</p>       
  <h1>h1 heading <small>secondary text</small></h1>
  <h2>h2 heading <small>secondary text</small></h2>
  <h3>h3 heading <small>secondary text</small></h3>
  <h4>h4 heading <small>secondary text</small></h4>
  <h5>h5 heading <small>secondary text</small></h5>
  <h6>h6 heading <small>secondary text</small></h6>
</div>
```

### &#60;mark&#62;

**형광펜**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_mark.html" height="100" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Highlight Text</h1>    
  <p>Use the mark element to <mark>highlight</mark> text.</p>
</div>
```

### &#60;abbr&#62;

**점선 밑줄**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_abbr.html" height="100" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Abbreviations</h1>
  <p>The abbr element is used to mark up an abbreviation or acronym:</p>
  <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>
</div>
```

---

## Code Elements

### &#60;var&#62;

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_abbr.html" height="100" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Abbreviations</h1>
  <p>The abbr element is used to mark up an abbreviation or acronym:</p>
  <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>
</div>
```

### &#60;blockquote&#62;

**인용 문구**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_blockquote.html" height="400" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Blockquotes</h1>
  <p>The blockquote element is used to present content from another source:</p>
  <blockquote>
    <p>For 50 years, WWF has been protecting the future of nature. The world's leading conservation organization, WWF works in 100 countries and is supported by 1.2 million members in the United States and close to 5 million globally.</p>
    <footer>From WWF's website</footer>
  </blockquote>
</div>
```

#### blockquote-reverse class

**오른쪽 정렬**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_blockquote_rv.html" height="400" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Blockquotes</h1>
  <p>To show the quote on the right use the class .blockquote-reverse:</p>
  <blockquote class="blockquote-reverse">
    <p>For 50 years, WWF has been protecting the future of nature. The world's leading conservation organization, WWF works in 100 countries and is supported by 1.2 million members in the United States and close to 5 million globally.</p>
    <footer>From WWF's website</footer>
  </blockquote>
</div>
```

### &#60;kbd&#62;

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_kbd.html" height="400" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Keyboard Inputs</h1>
  <p>To indicate input that is typically entered via the keyboard, use the kbd element:</p>
  <p>Use <kbd>ctrl + p</kbd> to open the Print dialog box.</p>
</div>
```

### &#60;pre&#62;

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_pre.html" height="400" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
    <h1>Multiple Code Lines</h1>
    <p>For multiple lines of code, use the pre element:</p>
    <pre>
    Text in a pre element
    is displayed in a fixed-width
    font, and it preserves
    both      spaces and
    line breaks.
    </pre>
</div>
```

#### pre-scrollable class

&#60;pre class="pre-scrollable"&#62;

### &#60;samp&#62;

### &#60;code&#62;

**짧은 코드**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_code.html" height="300" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Code Snippets</h1>
  <p>Inline snippets of code should be embedded in the code element:</p>
  <p>The following HTML elements: <code>span</code>, <code>section</code>, and <code>div</code> defines a section in a document.</p>
</div>
```

---

## Text/Typography Class

### Contextual Text Colors

### ackground colors

---

## More Typography Classes

.lead	Makes a paragraph stand out	
.small	Indicates smaller text (set to 85% of the size of the parent)	
.text-left	Indicates left-aligned text	
.text-center	Indicates center-aligned text	
.text-right	Indicates right-aligned text	
.text-justify	Indicates justified text	
.text-nowrap	Indicates no wrap text	
.text-lowercase	Indicates lowercased text	
.text-uppercase	Indicates uppercased text	
.text-capitalize	Indicates capitalized text	
.initialism	Displays the text inside an <abbr> element in a slightly smaller font size	
.list-unstyled	Removes the default list-style and left margin on list items (works on both <ul> and <ol>). This class only applies to immediate children list items (to remove the default list-style from any nested lists, apply this class to any nested lists as well)	
.list-inline	Places all list items on a single line	
.dl-horizontal	Lines up the terms (<dt>) and descriptions (<dd>) in <dl> elements side-by-side. Starts off like default <dl>s, but when the browser window expands, it will line up side-by-side	
.pre-scrollable	Makes a <pre> element scrollable


---

## Complete Bootstrap Typography Reference

For a complete reference of all typography elements/classes, go to our complete [Bootstrap Typography Reference](https://www.w3schools.com/bootstrap/bootstrap_ref_css_text.asp)



### [Typography](https://gekdev.github.io/docs/css/bootstrap/typo-sample.html)

* 부트스트랩의 타이포

  1. h1~h6  (36,30,24,18,14,12)의 고정 px 크기를 갖음

        `<small></small>` 태그 지정시  65%(h1~h3) 75%(h4~h6), 축소 색상은 #999

  2. `<p>` 
  
        하단에 자동으로 10px의 마진값 적용

  3. class="lead"  

        **단락의 첫 문장을 강조** 16px, 살짝 두꺼운 글꼴  
  
  4. 문단 정렬

        class="text-left", class="text-center", class="text-right"
  
  6. `<abbr>` 

        **물음표와 원래 텍스트 표현**

        영문 약어는 abbr에 class="initialism" 를 추가하게 되면 단어가 소문자인 경우에도 영문 대문자로 
        변환되면서 글씨 크기는 90%정도로 변환
    
  7. 목록(list)

     &#9656; ul/ol/li : 왼쪽에 20px 하단으로 10px의 여백

     &#9656; .list-unstyled 클래스 선택자를 사용하면 왼쪽 20px 여백이 0으로 바뀜

     직접 위에 페이지 들어가서 보는걸 추천!
     
* 부트스트랩 기본 글꼴

    &#9656; helvetica neue , helvetica , arial , sans-serif 계열 글꼴 설정
  
    &#9656; 글꼴의 크기 14px
  
    &#9656; 행간 1.42857443
  
    &#9656; 글자색상 #333

    ```css
      body {
        font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
        font-size: 14px;
        line-height: 1.42857143;
        color: #333;
        background-color: #fff;
      }
    ```

* 브라우저에 따른 기본글꼴

    | 구글(크롬)          | 파이어폭스/IE11     | 맥(사파리)             | 맥(크롬)            | 
    |:-------------------|:------------------|:----------------------|:-------------------|
    | 한글 글꼴(굴림체)    | 한글 글꼴(맑은 고딕) | 한글 글꼴(산돌 고딕 Neo) | 한글 글꼴(애플 고딕) |


* 구글 폰트 사용

    @font-face{}
    
    ```css
    @font-face{
      font-family:'NanumBarunGothic';
      src:url("../fonts/NanumBarunGothic.eot");
      src:local("☺"),url("../fonts/NanumBarunGothic.woff") format("woff");
    }

    body { font-family: "Helvetica Neue", Helvetica, Arial,"NanumBarunGothic",  sans-serif; }
    ```
    
    or 
    
    ```css
    @import url(http://fonts.googleapis.com/earlyaccess/nanumgothic.css);

    body { font-family: "Helvetica Neue", Helvetica, Arial,'Nanum Gothic', sans-serif; }
    ```

### [Code](https://gekdev.github.io/docs/css/bootstrap/code-sample.html)

* 간단한 코드 표시

    `code` 태그 사용

* 행일 길 경우 
    
    `pre` 태그 사용
    
    `<pre class="pre-scrollable"></pre>`를 사용하면, 높이가 350px이 넘어가는 경우 자동으로 스크롤 생성