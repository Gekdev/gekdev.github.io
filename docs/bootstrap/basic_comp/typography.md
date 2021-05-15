---
layout: default
title: Typography
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 1
---

# Basic BT Typography
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Text/Typography Basic

### Bootstrap's Default Settings

**부트스트랩 기본 CSS는 브라우저 기본값과 약간 다름**

* `<p>`요소에는 계산 된 선 높이의 절반(기본적으로 10px)에 해당하는 아래쪽 여백이 있음

### Bootstrap's Default font 

**부트스트랩 기본 글꼴**

&#9656; helvetica neue , helvetica , arial , sans-serif 계열 글꼴 설정

&#9656; 글꼴의 크기 14px

&#9656; 행간 1.42857443

&#9656; 글자색상 #333

```css
body{
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 14px;
    line-height: 1.42857143;
    color: #333;
    background-color: #fff;
}
```

### Default fonts By Browsers

브라우저에 따른 기본 글꼴

| 구글(크롬)          | 파이어폭스/IE11     | 맥(사파리)             | 맥(크롬)            | 
|:-------------------|:------------------|:----------------------|:-------------------|
| 한글 글꼴(굴림체)    | 한글 글꼴(맑은 고딕) | 한글 글꼴(산돌 고딕 Neo) | 한글 글꼴(애플 고딕) |


### Using Google Font

**@font-face{}나 @import url()**로 구글폰트를 사용할 수 있음

#### @font-face{} 

```css
@font-face{
  font-family:'NanumBarunGothic';
  src:url("../fonts/NanumBarunGothic.eot");
  src:local("☺"),url("../fonts/NanumBarunGothic.woff") format("woff");
}

body { font-family: "Helvetica Neue", Helvetica, Arial,"NanumBarunGothic",  sans-serif; }
```

#### @import url()

```css
@import url(http://fonts.googleapis.com/earlyaccess/nanumgothic.css);

body { font-family: "Helvetica Neue", Helvetica, Arial,'Nanum Gothic', sans-serif; }
```

---

## Text/Typography Elements

### <h1>-<h6>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_heading.html" height="270" width="700" style="border:none;" title="bt heading example"></iframe>
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
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_small.html" height="350" width="700" style="border:none;" title="bt heading example"></iframe>
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
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_abbr.html" height="150" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Abbreviations</h1>
  <p>The abbr element is used to mark up an abbreviation or acronym:</p>
  <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>
</div>
```

#### initialism class

**더 세밀한 점선**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
abbr class="initialism"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_initialism_cl.html" height="150" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948. (normal abbr)</p>      
  <p>The <abbr title="World Health Organization" class="initialism">WHO</abbr> was founded in 1948. (slightly smaller abbr)</p>
</div>
```

### &#60;blockquote&#62;

**인용 문구**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_blockquote.html" height="250" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Blockquotes</h1>
  <p>The blockquote element is used to present content from another source:</p>
  <blockquote>
    <p>For 50 years, WWF has been protecting the future of nature. 
    The world's leading conservation organization, WWF works in 100 countries and is supported by 
    1.2 million members in the United States and close to 5 million globally.</p>
    <footer>From WWF's website</footer>
  </blockquote>
</div>
```

#### blockquote-reverse class

**오른쪽 정렬**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
blockquote class="blockquote-reverse"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_blockquote_rv.html" height="250" width="700" style="border:none;" title="bt heading example"></iframe>
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

---

## Code Elements

### &#60;var&#62;

**변수를 나타냄**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_var.html" height="150" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Code</h2>    
      
  <p>To indicate variables, use the var element:</p>
  <p><var>x</var> = <var>a</var><var>b</var> + <var>y</var></p>

</div>
```

### &#60;code&#62;

**짧은 코드**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_code.html" height="150" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h1>Code Snippets</h1>
  <p>Inline snippets of code should be embedded in the code element:</p>
  <p>The following HTML elements: <code>span</code>, <code>section</code>, and <code>div</code> defines a section in a document.</p>
