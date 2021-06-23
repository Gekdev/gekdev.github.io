---
layout: default
title: Custom Tag & JSTL
parent: JSP
nav_order: 9
---

# JSP Custom Tag & JSTL
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Custom Tag & JSTL

### What is Custom Tag & JSTL?

**표준라이브러리**

커스텀 태그 : JSP를 확장시켜주는 기능, 액션태그와 마찬가지로 태그 형태로 기능을 제공

액션태그와의 차이점은 커스텀 태그는 개발자가 직접 개발해주어야 함

사용목적 : JSP코드에서 중복되는 것을 모듈화하거나 스크립트 코드를 사용할 때 발생하는 소스 코드의 복잡함을 없애기 위해 사용

**JSTL(JavaServer Pages Standard Tag Library) : 커스텀 태그 중 자주 사용하는 것들을 별도로 표준화한 태그 라이브러리**

### Features of JSTL

* if-else조건문 그리고 for 구문과 같은 반복 처리를 커스텀 태그를 이용해서 구현할 수 있도록 함

* 스크립트 코드보다 이해하기 쉽기 때문에 자바 언어에 익숙하지 않더라도 JSTL을 이용해서 어느 정도 논리적인 처리를 수행할 수 있음