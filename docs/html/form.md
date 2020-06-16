---
layout: default
title: Form 
parent: HTML
nav_order: 6
---

# Form
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Form basic 

### What is form?

**collect user input**

### Form features

* form attribute

    &#9656; action : 웹 서버 응용 프로그램의 url
    
    &#9656; enctype : 인코딩 타입 (데이터를 전송할 때 암호과 방식 지정)
        
    &#9656; name : 폼 이름
    
    &#9656; target : 윈도우 이름 (응용프로그램으로부터 받은 데이터를 출력할 윈도우 이름)
    
    &#9656; method : GET/POST (폼 데이터를 웹 서버에 전송하는 방식, default= get)

    Notes on GET
    {: .label .mt-3}
    <div class="code-example" markdown="1">
	**the submitted form data will be visible in the page address field**

	&#9656; Appends form-data into the URL in name/value pairs
    
	&#9656; The length of a URL is limited (2048 characters)
    
	&#9656; Never use GET to send sensitive data! (will be visible in the URL)
    
	&#9656; Useful for form submissions where a user wants to bookmark the result
    
	&#9656; GET is better for non-secure data, like query strings in Google
    </div>

	Notes on POST
    {: .label .mt-3}
    <div class="code-example" markdown="1">
    **Always use POST if the form data contains sensitive or personal information. 
    
    The POST method does not display the submitted form data in the page address field**
    
	&#9656; POST has no size limitations, and can be used to send large amounts of data.
    
	&#9656; Form submissions with POST cannot be bookmarked
    </div>

### Basic form of form

---

## Form elements

### Form

### input 

**값을 입력받는 요소**

&#9656; 기본형식
```html
<input type="text" title="아이디 입력" />
```
&#9656; 거의 모든 방식에서 method=“post” 와 enctype=“multipart/form-data”>를 씀 name이 없으면 에러가 뜸

* name attribute : Each input field must have a name attribute to be submitted.
    
    > 생략될경우 submit 했을때 값을 받을수가 없음(not be sent at all)

* type attribute : Each input field must have a name attribute to be submitted.

    basic type
    {: .label .mt-3}
    
    | description       | tag                                     | shape                                |
    |:------------------|:----------------------------------------|:-------------------------------------|
    | text(default)     | `<input type="text">`                   | <input type="text">                  |
    | password          | `<input type="password">`               | <input type="password">              |
    | image             | `<input type="image" src="">`           | <input type="image" src="">          |
    | button            | `<input type="button" value="button">`  | <input type="button" value="button"> |
    | checkbox          | `<input type="checkbox">`               | <input type="checkbox">              |
    | radio             | `<input type="radio">`                  | <input type="radio">                 |
    | email             | `<input type="email">`                  | <input type="email">                 |
    | file              | `<input type="file">`                   | <input type="file">                  |
    | submit            | `<input type="submit">`                 | <input type="submit">                |
    | reset             | `<input type="reset">`                  | <input type="reset">                 |
    | search            | `<input type="search">`                 | <input type="search">                |
    | color             | `<input type="color">`                  | <input type="color">                 |
    | hidden            | `<input type="hidden">`                 | <input type="hidden">                |
    | number            | `<input type="number">`                 | <input type="number">                |
    | range             | `<input type="range">`                  | <input type="range">                 |
    | tel               | `<input type="tel">`                    | <input type="tel">                   |
    | time              | `<input type="time">`                   | <input type="time">                  |
    | url               | `<input type="url">`                    | <input type="url">                   |
    | month             | `<input type="month">`                  | <input type="month">                 |
    | week              | `<input type="week">`                   | <input type="week">                  |
    | date              | `<input type="date">`                   | <input type="date">                  |
    | datetime-local    | `<input type="datetime-local">`         | <input type="datetime-local">        |
    
    
    
    ```html
    <input type="button">

    <input type="checkbox">

    <input type="color">

    <input type="date">

    <input type="datetime-local">

    <input type="email">

    <input type="file">

    <input type="hidden">

    <input type="image" src="">

    <input type="month">

    <input type="number">

    <input type="password">

    <input type="radio">

    <input type="range">

    <input type="reset">

    <input type="search">

    <input type="submit">

    <input type="tel">

    <input type="text">

    <input type="time">

    <input type="url">

    <input type="week">
    ```

    새로 생긴것
    {: .label .mt-3}
    | description       | tag                                                         | shape                                                     |
    |:------------------|:------------------------------------------------------------|:----------------------------------------------------------|
    | text(default)     | `<input type="text">`                                       | <input type="text">                                       |
    | password          | `<input type="password">`                                   | <input type="password">                                   |
    | image             | `<input type="image" src="">`                               | <input type="image" src="">                               |
    | button            | `<input type="button" value="button">`                      | <input type="button" value="button">                      |
    | checkbox          | `<input type="checkbox">`                                   | <input type="checkbox">                                   |
    | radio             | `<input type="radio">`                                      | <input type="radio">                                      |
    | email             | `<input type="email">`                                      | <input type="email">                                      |
    | file              | `<input type="file">`                                       | <input type="file">                                       |
    | submit            | `<input type="submit">`                                     | <input type="submit">                                     |
    | reset             | `<input type="reset">`                                      | <input type="reset">                                      |
    | search            | `<input type="search">`                                     | <input type="search">                                     |
    | color             | `<input type="color">`                                      | <input type="color">                                      |
    | hidden            | `<input type="hidden">`                                     | <input type="hidden">                                     |
    | number            | `<input type="number">`                                     | <input type="number">                                     |
    |                   | `<input type="number" name="quantity" min="1" max="5">`     | <input type="number" name="quantity" min="1" max="5">     |
    | range             | `<input type="range">`                                      | <input type="range">                                      |
    | tel               | `<input type="tel">`                                        | <input type="tel">                                        |
    | time              | `<input type="time">`                                       | <input type="time">                                       |
    | url               | `<input type="url">`                                        | <input type="url">                                        |
    | month             | `<input type="month">`                                      | <input type="month">                                      |
    | week              | `<input type="week">`                                       | <input type="week">                                       |
    | date              | `<input type="date">`                                       | <input type="date">                                       |
    |                   | `<input type="date" name="bday" max="1979-12-31">`          | <input type="date" name="bday" max="1979-12-31">          |
    |                   | `<input type="date" name="bday" min="2000-01-02">`          | <input type="date" name="bday" min="2000-01-02">          |
    | datetime-local    | `<input type="datetime-local">`                             | <input type="datetime-local">                             |
    
    
    ```html
    <input type="color">
    
    Enter a date before 1980-01-01:
    <input type="date" name="bday" max="1979-12-31"><br>
    
    Enter a date after 2000-01-01:
    <input type="date" name="bday" min="2000-01-02"><br>
    
    <input type="datetime-local">
    
    <input type="email">
    
    <input type="file"> : file-select field and a "Browse" button for file uploads
    
    <input type="month"> : the user to select a month and year
    <input type="number"> : numeric input field,
    
    You can also set restrictions on what numbers are accepted.
    
    <input type="number" name="quantity" min="1" max="5">
    
    <input type="range">
    
    <input type="search">
    
    <input type="tel">
    
    <input type="time">
    
    <input type="url">
    
    <input type="week">
    ```

