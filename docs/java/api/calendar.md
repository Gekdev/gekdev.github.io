---
layout: default
title: Calendar 
parent: Basic API 
grand_parent: Java
nav_order: 8
---

# Basic API Calendar
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Calendar 클래스
자바에서의 날짜 및 시간 처리
JDK 1.0에서는 Date 클래스를 사용하여 날짜에 관한 간단한 처리만을 수행할 수 있었습니다.

하지만 Date 클래스는 현재 대부분의 메소드가 사용을 권장하지 않고(deprecated) 있습니다.

 

JDK 1.1부터는 새롭게 제공되는 Calendar 클래스를 이용하여 날짜와 시간에 관한 처리를 수행하게 됩니다.

하지만 이러한 Calendar 클래스는 다음과 같은 문제점을 안고 있습니다.

 

1. Calendar 인스턴스는 불변 객체(immutable object)가 아니라서 값이 수정될 수 있습니다.

2. 윤초(leap second)와 같은 특별한 상황을 고려하지 않습니다.

3. Calendar 클래스에서는 월(month)을 나타낼 때 1월부터 12월을 0부터 11까지로 표현해야 하는 불편함이 있습니다.

 

따라서 많은 자바 개발자들은 Calendar 클래스뿐만 아니라 더 나은 성능의 Joda-Time이라는 라이브러리를 함께 사용해 왔습니다.

 

Java SE 8 버전에서는 이러한 Joda-Time 라이브러리를 발전시킨 새로운 날짜와 시간 API인 java.time 패키지를 제공합니다.

java.time 패키지는 위와 같은 문제점을 모두 해결했으며, 다양한 기능을 지원하는 다수의 하위 패키지를 포함하고 있습니다.

 

java.time 패키지에 대한 더 자세한 사항은 JAVA8 java.time 패키지 수업에서 확인할 수 있습니다.

 

JAVA8 java.time 패키지 수업 확인 =>

java.util.Calendar 클래스
Calendar 클래스는 자바에서 날짜와 시간에 관한 데이터를 손쉽게 처리할 수 있도록 제공하는 추상 클래스입니다.

이 클래스가 추상 클래스로 선언된 이유는 나라마다 사용하는 달력 체계가 조금씩 다를 수 있기 때문입니다.

 

이러한 Calendar 클래스에는 날짜와 시간을 처리하기 위한 다양한 필드와 메소드가 포함되어 있습니다.

Calendar 클래스의 모든 필드는 클래스 변수(static variable)이므로, 객체를 생성하지 않고도 바로 사용할 수 있습니다.

java.util.GregorianCalendar 클래스
현재 전 세계적으로 가장 많이 사용되는 달력은 1582년 교황 그레고리오 13세가 개혁한 그레고리오 달력입니다.

Calendar 클래스는 추상 클래스이므로, 직접 인스턴스를 생성할 수 없습니다.

GregorianCalendar 클래스는 이러한 Calendar 클래스를 상속받아 그레고리오 달력을 완전히 구현한 하위 클래스입니다.

add() 메소드
add() 메소드는 전달된 Calendar 필드에서 일정 시간 만큼을 더하거나 빼줍니다.

즉, 특정 시간을 기준으로 일정 시간 전후의 날짜와 시간을 알 수 있습니다.

 

다음 예제는 add() 메소드를 이용하여 현재 시각에 120초를 더하는 예제입니다.

예제
Calendar time = Calendar.getInstance();

System.out.println(time.getTime());

 

time.add(Calendar.SECOND, 120);

System.out.println(time.getTime());

코딩연습 ▶

실행 결과
Thu Feb 16 08:57:29 KST 2017

Thu Feb 16 08:59:29 KST 2017

 

Calendar 클래스의 메소드는 현재 시각을 기준으로 동작하므로, 여러분의 결과는 위의 실행 결과와는 다를 것입니다.
before()와 after() 메소드
두 시간상의 전후 관계만을 알고 싶을 경우에는 before()와 after() 메소드를 사용할 수 있습니다.

before() 메소드는 현재 Calendar 인스턴스가 전달된 객체가 나타내는 시간보다 앞서는지를 판단합니다.

반대로 after() 메소드는 현재 Calendar 인스턴스가 전달된 객체가 나타내는 시간보다 나중인지를 판단합니다.

 

예제
Calendar time1 = Calendar.getInstance();

Calendar time2 = Calendar.getInstance();

Calendar time3 = Calendar.getInstance();

 

time2.set(1982, 2, 19);

time3.set(2020, 2, 19);

 

System.out.println(time1.before(time2));

