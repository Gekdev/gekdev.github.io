---
layout: default
title: Tooltip
parent: Plugin
grand_parent: Bootstrap
nav_order: 3
---

# Plugin Tooltip
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Tooltip

**사용자가 마우스 포인터를 요소 위로 이동할 때 나타나는 작은 팝업 상자**

### How to make Tooltip

**data-toggle="tooltip" 속성을 추가, title에 표시해야 할 텍스트 지정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1"> 
&#60;a href="#" data-toggle="tooltip" title="Hooray!" &#62;Hover over me&#60;/a &#62;
</div>

★ 툴팁은 jQuery로 초기화 되어야 함
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1"> 
특정한 요소를 선택해서 툴팁 메소드를 호출해야 함

아래 코드는 문서의 모든 툴팁을 활성화
</div>
```html
<script>
$(document).ready(function(){
  $('[data-toggle="tooltip"]').tooltip();
});
</script>
```

### Positioning Tooltips

&#9656; 툴팁은 기본적으로 요소 위로 표시됨

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
<iframe src="https://gekdev.github.io/docs/bootstrap/plugin/example/plg_tt_place.html" height="200" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h3>Tooltip Example</h3>
  <p>The data-placement attribute specifies the tooltip position.</p>
  <ul class="list-inline">
    <li><a href="#" data-toggle="tooltip" data-placement="top" title="Hooray!">Top</a></li>
    <li><a href="#" data-toggle="tooltip" data-placement="bottom" title="Hooray!">Bottom</a></li>
    <li><a href="#" data-toggle="tooltip" data-placement="left" title="Hooray!">Left</a></li>
    <li><a href="#" data-toggle="tooltip" data-placement="right" title="Hooray!">Right</a></li>
    <li><a href="#" data-toggle="tooltip" data-placement="auto left" title="Hooray!">Auto Left</a></li>
  </ul>
</div>

<script>
$(document).ready(function(){
  $('[data-toggle="tooltip"]').tooltip();   
});
</script>
```

---

## Complete Bootstrap Tooltip Reference

For a complete reference of all tooltip options, methods and events, go to our [Bootstrap JS Tooltip Reference](https://www.w3schools.com/bootstrap/bootstrap_ref_js_tooltip.asp)