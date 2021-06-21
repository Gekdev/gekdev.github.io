---
layout: default
title: Scanner
parent: Advanced
grand_parent: Java
nav_order: 1
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

### Example

Q1. while문과 Scanner를 이용해서 키보드로 부터 입력된 데이터로 예금, 출금, 조회, 종료기능을 제공하는 코드를 작성(예금잔액을 입출금내역을 출력)

WhileKeyControlMain.java를 참조해서 자유롭게 작성

```java
boolean run = true;
int balance = 0;

Scanner scanner = new Scanner(System.in); //콘솔에서 기다리고 있는 상태

while(run) {
    System.out.println("-------------------------------------");
    System.out.println("1. 입금  | 2. 출금  | 3. 조회  | 4. 종료" );
    System.out.println("-------------------------------------");
    System.out.println("작업할 번호를 선택하세요");

    int num = scanner.nextInt();

    switch(num) {
    case 1 : System.out.println("입금 => "); 
             balance += scanner.nextInt();
             break;
    case 2 : System.out.println("출금 =>");
             balance -= scanner.nextInt();
             break;
    case 3 : System.out.println("잔액 = "+balance);
             break;
    case 4 : run = false;
             break;
    }

    /* if문을 사용해도 됨
     if(num==1) {
        System.out.println("입금 => ");
        balance += scanner.nextInt();
    } else if(num==2) {
        System.out.println("출금 => ");
        balance -= scanner.nextInt();
    } else if(num==3) {
        System.out.println("잔액 = " + balance);
    } else	if (num==4) {
        run = false;
    }
     */
}

System.out.println("프로그램 종료");
```

키보드로부터 학생 수와 각 학생들의 점수를 입력받아서 최고 점수 및 평균 점수를 구하기

(참고: Scanner의 nextlnt() 메소드이용)

```java
package exercise;

import java.util.Scanner;

public class Exercise09 {
public static void main(String[] args) {
	boolean run = true;
	Scanner scanner = new Scanner(System.in);
	int studentNum = 0;
	int scores[] = null;
	
	while(run) {
		System.out.println("---------------------------------------------------");
		System.out.println("1. 학생수 2. 점수입력 3. 점수리스트 4. 분석 5. 종료");
		System.out.println("---------------------------------------------------");
		System.out.println("작업번호를 선택하세요 =>");
		
		int selectNo = scanner.nextInt();
		
		if(selectNo==1) {
			System.out.println("학생수를 입력하세요");
			studentNum = scanner.nextInt();
			scores = new int[studentNum];
		}else if(selectNo==2) {
			for(int i=0;i<scores.length;i++) {
				System.out.println( (i+1) +"번째 학생점수를 입력하세요");
				scores[i] = scanner.nextInt();
			}
		}else if(selectNo==3) {
			for(int i=0;i<scores.length;i++) {
				System.out.println(i + "번째 학생 점수 = " + scores[i]);
			}
		}else if(selectNo==4) {
			int max = 0;
			int sum = 0;
			double avg = 0;
			for(int i=0;i<scores.length;i++) {
				sum += scores[i];
				if(max<scores[i]) {
					max = scores[i];
				}
				avg = (double) sum/studentNum;
				System.out.println("전체점수 = " + sum);
				System.out.println("평균점수 = " + avg);
				System.out.println("최고점수 = " + max);
			}
		}else{
			run = false;
			System.out.println("프로그램이 종료되었습니다");
		}
		
	}
}
}
```

---

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

### Example

Q1. showInputDialog를 이용해서 키보드로 부터 입력된 데이터로 예금, 출금, 조회, 종료기능을 제공하는 코드를 작성(예금잔액을 입출금내역을 출력)

```java
package com.lec.exercise;

import java.util.Scanner;

import javax.swing.JOptionPane;

public class Exercise08 {
public static void main(String[] args) {

    int num = 0;
    int balance = 0;
    String data;
    Scanner scanner = new Scanner(System.in);

    do {
        data = JOptionPane.showInputDialog("1. 입금\n 2. 출금\n 3. 조회\n 4. 종료\n");
        if(data == null) data = "0";
        if(data.equals("")) {
            num = 0;
        }else {
            num = Integer.parseInt(data);
            //System.out.println("입력된번호 = " + num);
            if(num==1) {
                System.out.println("입금: ");
                balance += scanner.nextInt();
            }else if(num==1) {
                System.out.println("출금: ");
                balance -= scanner.nextInt();
            }else if(num==3) {
                System.out.println("잔액: " + balance);
            }
        }
    }while(num!=4);

    System.out.println("프로그램종료");
                                        
}
}
```
