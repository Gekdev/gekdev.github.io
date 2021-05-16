---
layout: default
title: Progress Bar
parent: Information
grand_parent: Bootstrap
nav_order: 4
---

# Info Progress Bar
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Progress Bars

**사용자에게 프로세스를 얼마나 진행하고 있는지 보여줌**

### Basic & Label Progress Bar 

**기본 진행 바**

&#9656; 스크린 리더를 사용하는 사람들을 위해 aria-* 속성을 포함해야 함(기본일 경우)

&#9656; 진행률 표시줄에서 sr-only 클래스를 제거하여 백분율을 표시(라벨일 경우)

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//부모 객체 (배경 진행 바 생성)

class="progress" (필수사항)

//자식 객체 (진행 상황)
class="progress-bar" role="progressbar" aria-valuenow="70" aria-valuemin="0" aria-valuemax="100" style="width:70%"
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/pg_basic.html" height="100" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Basic Progress Bar</h2>
  <div class="progress">
    <div class="progress-bar" role="progressbar" aria-valuenow="70" aria-valuemin="0" aria-valuemax="100" style="width:70%">
      <span class="sr-only">70% Complete</span>
    </div>
  </div>
  
  <h2>Progress Bar With Label</h2>
  <div class="progress">
    <div class="progress-bar" role="progressbar" aria-valuenow="70" aria-valuemin="0" aria-valuemax="100" style="width:70%">
      70%
    </div>
  </div>
</div>
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
Internet Explorer 9 및 이전 버전에서는 진행률 표시 줄이 지원되지 않음 (CSS3 전환 및 애니메이션을 사용하여 일부 효과를 얻기 때문)
</div>

### Decorated Progress Bars

**문맥 클래스는 "색상을 통한 의미"를 제공하는 데 사용**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
//Contextual classes 

* class= "progress-bar progress-bar-success"

* class= "progress-bar progress-bar-info"

* class= "progress-bar progress-bar-warning"

* class= "progress-bar progress-bar-danger"

//Decorating classes 

.progress-bar-striped를 추가하면 줄무늬

.active를 추가하면 애니메이션(.progress-bar-striped 필수사항)
</div>

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/pg_deco.html" height="450" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Colored Progress Bars</h2>
  <p>The contextual classes colors the progress bars:</p> 
  <div class="progress">
    <div class="progress-bar progress-bar-success" role="progressbar" aria-valuenow="40" aria-valuemin="0" aria-valuemax="100" style="width:40%">
      40% Complete (success)
    </div>
  </div>
  <div class="progress">
    <div class="progress-bar progress-bar-info" role="progressbar" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100" style="width:50%">
      50% Complete (info)
    </div>
  </div>
  <div class="progress">
    <div class="progress-bar progress-bar-warning" role="progressbar" aria-valuenow="60" aria-valuemin="0" aria-valuemax="100" style="width:60%">
      60% Complete (warning)
    </div>
  </div>
  <div class="progress">
    <div class="progress-bar progress-bar-danger" role="progressbar" aria-valuenow="70" aria-valuemin="0" aria-valuemax="100" style="width:70%">
      70% Complete (danger)
    </div>
  </div>
  
  <h2>Striped Progress Bars</h2>
  <p>The .progress-bar-striped class adds stripes to the progress bars:</p> 
  <div class="progress">
    <div class="progress-bar progress-bar-success progress-bar-striped" role="progressbar" aria-valuenow="40" aria-valuemin="0" aria-valuemax="100" style="width:40%">
      40% Complete (success)
    </div>
  </div>
  
  <h2>Animated Progress Bar</h2>
  <p>The .active class animates the progress bar:</p> 
  <div class="progress">
    <div class="progress-bar progress-bar-striped active" role="progressbar" aria-valuenow="40" aria-valuemin="0" aria-valuemax="100" style="width:40%">
      40%
    </div>
  </div>
</div>
```

### Stacked Progress Bars

**진행바는 스택시킬 수 있음**

&#9656; 부모객체 안에 여러개의 프로그래스 바를 만들어서 누적시킴

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/information/example/pg_stacked.html" height="300" width="700" style="border:none;" title="example"></iframe>
</div>
```html
<div class="container">
  <h2>Stacked Progress Bars</h2>
  <p>Create a stacked progress bar by placing multiple bars into the same div with class .progress:</p> 
  <div class="progress">
    <div class="progress-bar progress-bar-success" role="progressbar" style="width:40%">
      Free Space
    </div>
    <div class="progress-bar progress-bar-warning" role="progressbar" style="width:10%">
      Warning
    </div>
    <div class="progress-bar progress-bar-danger" role="progressbar" style="width:20%">
      Danger
    </div>
  </div>
</div>
```
