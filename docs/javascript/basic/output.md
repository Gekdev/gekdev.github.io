---
layout: default
title: Output
parent: Basic
grand_parent: JavaScript
nav_order: 6
---

# JavaScript Output
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Showing Display Possibilities

대표적으로 다음 4가지의 방법으로 데이터를 보일 수 있음

### document.write

**테스트 용**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
document.write("내용");

&#9656; document.writeIn("내용")도 비슷함
</div>

&#9656; HTML 문서가로드 된 후 document.write ()를 사용하면 기존의 모든 HTML이 삭제 

&#8594; 사용하지 않는게 좋음

### innerHTML

**HTML 내용 변경**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
document.getElementById("").innerHTML = "";
</div>

&#9656; 가장 흔한 방법

★ getElementById를 사용하기 때문에 순서가 중요함 (아이디를 알기 전에 스크립트를 읽어버리면 실행되지 않음)

&#9656; `innerTEXT`를 사용하게 되면 뒤 ""에 따라나오는 내용 전체를 텍스트로 읽어버림

innerhtml와 innertext의 차이점
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
document.getElementById("").innerHTML = "<h1>HELLO JAVASCRIPT!</h1>";

결과값 : HELLO JAVASCRIPT!

document.getElementById("").innerTEXT = "<h1>HELLO JAVASCRIPT!</h1>";

결과값 : &#60;h1&#62; HELLO JAVASCRIPT! &#60;h1&#62;
</div>

### window.alert()

**데이터를 표시하는 경고 상자**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
alert("HELLO JAVASCRIPT!")

window.alert("HELLO JAVASCRIPT!") 

&#8594; 코드를 풀어서 쓴 모습
</div>

&#9656; window object 는 전역범위 개체(global scope object)라서 변수, 속성이나 메소드들이 기본적으로 window 객체에 속해 따로 window. 라고 쓰지 않아도 됨

### console.log()

**브라우저 콘솔, 디버깅 목적**

window.print()
{: .label .mt-2}
<div class="code-example" markdown="1">
오직 **window.print()로만 브라우저에서 메소드를 호출해 현재 창을 인쇄**할 수 있음

&#8594; 자바스크립트는 프린트 객체나 프린트 메소드가 따로 없어서 출력 장치에 접근할 수 없음
</div>

---

## Getting User Input dialog

사용자 입력방법

### prompt 

**사용자에게 윈도우 창을 띄워 데이터를 입력받을 수 있는 함수, 다이얼로그 출력** 

Syntax
{: .label}
<div class="code-example" markdown="1">
prompt(“메시지”, “디폴트 입력값”-생략가능)
</div>

&#9656; 아무것도 안하면 “”리턴 / 강제로 닫으면 null 리턴

사용예제
{: .label .label-purple .mt-2}
```js
var ret = prompt(“hello”,“hi”)
if(ret == null){
    //강제로 닫은 경우
}else if(ret == “”){
    //문자열 입력 없이 확인 버튼을 누른 경우
}else{
    //사용자가 입력한 문자열
}
```

### confirm

**확인, 취소(OKAY, CANCEL)를 가진 함수,  다이얼로그 출력**

Syntax
{: .label}
<div class="code-example" markdown="1">
confirm(“메시지”)
</div>

사용예제
{: .label .label-purple .mt-2}
```js
var ret = confirm(‘전송할까요?’)
if(ret == true){
    //okay 버튼을 누른 경우
}else{
    //cancel버튼을 누른 경우
}
```

