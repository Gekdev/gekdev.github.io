---
layout: default
title: Form 
parent: Elements
grand_parent: HTML
nav_order: 3
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

user input can be sent to a server for processing

### Basic form of form

<div class="code-example" markdown="1">
<form action="/action_page.php">
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" value="John"><br><br>
  <input type="submit" value="Submit">
</form> 
</div>
```html
<form action="/action_page.php">
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" value="John"><br><br>
  <input type="submit" value="Submit">
</form>
```

---

## Form elements

### &#60;form&#62;

**defines a form that is used to collect user input**

* form attributes

    &#9656; action : 웹 서버 응용 프로그램의 url
    
    &#9656; enctype : 인코딩 타입 (데이터를 전송할 때 암호과 방식 지정)
        
    &#9656; name : 폼 이름

    &#9656; novalidate : **specifies that all of the form-data should not be validated when submitted**
    
    ```html
    <form action="/action_page.php" novalidate>
      <label for="email">Enter your email:</label>
      <input type="email" id="email" name="email"><br><br>
      <input type="submit" value="Submit">
    </form>
    ```
    
    &#9656; autocomplete : Specifies if the browser should autocomplete the form (default: on).
    
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
    **Always use POST if the form data contains sensitive or personal information.**
    
    **The POST method does not display the submitted form data in the page address field**
    
	&#9656; POST has no size limitations, and can be used to send large amounts of data.
    
	&#9656; Form submissions with POST cannot be bookmarked
    </div>

### &#60;input&#62; 

**값을 입력받는 요소**

기본형식
```html
<input type="text" title="아이디 입력" />
```
&#8594; 거의 모든 방식에서 method=“post” 와 enctype=“multipart/form-data”>를 씀 (name이 없으면 에러가 뜸)

#### Input Attributes

* name : Each input field must have a name attribute to be submitted.
    
    > **생략될경우 submit 했을때 값을 받을수가 없음(not be sent at all)**

* type : Each input field must have a name attribute to be submitted.

    basic type
    {: .label .mt-3}
    
    | type              | tag                                                         | shape                                                     |
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

    &#8594; reset은 값을 지우는게 아닌 초기값으로 돌아가는것!(value 값에 따라)
    
    &#8594; image는 submit과 동일함
    
    &#9656; 그냥 데이터만 서버에 전송해야 할때 : input type=“hidden” name=“hide” value=“hey”

* value

    **initial value for an input field**
    
    <div class="code-example" markdown="1">
    <input type="text" name="firstname" value="John">
    </div>
    ```html
    <input type="text" name="firstname" value="John">
    ```
    
* readonly 

    **read only (cannot be changed)**
    
    폼에 value가 저장되어 날아감(disabled와 반대)
    
    &#8594; however, a user can tab to it, highlight it, and copy the text from it
    
    <div class="code-example" markdown="1">
    <input type="text" id="fname" name="fname" value="John" readonly>
    </div>
    ```html
    <input type="text" id="fname" name="fname" value="John" readonly>
    ```

* disabled 

    **unusable and un-clickable**
    
    폼에 value가 저장되지 않고 날아감(readonly와 반대)
    
    <div class="code-example" markdown="1">
    <input type="text" name="firstname" value="John" disabled>
    </div>
    ```html
    <input type="text" name="firstname" value="John" disabled>
    ```
* size 
    
    **visible width, in characters, of an input field**

    works with input types : text, search, tel, url, email, and password
    
    <div class="code-example" markdown="1">
    <form>
      <label for="fname">First name:</label><br>
      <input type="text" id="fname" name="fname" size="50"><br>
      <label for="pin">PIN:</label><br>
      <input type="text" id="pin" name="pin" size="4">
    </form>
    </div>
    ```html
    <form>
      <label for="fname">First name:</label><br>
      <input type="text" id="fname" name="fname" size="50"><br>
      <label for="pin">PIN:</label><br>
      <input type="text" id="pin" name="pin" size="4">
    </form>
    ```

