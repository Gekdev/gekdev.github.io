---
layout: default
title: Popover
parent: Plugin
grand_parent: Bootstrap
nav_order: 4
---

# Plugin Popover
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Popover Plugin

**사용자가 요소를 클릭 할 때 나타나는 팝업 상자**

툴팁과 비슷하지만 차이점은 Popover에 더 많은 컨텐츠를 포함할 수 있음

### How To Create a Popover

**data-toggle="popover" 속성을 추가, title에 헤더 텍스트를 지정, data-content에 팝오버 몸 안에 표시해야 할 텍스트 지정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1"> 
&#60;a href="#" data-toggle="popover" title="Popover Header!" &#62;Toggle popover&#60;/a&#62;
</div>

★ 팝오버는 jQuery로 초기화 되어야 함
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1"> 
특정한 요소를 선택해서 popover 메소드를 호출해야 함

아래 코드는 문서의 모든 popover를 활성화
</div>
```html
<script>
$(document).ready(function(){
  $('[data-toggle="popover"]').popover();
});
</script>
```

### Positioning Popovers

&#9656; 팝오버는 기본적으로 요소 오른쪽으로 표시됨

&#9656; data-place 속성을 통해 툴팁 위치를 바꿀 수 있음

&#9656; auto 속성을 앞에 추가하면 가능한 그 위치로 보여지게 함

&#8594; ex) auto left : 가능한 왼쪽, 불가능하면 오른쪽으로 보여줌

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* data-placement="top"

* data-placement="bottom"

* data-placement="left"

* data-placement="right"

* data-placement="auto ..."
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_po_place.html" height="200" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h3>Popover Example</h3>
  <ul class="list-inline">
    <li><a href="#" title="Header" data-toggle="popover" data-placement="top" data-content="Content">Top</a></li>
    <li><a href="#" title="Header" data-toggle="popover" data-placement="bottom" data-content="Content">Bottom</a></li>
    <li><a href="#" title="Header" data-toggle="popover" data-placement="left" data-content="Content">Left</a></li>
    <li><a href="#" title="Header" data-toggle="popover" data-placement="right" data-content="Content">Right</a></li>
  </ul>
</div>

<script>
$(document).ready(function(){
    $('[data-toggle="popover"]').popover();   
});
</script>
```

### Closing Popovers

기본적으로 요소를 다시 클릭하면 팝 오버가 닫히지만, data-trigger="focus"를 사용하면 요소 외부를 클릭 할 때 팝 오버를 닫게 할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
data-trigger="focus"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_po_focus.html" height="150" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h3>Popover Example</h3>
    <a href="#" title="Dismissible popover" data-toggle="popover" data-trigger="focus" data-content="Click anywhere in the document to close this popover">Click me</a>
</div>

<script>
$(document).ready(function(){
    $('[data-toggle="popover"]').popover();   
});
</script>
```

### Hovering Popovers

요소 위로 마우스 포인터를 이동할 때 팝 오버가 표시되도록 하기

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
data-trigger="hover"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_po_hover.html" height="200" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h3>Popover Example</h3>
  <a href="#" title="Header" data-toggle="popover" data-content="Some content">Click Me</a><br>
  <a href="#" title="Header" data-toggle="popover" data-trigger="hover" data-content="Some content">Hover over me</a>
</div>

<script>
$(document).ready(function(){
    $('[data-toggle="popover"]').popover();   
});
</script>
```

---

## Complete Bootstrap Popover Reference

For a complete reference of all popover options, methods and events, go to our [Bootstrap JS Popover Reference](https://www.w3schools.com/bootstrap/bootstrap_ref_js_popover.asp)