</div>
```

### &#60;kbd&#62;

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_kbd.html" height="150" width="700" style="border:none;" title="bt heading example"></iframe>
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
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_pre.html" height="230" width="700" style="border:none;" title="bt heading example"></iframe>
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

**스크롤 바 생성**

높이가 350px이 넘어가는 경우 자동으로 스크롤 생성

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
pre class="pre-scrollable"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_pre_sb.html" height="230" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <p>If you add the .pre-scrollable class, the pre element gets a max-height of 350px and provides a y-axis scrollbar:</p>
  <pre class="pre-scrollable">Text in a pre element
  is displayed in a fixed-width
  font, and it preserves
  both      spaces and
  line breaks.</pre>
</div>
```

### &#60;samp&#62;

**컴퓨터 프로그램에서 샘플 출력**

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_samp.html" height="150" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Code</h2>    
      
  <p>To indicate sample output from a computer program, use the samp element:</p>
  <p><samp>This text is output from a computer program....</samp></p>

</div>
```

---

## Text/Typography Class

### Text Align 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
pre class="pre-scrollable"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_align_cl.html" height="280" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p class="text-left">Left-aligned text.</p>
  <p class="text-right">Right-aligned text.</p>      
  <p class="text-center">Center-aligned text.</p>
  <p class="text-justify">Justified text. Justified text. Justified text. Justified text. Justified text. Justified text.</p>      
  <p class="text-nowrap">No wrap text. No wrap text. No wrap text. No wrap text.</p>
  <p><strong>Tip:</strong> Try to resize the browser window to see the behaviour of justify and nowrap.</p>      
</div>
```

### Text Transform

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
pre class="pre-scrollable"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_trans_cl.html" height="150" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p class="text-lowercase">Lowercased text.</p>
  <p class="text-uppercase">Uppercased text.</p>      
  <p class="text-capitalize">Capitalized text.</p>
</div>
```

### Contextual Text Colors

**색상을 통한 의미를 제공하는 데 사용할 수 있는 클래스**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
pre class="pre-scrollable"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_color_cl.html" height="300" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Contextual Colors</h2>
  <p>Use the contextual classes to provide "meaning through colors":</p>
  <p class="text-muted">This text is muted.</p>
  <p class="text-primary">This text is important.</p>
  <p class="text-success">This text indicates success.</p>
  <p class="text-info">This text represents some information.</p>
  <p class="text-warning">This text represents a warning.</p>
  <p class="text-danger">This text represents danger.</p>
</div>
```

### Contextual background colors

**색상을 통한 의미를 제공하는 데 사용할 수 있는 클래스**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
pre class="pre-scrollable"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_background_cl.html" height="280" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Contextual Backgrounds</h2>
  <p>Use the contextual background classes to provide "meaning through colors":</p>
  <p class="bg-primary">This text is important.</p>
  <p class="bg-success">This text indicates success.</p>
  <p class="bg-info">This text represents some information.</p>
  <p class="bg-warning">This text represents a warning.</p>
  <p class="bg-danger">This text represents danger.</p>
</div>
```

### More Typography Classes

#### lead class  

**단락의 첫 문장을 강조** 

&#9656; 16px, 살짝 두꺼운 글꼴

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
pre class="pre-scrollable"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_lead_cl.html" height="200" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p>Use the .lead class to make a paragraph "stand out":</p>
  <p class="lead">This paragraph stands out.</p>
  <p>This is a regular paragraph.</p>
</div>
```

#### small class

**더 작은 텍스트 (상위 텍스트 크기의 85%로 설정됨)**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
pre class="pre-scrollable"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_ty_small_cl.html" height="200" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Typography</h2>
  <p>Use the .small class to make the text smaller:</p>
  <p class="small">This paragraph is smaller.</p>
  <p>This is a regular paragraph.</p>
</div>
```

---

## Complete Bootstrap Typography Reference

For a complete reference of all typography elements/classes, go to our complete [Bootstrap Typography Reference](https://www.w3schools.com/bootstrap/bootstrap_ref_css_text.asp)