* maxlength 

    <div class="code-example" markdown="1">
    <form>
      <label for="fname">First name:</label><br>
      <input type="text" id="fname" name="fname" size="50"><br>
      <label for="pin">PIN:</label><br>
      <input type="text" id="pin" name="pin" maxlength="4" size="4">
    </form>
    </div>
    ```html
    <form>
      <label for="fname">First name:</label><br>
      <input type="text" id="fname" name="fname" size="50"><br>
      <label for="pin">PIN:</label><br>
      <input type="text" id="pin" name="pin" maxlength="4" size="4">
    </form>
    ```
	Note
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    When a maxlength is set, the input field will not accept more than the specified number of characters. However, **this attribute does not provide any feedback.** 
    
    So, if you want to alert the user, you must write JavaScript code.
    </div>

* min and max 

    **specify the minimum and maximum values for an input field**
    
    this attributes is for create a range of legal values
    
    works with input types : number, range, date, datetime-local, month, time and week.
    
    <div class="code-example" markdown="1">
    <form>
      <label for="datemax">Enter a date before 1980-01-01:</label>
      <input type="date" id="datemax" name="datemax" max="1979-12-31">

      <label for="datemin">Enter a date after 2000-01-01:</label>
      <input type="date" id="datemin" name="datemin" min="2000-01-02">

      <label for="quantity">Quantity (between 1 and 5):</label>
      <input type="number" id="quantity" name="quantity" min="1" max="5">
    </form>
    </div>
    ```html
    <form>
      <label for="datemax">Enter a date before 1980-01-01:</label>
      <input type="date" id="datemax" name="datemax" max="1979-12-31">

      <label for="datemin">Enter a date after 2000-01-01:</label>
      <input type="date" id="datemin" name="datemin" min="2000-01-02">

      <label for="quantity">Quantity (between 1 and 5):</label>
      <input type="number" id="quantity" name="quantity" min="1" max="5">
    </form>
    ```
    
* multiple 

    **user is allowed to enter more than one value in an input field**
    
    works with input types : email, and file.
    
    <div class="code-example" markdown="1">
    <form>
      <label for="files">Select files:</label>
      <input type="file" id="files" name="files" multiple>
    </form>
    </div>
    ```html
    <form>
      <label for="files">Select files:</label>
      <input type="file" id="files" name="files" multiple>
    </form>
    ```
    
* pattern 

    **regular expression that the input field's value is checked against, when the form is submitted.**
    
    Use the global `title` attribute to describe the pattern to help the user
    
    works with input types : text, date, search, url, tel, email, and password.
    
    <div class="code-example" markdown="1">
    <form>
      <label for="country_code">Country code:</label>
      <input type="text" id="country_code" name="country_code" pattern="[A-Za-z]{3}" title="Three letter country code">
    </form>
    </div>
    ```html
    <form>
      <label for="country_code">Country code:</label>
      <input type="text" id="country_code" name="country_code"
      pattern="[A-Za-z]{3}" title="Three letter country code">
    </form>
    ```
    
* placeholder 

    **short a hint that describes the expected value of an input field**
    
     short hint is displayed in the input field before the user enters a value
     
     works with input types : text, search, url, tel, email, and password
     
     <div class="code-example" markdown="1">
     <form>
        <label for="phone">Enter a phone number:</label>
        <input type="tel" id="phone" name="phone" placeholder="123-45-678" pattern="[0-9]{3}-[0-9]{2}-[0-9]{3}">
     </form>
     </div>
     ```html
      <form>
        <label for="phone">Enter a phone number:</label>
        <input type="tel" id="phone" name="phone" placeholder="123-45-678" pattern="[0-9]{3}-[0-9]{2}-[0-9]{3}">
     </form>
     ```

