---
layout: default
title: Thread
parent: Java
nav_order: 17
---

# Java Thread
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Thread Basic

### Process

**사용자가 작성한 프로그램이 운영체제에 의해 메모리 공간을 할당받아 실행 중인 프로그램(program)**

구성 : 자원(프로그램에 사용되는 데이터와 메모리 등) + 스레드

### Thread

**프로세스(process) 내에서 실제로 작업을 수행하는 주체**

모든 프로세스에는 한 개 이상의 스레드가 존재하여 작업을 수행

Thread를 생성하는데에는 Runnable 인터페이스를 구현하거나 Thread 클래스를 상속받는 방법 두가지 방법이 있음

### Multi Tasking

**멀티 태스킹, 두가지 이상의 작업을 동시에 처리하는 것**

1. 멀티 프로세스

    **독립적으로 프로그램들을 실행하고 여러가지 작업 처리**
    
    CPU에 프로그램이 여러가지 프로세스로 돌아감
    
2. 멀티 스레드

    **한 개의 프로그램을 실행하고 내부적으로 여러가지 작업 처리**
    
    한 프로세스 내에 멀티 작업을 하는것
    
    두 개 이상의 스레드를 가지는 프로세스를 멀티스레드 프로세스(multi-threaded process)
 
### main() Thread

**모든 자바프로그램은 메인 스레드가 main()메소드 실행하며 시작**

&#9656; main()메소드의 첫 코드부터 아래로 순차적으로 실행

&#9656; 실행 종료 조건 : 마지막 코드 실행, return문

&#9656; main() 메소드를 실행하는 스레드의 우선순위는 언제나 5

### Multi Thread

&#9656; 멀티 쓰레드로 실행하는 애플리케이션을 개발하려면 먼저 몇개의 작업을 병렬로 실행할지를 결정하고 각 작업별로 쓰레드를 생성해야 함

&#9656; 어떤 자바 애플리케이션이건 메인 쓰레드는 반드시 존재하기 때문에 메인 작업이외에 추가적인 병렬 작업의 수만큼 쓰레드를 생성해야함

&#9656; 자바에서는 작업 쓰레드도 객체로 생성되기 때문에 객체가 필요함

&#9656; java.langThread클래스를 직접 객체화해서 생성해도 되지만, Thread를 상속해서 하위 클래스를 만들어 생성할 수 있음

### Thread Name

**Thread는 자신의 이름을 가지고 있음**

&#9656; 쓰레드의 이름이 큰역할을 하는건 아니지만 디버깅할 때 유용함

&#9656; 메인쓰레드는 main이라는 이름을 가지고 있고 우리가 생성한 쓰레드는 자동적으로 Thread-n 이라는 이름으로 설정 (n은 쓰레드의 일련번호를 의미)

&#9656; w자동으로 부여되는 이름 대신에 사용자가 이름을 설정하고 싶을 경우에는 Thread클래스의 setName()메서드로 변경하고 getName()메서드로 쓰레드의 이름을 가져올 수 있음

&#8594; setName()과 getName()은 Thread의 인스턴트 메서드이기 때문에 객체의 참조가 필요

&#9656; 만약, 쓰레드 객체의 참조를 가지고 있지 않다면 Thread정적 메서드인 currentTread()로 코드를 실행하면 현재 쓰레드의 참조를 얻을 수 있음

예제 : ThreadA
{: .label .label-purple .mt-2}
```java
public class ThreadA extends Thread{

	public ThreadA() {
		setName("ThreadA"); //스레드 이름을 설정
	}
	
	@Override
	public void run() {
		for(int i=0; i<2 ; i++) {
			System.out.println(getName() + "가 출력한 내용"); //스레드 이름을 가져옴
			
		}
	}
}
```

예제 : Thread B, C
{: .label .label-purple .mt-2}
```java
public class ThreadB extends Thread{
	@Override
	public void run() {
		for(int i=0; i<2 ; i++) {
			System.out.println(getName() + "가 출력한 내용"); //스레드 이름을 가져옴
			
		}
	}
}

public class ThreadC extends Thread{
	@Override
	public void run() {
		for(int i=0; i<2 ; i++) {
			System.out.println(getName() + "가 출력한 내용"); //스레드 이름을 가져옴
			
		}
	}
}
```

예제 : Thread Main
{: .label .label-purple .mt-2}
```java
public class ThreadMain {
public static void main(String[] args) {
	
	Thread mainThread = Thread.currentThread();
	System.out.println("프로그램 시작 쓰레드 이름 = " + mainThread.getName());
	
	ThreadA threadA = new ThreadA();
	System.out.println("작업 쓰레드 이름 = " + threadA.getName());
	threadA.start();

	ThreadB threadB = new ThreadB();
	System.out.println("작업 쓰레드 이름 = " + threadB.getName());
	threadB.start();

	ThreadC threadC = new ThreadC();
	System.out.println("작업 쓰레드 이름 = " + threadC.getName());
	threadC.start();
	
}
}
```