System.out.println(time1.before(time3));

코딩연습 ▶

실행 결과
false

true

get() 메소드
get() 메소드는 전달된 Calendar 필드에 저장된 값을 반환합니다.

 

예제
Calendar time = Calendar.getInstance();

 

System.out.println(time.getTime());

System.out.println(time.get(Calendar.DAY_OF_WEEK));

System.out.println(time.get(Calendar.MONTH) + 1);

System.out.println(time.get(Calendar.DAY_OF_MONTH));

System.out.println(time.get(Calendar.HOUR_OF_DAY));

System.out.println(time.get(Calendar.MINUTE));

System.out.println(time.get(Calendar.SECOND));

System.out.println(time.get(Calendar.YEAR));

코딩연습 ▶

실행 결과
Thu Feb 16 08:57:44 KST 2017

5

2

16

8

57

44

2017

roll() 메소드
roll() 메소드는 전달된 Calendar 필드에서 일정 시간 만큼을 더하거나 빼줍니다.

하지만 add() 메소드와는 달리 다른 Calendar 필드에는 영향을 주지 않습니다.

즉, 계산 결과가 해당 필드의 최댓값이나 최솟값을 넘어가도 다른 필드에 영향을 주지 않습니다.

 

예제
Calendar time1 = Calendar.getInstance();

Calendar time2 = Calendar.getInstance();

System.out.println(time1.getTime());

 

time1.add(Calendar.SECOND, 60);

System.out.println(time1.getTime());

 

time2.roll(Calendar.SECOND, 60);

System.out.println(time2.getTime());

코딩연습 ▶

실행 결과
Thu Feb 16 08:58:23 KST 2017

Thu Feb 16 08:59:23 KST 2017

Thu Feb 16 08:58:23 KST 2017

 

위의 예제에서 add() 메소드를 사용하여 Calendar.SECOND 필드를 60초 증가시키면 결과적으로 Calendar.MINUTE 필드가 1 증가해야 합니다.

하지만 roll() 메소드를 사용하여 Calendar.SECOND 필드를 60초 증가시키면 Calendar.MINUTE 필드에는 아무런 영향을 주지 않습니다.

즉, Calendar.SECOND 필드만이 60초 증가하여 결과적으로 같은 값이 출력되게 됩니다.

set() 메소드
set() 메소드는 전달된 Calendar 필드를 특정 값으로 설정합니다.

 

다음 예제는 set() 메소드에 다양한 형태의 인수를 전달하여 시간을 설정하는 예제입니다.

예제
Calendar time = Calendar.getInstance();

System.out.println(time.getTime());

 

time.set(Calendar.YEAR, 2020);

System.out.println(time.getTime());

 

time.set(1982, 1, 19); // 1은 2월을 나타냄.

System.out.println(time.getTime());

 

time.set(1982, 1, 19, 12, 34, 56);

System.out.println(time.getTime());

코딩연습 ▶

실행 결과
Thu Feb 16 08:58:01 KST 2017

Sun Feb 16 08:58:01 KST 2020

Fri Feb 19 08:58:01 KST 1982

Fri Feb 19 12:34:56 KST 1982

대표적인 Calendar 메소드
Calendar 클래스의 메소드는 매우 다양하며, 그중에서 많이 사용되는 메소드는 다음과 같습니다.

메소드	설명
void add(int field, int amount)	
전달된 Calendar 필드에서 특정 시간 만큼을 더하거나 뺌.

boolean after(Object when)	
현재 Calendar 인스턴스가 전달된 객체가 나타내는 시간보다 나중인지를 확인함.

boolean before(Object when)	
현재 Calendar 인스턴스가 전달된 객체가 나타내는 시간보다 앞서는지를 확인함.

void clear(int field)	현재 Calendar 인스턴스의 모든 필드의 값을 undefined로 설정함.
int get(int field)	
전달된 Calendar 필드에 저장된 값을 반환함.

static Calendar getInstance()	시스템의 현재 날짜와 시간으로 Calendar 인스턴스를 생성하여 반환함.
Date getTime()	현재 Calendar 인스턴스의 시간 정보를 나타내는 Date 인스턴스를 생성하여 반환함.
void roll(int field, int amount)	
전달된 Calendar 필드에서 특정 시간 만큼을 더하거나 뺌.

void set(int field, int value)

void set(int year, int month, int date)

void set(int year, int month, int date, int hourOfDay, int minute)
void set(int year, int month, int date, int hourOfDay, int minute, int second)

전달된 Calendar 필드를 특정 값으로 설정함.