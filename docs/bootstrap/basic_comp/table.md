---
layout: default
title: Table
parent: Basic Comp
grand_parent: Bootstrap
nav_order: 5
---

# Basic BT Table
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Table Classes

### table class

**넓이가 100%인 테이블 생성, 행 사이에 보더 적용**

&#9656; 기본 부트 스트랩 테이블에는 밝은 패딩과 수평 구분선만 있음

&#9656; .table클래스는 테이블에 기본 스타일만 추가

<div class="code-example" markdown="1">
<iframe src="https://gekdev.github.io/docs/bootstrap/basic_comp/example/bt_tb_table.html" height="200" width="700" style="border:none;" title="bt heading example"></iframe>
</div>
```html
<div class="container">
  <h2>Basic Table</h2>
  <p>The .table class adds basic styling (light padding and only horizontal dividers) to a table:</p>            
  <table class="table">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
  </table>
</div>
```

스트라이프 행
이 .table-striped클래스는 테이블에 얼룩말 줄무늬를 추가합니다.

예
Firstname	Lastname	Email
John	Doe	john@example.com
Mary	Moe	mary@example.com
July	Dooley	july@example.com
경계 표
이 .table-bordered클래스는 표와 셀의 모든면에 테두리를 추가합니다.

예
Firstname	Lastname	Email
John	Doe	john@example.com
Mary	Moe	mary@example.com
July	Dooley	july@example.com
호버 행
.table-hover클래스는 테이블 행에 호버 효과 (회색 배경 색상)을 추가합니다 :

예
Firstname	Lastname	Email
John	Doe	john@example.com
Mary	Moe	mary@example.com
July	Dooley	july@example.com
압축 된 테이블
이 .table-condensed클래스는 셀 패딩을 반으로 줄여 테이블을 더 간결하게 만듭니다.

예
Firstname	Lastname	Email
John	Doe	john@example.com
Mary	Moe	mary@example.com
July	Dooley	july@example.com
상황 별 클래스
상황 별 클래스를 사용하여 테이블 행 ( <tr>) 또는 테이블 셀 ( <td>)의 색상을 지정할 수 있습니다 .

예
Firstname	Lastname	Email
Default	Defaultson	def@somemail.com
Success	Doe	john@example.com
Danger	Moe	mary@example.com
Info	Dooley	july@example.com
Warning	Refs	bo@example.com
Active	Activeson	act@example.com
사용할 수있는 컨텍스트 클래스는 다음과 같습니다.

수업	기술
.active	표 행 또는 표 셀에 호버 색상을 적용합니다.
.success	성공하거나 긍정적 인 행동을 나타냅니다.
.info	중립적 인 정보 변경 또는 조치를 나타냅니다.
.warning	주의가 필요할 수있는 경고를 나타냅니다.
.danger	위험하거나 잠재적으로 부정적인 행동을 나타냅니다.
반응 형 테이블
.table-responsive클래스는 반응 테이블을 작성합니다. 그러면 테이블이 소형 장치 (768px 미만)에서 가로로 스크롤됩니다. 768px보다 큰 화면에서 볼 때 차이가 없습니다.

### [Table](https://gekdev.github.io/docs/css/bootstrap/table-sample.html)

* class="table"
    
    
    
* class="table table-striped"

    각 행에 색상(배경)을 줌
    
* class="table table-bordered"

    테이블 전체 테두리
    
* class="table table-hover"

    각 행에 마우스 오버시 색상에 오버 기능 추가
    
* class="table table-condensed"

    각행의 padding 값이 작아짐
    
* class="active" class="success" class="warning" class="danger" 

    각 셀에 색상을 지원
    
* div class="table-responsive"

    테이블을 감싸게 되면, 768px 이하의 사이즈에서 자동으로 테이블에 스크롤 바가 생성
    
* table class="table table-hover"

   호버시 색상 살짝 바뀜
       
