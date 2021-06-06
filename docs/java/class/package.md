---
layout: default
title: Package
parent: Class
grand_parent: Java
nav_order: 4
---

# Class Package
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Package 

### What is Package?
 
**패키지(package)란 클래스와 인터페이스의 집합**

&#9656; 패키지의 물리적인 형태는 파일시스템의 폴더이지만 단순히 폴더 기능만 하는게 아니라 클래스 이름의 일부분, 클래스이름은 패키지명을 포함한 클래스파일명이 전체 클래스 이름

&#9656; 패키지는 클래스를 유일하게 만들어주는 식별자 역할을 해서 클래스이름이 동일하더라도 패키지가 다르면 다른 클래스로 인식함

&#9656; 클래스 전체이름은 "패키지명.클래스명"인데 상위 하위로 구분이 되어있다면 (.)연산자로 구분해서 사용

&#9656; 패키지의 선언은 자바명명규칙에 의거해 패키지명은 전부 소문자로 정의하는것이 관례

### Why Use Package?

프로그램을 개발하다 보면 작게는 수십개, 많게는 수백개의 클래스를 작성해야 함

클래스를 체계적으로 관리하지 않으면 클래스간의 관계가 뒤엉켜서 복잡하고 난해한 프로그램이 되어버려 유지보수가 어렵게됨

**자바에서는 체계적으로 관리하기 위해 패키지를 사용함**

PC에서 파일을 저장해서 관리하듯이 패키지를 만들어 클래스를 저장, 관리하도록 지원

### Package Declaration

명령문을 클래스나 인터페이스의 소스 파일에 추가하면 됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
package 패키지이름;

&#9656; 패키지 이름: 패키지의 경로까지 포함한 풀 네임을 명시
</div>

### Unnamed Package

모든 클래스는 반드시 하나 이상의 패키지에 포함해야하지만 자바 컴파일러는 소스 파일에 어떠한 패키지의 선언도 포함되지 않으면, 기본적으로 **이름 없는 패키지(unnamed package)에 포함해 컴파일함**

&#8594; 패키지를 명시하지 않은 모든 클래스와 인터페이스는 모두 같은 패키지에 포함

---

## Import Statement

패키지에 속한 클래스를 다른 파일에서 사용하기 위해서 사용하기 위해서는 아래 두가지 방법이 있음

1. 클래스 이름 앞에 패키지의 경로까지 포함한 풀 네임을 명시

    ```java
    다른 패키지의 클래스 가져오기
    com.lec.ex09_pkg.hankook.Tire frontTire = new com.lec.ex09_pkg.hankook.Tire();
    com.lec.ex09_pkg.kumho.Tire backTire = new com.lec.ex09_pkg.kumho.Tire();
    ```

2. import문 사용

    자바 컴파일러에 코드에서 사용할 클래스의 패키지에 대한 정보를 미리 제공하는 역할

    다른 패키지에 속한 클래스를 패키지 이름을 제외한 클래스 이름만으로 사용할 수 있음

### Import Declaration

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. import 패키지이름.클래스이름;

2. import 패키지이름.*;
</div>

1번은 특정 클래스만을 사용하고자 할 때 사용, 2번은 해당 패키지의 모든 클래스를 클래스 이름만으로 사용하고 싶을 때 사용

### Features of Import

별표는 패키지의 다른클래스를 포함하는거지 패키지의 하위패키지를 포함하는건 아님

즉 import java.awt.*;와 import java.util.*;를 import java.*;로 합칠 순 없음

자바에서는 자주사용하는 패키지에서는 import하지 않아도 이름만으로도 사용할 수 있도록 하고 있음
