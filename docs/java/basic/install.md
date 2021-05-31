---
layout: default
title: Basic Install
parent: Basic
grand_parent: Java
nav_order: 1
---

# Basic Install
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JAVA Installation

**자바 개발 도구인 JDK를 깔아야 Java라는 언어로 프로그래밍을 할 수 있기 때문에 JDK(Java Development Kit)을 설치해야 함**

자바라는 언어를 통해 개발을 하고자 하기 때문에 JRE, JVM이 아닌 JDK를 깔아야 함

![](https://gekdev.github.io/docs/java/basic/example/new.jpg)

* JRE : 자바언어로 개발된 어떤 SW를 구동시키기 위해 최소한 설치되어야할 것들을 지원

* JDK : JRE 이상으로 환경구성 뿐만 아니라 직접 개발까지 가능

### Java JDK Install

1. 다운로드 받기

    <span class="fs-2">
    [jdk1.9 win_64버전 다운](https://www.oracle.com/java/technologies/javase-downloads.html){: .btn .btn-outline .mt-2}
    </span>

    이미 설치가 되어있다면
    {: .label .label-yellow mt-2}
    <div class="code-example" markdown="1">
    1. 언인스톨 / 재설치

    2. 그냥 사용

    3. 경로설정 : C:\Program Files\Java\jdk1.8
    </div>

2. Setting File path

    ![](https://gekdev.github.io/docs/java/basic/example/ins_01.png)

    **개발도구폴더**

    폴더를 새로 생성하는데 폴더이름을 jdk1.8로 해야함 (위 이미지와 경로가 다름) 

3. Create jre Folder

    **실행폴더**

    폴더가 없는 경우는 해당폴더를 생성

    경로 : **C:\Program Files\Java\jre1.8**

    ![](https://gekdev.github.io/docs/java/basic/example/ins_02.png)

    폴더 생성 후 설치해야함(위 이미지와 경로가 다름) 

### API Document

JDK에서 제공하는 표준 클래스 라이브러리 설명해 놓은 HTML 페이지

<span class="fs-2">
[ORACLE](https://docs.oracle.com/javase/8/docs/api/){: .btn .btn-outline .mt-2}
</span>

---

## Setting Environment

cmd 콘솔에서 javac로 compile하거나, 다른 프로그램에서 자바 JDK를 참조하기 위해선 윈도우 환경변수를 지정해야 함 

이클립스같은 통합개발환경에서는 환경변수를 알아서 프로그램이 관리해줌

### Steps

1. **내 PC를 우클릭해서 속성을 들어가서 고급시스템설정**

    **winkey + R &#8594; sysdm.cpl** 도 동일한 방법

    ![](https://gekdev.github.io/docs/java/basic/example/javains_01.png)

2. 새로운 시스템 변수 생성

    **자바에 관련된 환경변수를 설정하기 위해선 새로운 시스템변수를 만들어야 함**

    ![](https://gekdev.github.io/docs/java/basic/example/javains_02.png)

    1. **변수 이름 : JAVA_HOME**

    2. **변수 값   : C:\Program Files\Java\jdk1.8**

    ![](https://gekdev.github.io/docs/java/basic/example/javains_03.png)

3. PATH 잡기

    우리가만든 시스템변수 JAVA_HOME 시스템변수의 PATH를 잡아주기

    ![](https://gekdev.github.io/docs/java/basic/example/javains_04.png)

    **새로만들기 &#8594; %JAVA_HOME%\bin**

    ![](https://gekdev.github.io/docs/java/basic/example/javains_05.png)
    
### Check Environment

1. CMD 콘솔창 열기

2. java -version이나 javac -version 명령어 치기
    
    ```java
    java -version 
    
    javac -version
    ```

3. 아래와 같이 나오면 설치 완료

    ![](https://gekdev.github.io/docs/java/basic/example/javains_06.png)
  
---

## Reference

### Site

* [Tistory](https://limkydev.tistory.com/61)

### School 

* [학원파일](https://gekdev.github.io/docs/java/basic/example/01.jdk설정.txt)

