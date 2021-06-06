---
layout: default
title: Package
parent: Class
grand_parent: Java
nav_order: 6
---

# Class Package
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 패키지(package)
 
프로그램을 개발하다 보면 작게는 수십개, 많게는 수백개의 클래스를 작성해야 함

클래스를 체계적으로 관리하지 않으면 클래스간의 관계가 뒤엉켜서 복잡하고 난해한 프로그램이 되어버려 유지보수가 어렵게됨

자바에서는 클래스를 체계적으로 관리하기 위해 패키지를 사용함

피씨에서 파일을 저장해서 관리하듯이 패키지를 만들어 클래스를 저장, 관리하도록 지원

패키지의 물리적인 형태는 파일시스템의 폴더이지만 단순히 폴더 기능만 하는게 아니라 클래스 이름의 일부분

즉, 클래스이름은 패키지명을 포함한 클래스파일명이 전체 클래스 이름

패키지는 클래스를 유일하게 만들어주는 식별자 역할을 함

즉, 클래스이름이 동일하더라도 패키지가 다르면 다른 클래스로 인식함

클래스 전체이름은 "패키지명.클래스명"인데 상위 하위로 구분이 되어있다면 (.)연산자로 구분해서 사용

패키지의 선언은 자바명명규칙에 의거해 패키지명은 전부 소문자로 정의하는것이 관례

```java
다른 패키지의 클래스 가져오기
com.lec.ex09_pkg.hankook.Tire frontTire = new com.lec.ex09_pkg.hankook.Tire();
com.lec.ex09_pkg.kumho.Tire backTire = new com.lec.ex09_pkg.kumho.Tire();
```