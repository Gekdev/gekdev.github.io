---
layout: default
title: Form & Input
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 6
---

# Basic Form & Input
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


### [Form 형태](https://gekdev.github.io/docs/css/bootstrap/form-sample.html)

* role="form"

    role값은 리더기가 읽어준다(접근성)

* class="form-control"

    넓이가 100%, 높이가 34px, 패딩 상하 6px 좌우 12px, border-radius:4px 적용
    
* class="form-group"

    하단에 15px의 마진이 생김

* 인라인 폼

    브라우져 너비가 커지면 한 라인으로 구성
    
    `<form role="form" class="form-inline"></form>`
  
* class="sr-only" 

    라벨을 화면에서 안보이게 할때 적용
    
    `<label for="Name" class="sr-only">이름</label>`

* class="form-horizontal" 
    
    라벨 오른쪽에 폼요소들을 배치
 
### [Form 형식](https://gekdev.github.io/docs/css/bootstrap/form-sample-2.html)


* textarea는 rows 값만 적용

    너비는 100%
 
    `<textarea  rows="5" class="form-control"></textarea>`


* class="checkbox-inline"

    인라인 체크 박스


* class="radio-inline"

    인라인 라디오

 
* p class="form-control-static"

    폼에 텍스트를 삽입 하기 위해

    form-control-static을 적용하지 않을 경우 텍스트가 label 부분과의 정렬이 틀어짐
  
    패딩 7px, 마진바텀 0px 
   
    `<p class="form-control-static">email@example.com</p>`

* disabled 

    비활성화 상태

  `<input type="text" class="form-control" disabled placeholder="이 부분은 disabled 상태입니다.">
  <fieldset disabled> ...  </fieldset>`

* input에 다양한 색 지정 클래스 선택자

  1. Input값이 성공적일(문제없을) 경우
  
     `<label class="control-label" for="inputSuccess">Input값이 성공적일(문제없을) 경우</label>`
  
  2. Input 값에 문제가 있어 경고를 내보낼 경우
  
     `<input type="text" class="form-control" id="inputWarning">`
     
  3. Input값에 에러가 있을 때
  
     `<input type="text" class="form-control" id="inputError">`

* input 크기 제어

    input-lg, 기본값, input-sm
    
    `<input type="text" class="form-control input-lg" placeholder="input-lg">`
    
    `<input type="text" class="form-control input-sm" placeholder="input-sm">`

* 그리드 시스템을 이용해서 컬럼 크기 조절

  `<div>` 태그로 감싼 후 클래스 선택자를 사용해서 처리

    ```html
    <div class="row">
          <div class="col-sm-2 col-lg-2">
            <input type="text" class="form-control" placeholder="">
          </div>
          <div class="col-sm-3  col-lg-3">
            <input type="text" class="form-control" placeholder="">
          </div>
          <div class="col-sm-4  col-lg-4">
            <input type="text" class="form-control" placeholder="">
          </div>
     </div> 
    ```

* input 부분에 대한 도움말

   `<span class="help-block">반드시 010-1234-5678 과 같은 형태로 입력해 주세요. </span>`
   