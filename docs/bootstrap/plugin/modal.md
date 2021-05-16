---
layout: default
title: Modal
parent: Plugin
grand_parent: Bootstrap
nav_order: 2
---

# Plugin Modal
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Modal

### How Modal works

```html
<!--[1]-->
<!-- Trigger the modal with a button -->
<button type="button" class="btn btn-info btn-lg" data-toggle="modal" data-target="#myModal">Open Modal</button>

<!-- Modal -->
<div id="myModal" class="modal fade" role="dialog">
  <div class="modal-dialog">

    <!-- Modal content-->
    <div class="modal-content">
      <div class="modal-header">
        <button type="button" class="close" data-dismiss="modal">&times;</button>
        <h4 class="modal-title">Modal Header</h4>
      </div>
      <div class="modal-body">
        <p>Some text in the modal.</p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
      </div>
    </div>

  </div>
</div>
```

1. Trigger

    **모달 창을 가져오려면 button 이나 a태그를 사용해야 함**

    * data-toggle="modal" : 모달창을 열기
    
    * data-target="#myModal" : 모달의 ID를 가리킴    
    
2. Modal

    **모달의 상위객체는 모달("myModal")을 트리거 하는데 사용되는 데이터 대상 특성의 값과 동일한 ID가 있어야 함**
    
    * class="modal" : div내용을 모달로 식별하고 초점을 맞춤
    
    * class="fade" : 모달 안과 밖이 희미해지는 전환 효과를 추가 (필요 없으면 제거 가능)

    * role="dialog" : screen readers를 사용하는 사람들의 접근성을 향상시킴
    
    * class="modal-dialog" : 모달의 적절한 폭과 여백을 설정
    
3. Modal content

    **class="modal-content라고 선언된 div는 경계선, 배경색 등을 스타일링 함, 안에는 헤더 바디, 푸터가 들어올 수 있음**
    
    * class="modal-header" : 모달의 헤더에 대한 스타일을 정의하는 데 사용
        
        * data-dismiss="modal" : 버튼 객체를 클릭시 모달을 닫음
        
        * class= "close" : 버튼에 닫기 버튼을 만들어줌
    
        * class= "modal-title" : 적절한 선 높이를 사용하여 머리글을 스타일링
    
    * class="modal-body" : 모달의 바디 스타일을 정의하는 데 사용, 여기에 문단, 이미지, 비디오 등의 HTML 마크업을 추가할 수 있음
    
    * class="modal-footer" : 모달의 푸터 스타일을 정의하는 데 사용, 기본으로 오른쪽 정렬
    
### Modal Size

모달 크기를 작게나 크게 할 수 있음 (기본으로는 중간사이즈)

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//작은 모달

div class="modal-dialog modal-sm"

//큰 모달

div class="modal-dialog modal-lg"
</div>

### Modal Basic Example

<div class="container">
  <h2>Modal Basic</h2>
  <!-- Trigger the modal with a button -->
  <button type="button" class="btn btn-info btn-lg" data-toggle="modal" data-target="#myModal">Open Modal</button>

  <!-- Modal -->
  <div class="modal fade" id="myModal" role="dialog">
    <div class="modal-dialog">
    
      <!-- Modal content-->
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Modal Header</h4>
        </div>
        <div class="modal-body">
          <p>Some text in the modal.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
      
    </div>
  </div>
  <hr>
  
  <h2>Small Modal</h2>
  <!-- Trigger the modal with a button -->
  <button type="button" class="btn btn-info btn-lg" data-toggle="modal" data-target="#myModa2">Open Small Modal</button>

  <!-- Modal -->
  <div class="modal fade" id="myModa2" role="dialog">
    <div class="modal-dialog modal-sm">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Modal Header</h4>
        </div>
        <div class="modal-body">
          <p>This is a small modal.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
  <hr>
  
   <h2>Large Modal</h2>
  <!-- Trigger the modal with a button -->
  <button type="button" class="btn btn-info btn-lg" data-toggle="modal" data-target="#myModa3">Open Large Modal</button>

  <!-- Modal -->
  <div class="modal fade" id="myModa3" role="dialog">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Modal Header</h4>
        </div>
        <div class="modal-body">
          <p>This is a large modal.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
</div>
<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_modal.html" height="400" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Modal Basic</h2>
  <!-- Trigger the modal with a button -->
  <button type="button" class="btn btn-info btn-lg" data-toggle="modal" data-target="#myModal">Open Modal</button>

  <!-- Modal -->
  <div class="modal fade" id="myModal" role="dialog">
    <div class="modal-dialog">
    
      <!-- Modal content-->
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Modal Header</h4>
        </div>
        <div class="modal-body">
          <p>Some text in the modal.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
      
    </div>
  </div>
  <hr>
  
  <h2>Small Modal</h2>
  <!-- Trigger the modal with a button -->
  <button type="button" class="btn btn-info btn-lg" data-toggle="modal" data-target="#myModa2">Open Small Modal</button>

  <!-- Modal -->
  <div class="modal fade" id="myModa2" role="dialog">
    <div class="modal-dialog modal-sm">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Modal Header</h4>
        </div>
        <div class="modal-body">
          <p>This is a small modal.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
  <hr>
  
   <h2>Large Modal</h2>
  <!-- Trigger the modal with a button -->
  <button type="button" class="btn btn-info btn-lg" data-toggle="modal" data-target="#myModa3">Open Large Modal</button>

  <!-- Modal -->
  <div class="modal fade" id="myModa3" role="dialog">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Modal Header</h4>
        </div>
        <div class="modal-body">
          <p>This is a large modal.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
</div>
```

---

## Complete Bootstrap Modal Reference

For a complete reference of all modal options, methods and events, go to our [Bootstrap JS Modal Reference](https://www.w3schools.com/bootstrap/bootstrap_ref_js_modal.asp)
