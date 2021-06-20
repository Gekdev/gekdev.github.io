---
layout: default
title: Enum
parent: Datatype
grand_parent: Java
nav_order: 4
---

# Datatype Enum
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Enum Type
{: .no_toc}

### Enum Type Basic

**한정된 값만 갖는 데이터타입을 열거타입(Enumeration Type)이라고 함**

예로 요일에 대한 데이터는 "월~일"이라는 7개의 값만, 계절에 대한 데이터는 봄,여름,가을,겨울이라는 4개의 값이 있음

열거타입을 선언하기 위해서는 먼저 열거타입의 이름을 정하고 열거타입 이름으로 소스파일(~.java)을 생성해야함

### How to use Enum

**열거타입도 하나의 데이터타입 (사용자정의)이므로 변수로 선언하고 사용해야 함**

&#9656; 열거타입변수를 선언했다면 열거상수를 저장 및 사용할 수 있음

&#9656; 열거상수는 단독으로 사용할 수 없고 반드시 "열거타입.열거상수"로 사용해야 함

ex) Week.MONDAY 형태로 사용

### Naming Rule

열거타입의 이름은 관례적으로 첫글자를 대문자로 하고 나머진 소문자

여러단어로 구성된 이름이라면 각 단어의 첫글자는 대문자로 하는 것이 관례

### Example

```java
public enum Week {
	// 열거상수
    MONDAY,
    THUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}

...
    
public static void main(String[] args) {
String str = new String();
    Week today = null;
    System.out.println(today.FRIDAY);

    //현재요일을 확인하기
    Calendar cal = Calendar.getInstance(); //객체생성
    int week = cal.get(Calendar.DAY_OF_WEEK); //현재요일 1~7(일~토)를 리턴
    switch(week) {
        case 1 : today = Week.SUNDAY; break;
        case 2 : today = Week.MONDAY; break;
        case 3 : today = Week.THUESDAY; break;
        case 4 : today = Week.WEDNESDAY; break;
        case 5 : today = Week.THURSDAY; break;
        case 6 : today = Week.FRIDAY; break;
        case 7 : today = Week.SATURDAY; break;
    }

    System.out.println(today);
}
```