* required 

    **input field must be filled out before submitting the form**
    
    works with input types : text, search, url, tel, email, password, date pickers, number, checkbox, radio, and file.
    
    <div class="code-example" markdown="1">
    <form>
      <label for="username">Username:</label>
      <input type="text" id="username" name="username" required>
    </form>
    </div>
    ```html
    <form>
      <label for="username">Username:</label>
      <input type="text" id="username" name="username" required>
    </form>
    ```
    
* step 

    **legal number intervals for an input field**
    
    (Example: if step="3", legal numbers could be -3, 0, 3, 6, etc.)

    Tip: This attribute can be used together with the max and min attributes to create a range of legal values.
    
    works with input types : number, range, date, datetime-local, month, time and week.
    
    <div class="code-example" markdown="1">
    <form>
      <label for="points">Points:</label>
      <input type="number" id="points" name="points" step="3">
    </form>
    </div>
    ```html
    <form>
      <label for="points">Points:</label>
      <input type="number" id="points" name="points" step="3">
    </form>
    ``` 
    
    Note:
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    입력 제한은 완벽하지 않고, 자바스크립트가 잘못된 인풋값을 잡아내는것도 필요함. 완벽하게 잡아내려면 서버에서도 확인해야함.
    </div>
    
* autofocus 

    **로드 후 자동포커스**
    
    ```html
    <input type="text" id="fname" name="fname" autofocus>
    ```
    
    이해가 되지 않는다면 확인! [W3C](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_input_autofocus)
    
* height and width 

    **the height and width of an `<input type="image">` element.**
    
    Note:
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    이미지 인풋을 사용한다면 항상 width와 height값을 설정해야 함. 그래야지 로드될때 이미지 사이즈를 인지하고 레이아웃을 잡음
    
    width, height값을 설정하지 않는다면 브라우저는 크기를 인지하지 못해서 레이아웃이 변경될 수 있음.
    </div>
    
* autocomplete 

    **whether a form or an input field should have autocomplete on or off**
    
    사용자가 값을 입력하면 브라우저가 이전에 입력했던 값을 기반으로 값을 예상해줌
    
    works with input types : text, search, url, tel, email, password, datepickers, range, and color.

    <div class="code-example" markdown="1">
    <form action="/action_page.php" autocomplete="on">
      <label for="fname">First name:</label>
      <input type="text" id="fname" name="fname"><br><br>
      <label for="lname">Last name:</label>
      <input type="text" id="lname" name="lname"><br><br>
      <label for="email">Email:</label>
      <input type="email" id="email" name="email" autocomplete="off"><br><br>
      <input type="submit" value="Submit">
    </form>
    </div>
    ```html
    <form action="/action_page.php" autocomplete="on">
      <label for="fname">First name:</label>
      <input type="text" id="fname" name="fname"><br><br>
      <label for="lname">Last name:</label>
      <input type="text" id="lname" name="lname"><br><br>
      <label for="email">Email:</label>
      <input type="email" id="email" name="email" autocomplete="off"><br><br>
      <input type="submit" value="Submit">
    </form>
    ```

#### Input Form Attributes

* formaction 

    **specifies the URL of the file that will process the input when the form is submitted**
    
    works with input types : submit and image
    
    [W3C Code](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_input_formaction)
    
    ```html
    <form action="/action_page.php">
      <label for="fname">First name:</label>
      <input type="text" id="fname" name="fname"><br><br>
      <label for="lname">Last name:</label>
      <input type="text" id="lname" name="lname"><br><br>
      <input type="submit" value="Submit">
      <input type="submit" formaction="/action_page2.php" value="Submit as Admin">
    </form>
    ```
    
    Note:
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    formaction 속성이 form의 action보다 우선함
    </div>

* formenctype 

    **specifies how the form-data should be encoded when submitted**
    
    only for forms with method="post"
    
    works with input types : submit and image
    
    [W3C Code](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_input_formenctype)
    
    ```html
    <form action="/action_page_binary.asp" method="post">
      <label for="fname">First name:</label>
      <input type="text" id="fname" name="fname"><br><br>
      <input type="submit" value="Submit">
      <input type="submit" formenctype="multipart/form-data"
      value="Submit as Multipart/form-data">
    </form>
    ```
    
    Note:
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    formenctype 속성이 form의 enctype보다 우선함
    </div>
    
