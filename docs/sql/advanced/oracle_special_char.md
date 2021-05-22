---
layout: default
title: Special Characters
parent: Advanced
grand_parent: SQL / Oracle
nav_order: 1
---

# Oracle Special Characters 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Oracle 패스워드에 사용가능한 특수문자

오라클에서 유저 생성 시 들어가는 패스워드에 특수문자를 사용하려면 몇가지 지켜져야하는 복잡성이 있음

실제 키보드상에 존재하는 특수문자는 패스워드에 모두 사용가능 하지만 아래 내용에 부합하게 설정해야 함

### Oracle Recommened Special characters

**그냥 입력해도 패스워드로 등록이 됨**

```html
_  : Underscore, 언더바

&#35; : Crossshatch, Sharp, 샵

$ : Dollar sign, 달러
```

ex) create user test identified by qwe123#

### "" Special characters

**"" 안에 입력해야 패스워드에 등록이 되는 특수 문자**

패스워드 입력 시 " " 까지 입력해야 로그인이 됨

```html
! 
% 
^ 
@ 
* 
( 
)
+
~
&#96;
&#95;
&#61;
&#91;
{
]
}
\
|
;
:
'
,
&#60;
.
&#62;
/ 
```

ex) create user test identified by "qwe123@"

note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
윗 내용은 오라클 9i, 10g, 11g 모두 적용되는 사항 (단 11g는 대소문자 구분)    
</div>

### Reference site

[DexCore.Net](https://dexcore.tistory.com/733)