---
layout: default
title: Output
parent: Basic
grand_parent: JavaScript
nav_order: 2
---

# JavaScript Output
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Display Possibilities

대표적으로 다음 4가지의 방법으로 데이터를 보일 수 있음

### document.write

**HTML output, For testing purposes**

Using document.write() after an HTML document is loaded, will delete all existing HTML -> 사용하지 않는게 좋음

document.writeIn(“”)도 비슷함
    
### innerHTML

**HTML element**

document.getElementById('').innerHTML ... -> 가장 흔한 방법

★ getElementById를 사용하기 때문에 순서가 중요함 (아이디를 알기 전에 스크립트를 읽어버리면 실행되지 않음)

### window.alert()

**alert box to display data**

window object is the global scope object 

&#9656; 변수, 속성이나 메소드들이 기본적으로 window 객체에 속해서 따로 쓰지 않아도 됨

### console.log()

**browser console, For debugging purposes**

window.print()
{: .label .mt-2}
<div class="code-example" markdown="1">
오직 **window.print()로만 브라우저에서 메소드를 호출해 현재 창을 인쇄**할 수 있음

자바스크립트는 프린트 객체나 프린트 메소드가 따로 없어서 출력 장치에 접근할 수 없음
</div>

### Dialog 

사용자 입력 및 메시지 출력(3가지)

* prompt dialog
    
    **신속한 대화** 
    
    Syntax
    {: .label}
    <div class="code-example" markdown="1">
    prompt(“메시지”, “디폴트 입력값”-생략가능)
    </div>
    
    &#9656; 아무것도 안하면 “”리턴 / 강제로 닫으면 null 리턴
    
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
		
* confirm

    **확인, 취소(OKAY, CANCEL)를 가진 다이얼로그 출력**
    
    Syntax
    {: .label}
    <div class="code-example" markdown="1">
    confirm(“메시지”)
    </div>
    
    ```js
    var ret = confirm(‘전송할까요?’)
    if(ret == true){
        //okay 버튼을 누른 경우
    }else{
        //cancel버튼을 누른 경우
    }
    ```
    
* alert

    **단순 메시지 전달**
    
    Syntax
    {: .label}
    <div class="code-example" markdown="1">
    alert(“메시지”)
    </div>