![](https://gekdev.github.io/docs/java/example/thread.jpg)

---

## How to make Thread?

1. Runnable 인터페이스를 구현하는 방법

2. Thread 클래스를 상속받는 방법

Thread 클래스를 상속받으면 다른 클래스를 상속받을 수 없으므로, 일반적으로 Runnable 인터페이스를 구현하는 방법으로 스레드를 생성

Runnable 인터페이스는 몸체가 없는 메소드인 run() 메소드 단 하나만을 가지는 간단한 인터페이스

### Runnable Interface

syntax
{: .label .mt-2}
```java
Thread thread = new Thread(Runnable target);
```

Runnable을 매개값으로 갖는 생성자를 호출

Runnable은 작업 쓰레드가 실행할 수 있는 코드를 가지고 있는 객체

인터페이스 타입이기때문에 구현 객체를 만들어 대입해야 함

Runnable 인터페이스는 run()메서드가 하나 정의되어있는데 구현객체는 run()을 재정의해서 작업 쓰레드가 실행할 코드를 작성해야 함

Runnable을 구현한 객체는 작업내역을 가지고 있는 객체이지 실제 쓰레드는 아님

Runnable구현객체를 생성 후 , 이것을 매개값으로 해서 Thread생성자를 호출하면 비로소 작업 쓰레드가 생성되는것

작업쓰레드는 생성되는 즉시 실행되는 것이 아니고 start()메서드를 호출해야 만 비로소 쓰레드가 생성됨

1. 외부 클래스

    ```java
    public class BeepPrintMain2 {
    public static void main(String[] args) throws Exception {
        Runnable beepTask = new BeepTask();   //Runnable구현객체를 생성
        Thread thread = new Thread(beepTask); //매개값으로 해서 Thread생성자를 호출
        thread.start();
    
        for(int i=0 ;i<5; i++) {
            System.out.println("띵");
            Thread.sleep(700);
        }                                                     
    }}
    ...

    class BeepTask implements Runnable{

    @Override
    public void run() {
        Toolkit toolkit = Toolkit.getDefaultToolkit();
        for(int i=0 ; i<5 ; i++) {
            toolkit.beep();
            try {
                Thread.sleep(700);
            } catch (InterruptedException e) {
                e.printStackTrace();
            } 
        }
    }
    }
    ```

2. 익명객체

    ```java
    public class BeepPrintMain2 {
    public static void main(String[] args) throws Exception {
        Thread thread = new Thread(new Runnable() {

        @Override
        public void run() {
            Toolkit toolkit = Toolkit.getDefaultToolkit();
            for(int i=0 ; i<5 ; i++) {
                toolkit.beep();
                try {
                    Thread.sleep(700);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } 
            }
        }});
        thread.start();
        
        for(int i=0 ;i<5; i++) {
            System.out.println("띵");
            Thread.sleep(700);
        }                                                     
    }}
    ```

3. lamda식

    **한개의 메서드만 가진 interface(Functional Interface)는 람다식으로 구현 가능**
    
    ```java
    public class BeepPrintMain2 {
    public static void main(String[] args) throws Exception {
    
        Thread thread = new Thread(() -> {
            Toolkit toolkit = Toolkit.getDefaultToolkit();
            for(int i=0 ; i<5 ; i++) {
                toolkit.beep();
                try {
                    Thread.sleep(700);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } 
            }});
        thread.start();
        
        for(int i=0 ;i<5; i++) {
            System.out.println("띵");
            Thread.sleep(700);
        }                                                     
    }}
    ```

### Thread Class 

작업쓰레드가 실행할 작업을 Runnable로 만들지 않고 Thread하위 클래스로 작업 쓰레드를 정의하면서 작업 내용을 포함시킬 수 있음

Thread클래스를 상속한 후 runs()메서드를 재정의 해서 쓰레드가 실행할 코드를 작성하면 됨

작업쓰레드로부터 객체를 생성하는 방법은 일반적인 객체를 생성하는 방법과 동일


1. 외부 클래스

    ```java
    public class BeepPrintMain3 {
    public static void main(String[] args) throws InterruptedException {
        Thread thread = new BeepThread();
        thread.start();
                                                                        
        for(int i=0 ;i<5; i++) {
            System.out.println("띵");
            Thread.sleep(700);
        }
    }}

    ...

    class BeepThread extends Thread {

        @Override
        public void run() {
            Toolkit toolkit = Toolkit.getDefaultToolkit();
            for(int i=0 ; i<5 ; i++) {
                toolkit.beep();
                try {
                    Thread.sleep(700);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } 
            }
        }
    }
    ```

2. 익명객체

    ```java
    public class BeepPrintMain3 {
    public static void main(String[] args) throws InterruptedException {

        Thread thread = new Thread() {
            @Override
            public void run() {
                Toolkit toolkit = Toolkit.getDefaultToolkit();
                for(int i=0 ; i<5 ; i++) {
                    toolkit.beep();
                    try {
                        Thread.sleep(700);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    } 
                }
            }
        };
        thread.start();
                                                                        
        for(int i=0 ;i<5; i++) {
            System.out.println("띵");
            Thread.sleep(700);
        }

    }}
    ```

3. lamda식

    thread는 funtional interface가 아니기 때문에 lamda식 사용불가
    
---



    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    




