* value attribute

    The value attribute specifies the initial value for an input field:
    <input type="text" name="firstname" value="John">

* readonly attribute

    The readonly attribute specifies that the input field is read only (cannot be changed):

* disabled attribute

    A disabled input field is unusable and un-clickable, and its value will not be sent when submitting the form:
    <input type="text" name="firstname" value="John" disabled>

* size attribute

    The maxlength Attribute
    The maxlength attribute does not provide any feedback. If you want to alert the user, you must write JavaScript code.

    [w3schools](https://www.w3schools.com/html/html_form_attributes.asp)

Note:
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
웹 접근성 기준 상, 폼 입력 요소가 있다면 이에 해당하는 **label 요소**를 반드시 가지고 있어야 합니다. 
label은 폼 입력 요소에 무엇을 입력하는 지 명시해 주는 요소. 주로 해당 입력 요소의 id를 연결. 

**만약 label을 넣을만한 공간적인 여유가 없거나 부득이한 경우라면, 해당 폼 입력 요소에 title 속성이라도 넣도록 권장하고 있습니다**
</div>

### select

**select element defines a drop-down list**

```html
<select name="cars">
  <option value="volvo" selected size="3">Volvo</option>
</select>
```

Allow Multiple Selections
{: .label .mt-3}
<div class="code-example" markdown="1">
Use the multiple attribute to allow the user to select more than one value.
Hold down the Ctrl (windows) / Command (Mac) button to select multiple options.
</div>

* optgroup

    **소제목 달기, make it bold**
    
    ```html
    <select>
      <optgroup label="Swedish Cars">
        <option value="volvo">Volvo</option>
        <option value="saab">Saab</option>
      </optgroup>
    <select>
    ```

### textarea

**a multi-line input field**

&#9656; 사이즈를 고정하고 싶으면 resize: none;

### button

**a clickable button**

Note:
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
Always specify the type attribute for the button element. 
Different browsers may use different default types for the button element.
</div>

### fieldset

**Grouping Form Data**

* legend : caption for the fieldset element

### datalist

**pre-defined options for an input element**

&#9656; input type list 속성에 datalist id를 같게 만들면, datalist 하위 option값들이 드롭다운 버튼에 나타난다

<div class="code-example" markdown="1">
    <form action="/action_page.php">
      <input list="browsers">
      <datalist id="browsers">
        <option value="Internet Explorer">
        <option value="Firefox">
        <option value="Chrome">
        <option value="Opera">
        <option value="Safari">
      </datalist>
    </form>
</div>
```html
<form action="/action_page.php">
  <input list="browsers">
  <datalist id="browsers">
    <option value="Internet Explorer">
    <option value="Firefox">
    <option value="Chrome">
    <option value="Opera">
    <option value="Safari">
  </datalist>
</form>
```

### output

represents the **result of a calculation** (like one performed by a script).

<div class="code-example" markdown="1">
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" id="a" value="50">
    +<input type="number" id="b" value="25">
    =<output name="x" for="a b"></output>
</form>    
</div>
```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" id="a" value="50">
    +<input type="number" id="b" value="25">
    =<output name="x" for="a b"></output>
</form>
```

## Form advanced

그냥 데이터만 서버에 전송해야 할때 : input type=“hidden” name=“hide” value=“hey”