* formmethod  

    **HTTP method for sending form-data to the action URL**
    
    form-data can be sent as URL variables (method="get") or as an HTTP post transaction (method="post")
    
    works with input types : submit and image
    
    [W3C Code](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_input_formmethod)
    
    ```html
    <form action="/action_page.php" method="get">
      <label for="fname">First name:</label>
      <input type="text" id="fname" name="fname"><br><br>
      <label for="lname">Last name:</label>
      <input type="text" id="lname" name="lname"><br><br>
      <input type="submit" value="Submit using GET">
      <input type="submit" formmethod="post" value="Submit using POST">
    </form>
    
    <!--A form with two submit buttons. The first sends the form-data with method="get". The second sends the form-data with method="post"-->
    ```
    
    Notes on the "get" method
    {: .label .mt-3}
    <div class="code-example" markdown="1">
    * This method appends the form-data to the URL in name/value pairs

    * This method is useful for form submissions where a user want to bookmark the result

    * There is a limit to how much data you can place in a URL (varies between browsers), therefore, you cannot be sure that all of the form-data will be correctly transferred

    * Never use the "get" method to pass sensitive information! (password or other sensitive information will be visible in the browser's address bar)
    </div>

    Notes on the "post" method
    {: .label .mt-3}
    <div class="code-example" markdown="1">
    * This method sends the form-data as an HTTP post transaction

    * Form submissions with the "post" method cannot be bookmarked

    * The "post" method is more robust and secure than "get", and "post" does not have size limitations
    </div>

    Note:
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    overrides the target attribute of the `<form>` element
    </div>
    
* formtarget   

    **specifies a name or a keyword that indicates where to display the response that is received after submitting the form**
    
    works with input types : submit and image
    
    [W3C Code](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_input_formtarget)
    
    ```html
    <form action="/action_page.php">
      <label for="fname">First name:</label>
      <input type="text" id="fname" name="fname"><br><br>
      <label for="lname">Last name:</label>
      <input type="text" id="lname" name="lname"><br><br>
      <input type="submit" value="Submit">
      <input type="submit" formtarget="_blank" value="Submit to a new window/tab">
    </form>
    ```
    
    Note:
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    overrides the target attribute of the `<form>` element
    </div>
      
* formnovalidate   

    **specifies that an `<input>` element should not be validated when submitted**
    
    works with input types : submit
    
    form의 novalidate와 같음
    
    [W3C Code](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_input_formnovalidate)
    
    ```html
    <form action="/action_page.php">
      <label for="email">Enter your email:</label>
      <input type="email" id="email" name="email"><br><br>
      <input type="submit" value="Submit">
      <input type="submit" formnovalidate="formnovalidate"
      value="Submit without validation">
    </form>
    ```
    
    Note:
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    overrides the target attribute of the `<form>` element
    </div>

### &#60;label&#62;

**defines a label for many form elements**

&#9656; useful for screen-reader users, because the screen-reader will read out loud the label when the user is focused on the input element

&#9656; also help users who have difficulty clicking on very small regions (such as radio buttons or checkboxes)

&#9656; for attribute should be equal to the id attribute of the `<input>` element to bind them together

Note:
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
웹 접근성 기준 상, 폼 입력 요소가 있다면 이에 해당하는 **label 요소**를 반드시 가지고 있어야 합니다. 
label은 폼 입력 요소에 무엇을 입력하는 지 명시해 주는 요소. 주로 해당 입력 요소의 id를 연결. 

**만약 label을 넣을만한 공간적인 여유가 없거나 부득이한 경우라면, 해당 폼 입력 요소에 title 속성이라도 넣도록 권장하고 있습니다**
</div>

### &#60;select&#62;

**select element defines a drop-down list**

<div class="code-example" markdown="1">
<select id="cars" name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select>
</div>
```html
<select id="cars" name="cars">
  <option value="volvo">Volvo</option>
  <option value="saab">Saab</option>
  <option value="fiat">Fiat</option>
  <option value="audi">Audi</option>
</select>
```

* Useful Attributes
    
    &#9656; selected(option attribute)
    
    &#9656; size
    
    &#9656; multiple
    
    Allow Multiple Selections
    {: .label .mt-3}
    <div class="code-example" markdown="1">
    Use the multiple attribute to allow the user to select more than one value.
    Hold down the Ctrl (windows) / Command (Mac) button to select multiple options.
    </div>

* &#60;optgroup&#62;

    **소제목 달기, make it bold**
    
    ```html
    <select>
      <optgroup label="Swedish Cars">
        <option value="volvo">Volvo</option>
        <option value="saab">Saab</option>
      </optgroup>
    <select>
    ```

### &#60;textarea&#62;

**a multi-line input field**

<div class="code-example" markdown="1">
<form action="/action_page.php">
  <textarea name="message" rows="10" cols="30">The cat was playing in the garden.</textarea>
  <br><br>
  <input type="submit">
</form>
</div>
```html
<form action="/action_page.php">
  <textarea name="message" rows="10" cols="30">The cat was playing in the garden.</textarea>
  <br><br>
  <input type="submit">
</form>
```

* Useful Attributes
    
    &#9656; rows : specifies the visible number of lines
    
    &#9656; size : visible width of a text area
    
    &#9656; resize : 사이즈를 고정유무


### &#60;button&#62;

**a clickable button**

<div class="code-example" markdown="1">
<button type="button" onclick="alert('Hello World!')">Click Me!</button>
</div>
```html
<button type="button" onclick="alert('Hello World!')">Click Me!</button>
```

Note:
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
Always specify the type attribute for the button element. 
Different browsers may use different default types for the button element.
</div>

### &#60;fieldset&#62;, &#60;legend&#62;

fieldset : **Grouping Form Data**

legend : caption for the fieldset element

<div class="code-example" markdown="1">
<form action="/action_page.php">
  <fieldset>
    <legend>Personalia:</legend>
    <label for="fname">First name:</label><br>
    <input type="text" id="fname" name="fname" value="John"><br>
    <label for="lname">Last name:</label><br>
    <input type="text" id="lname" name="lname" value="Doe"><br><br>
    <input type="submit" value="Submit">
  </fieldset>
</form>
</div>
```html
<form action="/action_page.php">
  <fieldset>
    <legend>Personalia:</legend>
    <label for="fname">First name:</label><br>
    <input type="text" id="fname" name="fname" value="John"><br>
    <label for="lname">Last name:</label><br>
    <input type="text" id="lname" name="lname" value="Doe"><br><br>
    <input type="submit" value="Submit">
  </fieldset>
</form>
```

### &#60;output&#62;

represents the **result of a calculation** (like one performed by a script).

<div class="code-example" markdown="1">
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" id="a" value="50">
     + <input type="number" id="b" value="25">
     = <output name="x" for="a b"></output>
</form>    
</div>
```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" id="a" value="50">
     + <input type="number" id="b" value="25">
     = <output name="x" for="a b"></output>
</form>
```

### &#60;datalist&#62;

**pre-defined options for an input element**

&#9656; input type list 속성과 datalist id를 같게 만들면, datalist 하위 option값들이 드롭다운으로 나타난다

&#8594; 가이드같은 개념, select같은 속성은 아님!

<div class="code-example" markdown="1">
<form action="/action_page.php" name="browser">
  <input list="browsers">
  <datalist id="browsers">
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
    <option value="Firefox">
    <option value="Chrome">
    <option value="Opera">
    <option value="Safari">
  </datalist>
</form>
```

