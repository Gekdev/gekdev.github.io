---
layout: default
title: Scanner
parent: Java
nav_order: 98
---

# Java Scanner
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Java Scanner

키보드로부터 문자열을 입력받는 방법

System.in.read()메서드는 하나의 키코드만 읽어서 콘솔에 입력된 전체 문자열을 한번에 읽을 수 없음

대신에 Scanner객체를 생성하고 nextLine()에서 메서드를 호출하면 콘솔에 입력된 문자열을 한번에 읽을수가 있음

Scanner는 자주 사용하지 않는 객체라서 public class위에 따로 선언해주어야 함

외부에서 유틸리티(프로그램, 클래스)를 자동 로드하려면, ctrl shift o

```java
// ① 자동로드
import java.util.Scanner;

public class DoWhileMain {
	public static void main(String[] args) {
    // ② 프로그램 처음 실행되는 메시지 생성
    System.out.println("메시지를 입력하세요");
    System.out.println("프로그램을 종료하려면 q를 입력하세요!");

    // ① ctrl shift o로 import하기
    Scanner scanner = new Scanner(System.in);
    String inputString = null;

    // ③ 반복문 생성
    do {
        System.out.println("->");               
        inputString = scanner.nextLine();       // ④ 입력된 문자열 가져오기
        System.out.println(inputString);        // ⑤ 입력된 문자열 그대로 출력
    }while (!inputString.contentEquals("q"));   // ⑥ q라고 누르면 반복문 종료

    System.out.println();                       // ⑦ 반복문이 종료되었다면 실행되는 명령문
    System.out.println("프로그램종료");
    
    }
}
```

![](https://gekdev.github.io/docs/java/example/scanner.jpg)

## Swing

java.swing 패키지(라이브러리)는 GUI 환경을 지원

예제
{: .label .label-purple .mt-2}
```java
// ① import하기
import javax.swing.JOptionPane;

public class SwingMain {
	
    public static void main(String[] args) {
        // ② 프로그램 처음 실행되는 창 생성
        String money_ = JOptionPane.showInputDialog("비용을 입력하세요");
        // ③ 받은 입력값을 문자열에서 정수로 변경
        int money = Integer.parseInt(money_);
        // ④ 메시지 출력
        System.out.println("입력한 비용 =" + money*10 + "원 입니다");

    }
}
```

인풋창

![](https://gekdev.github.io/docs/java/example/swing1.jpg)

실행결과

![](https://gekdev.github.io/docs/java/example/swing2.jpg)

