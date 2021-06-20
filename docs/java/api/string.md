---
layout: default
title: String 
parent: Basic API 
grand_parent: Java
nav_order: 2
---

# Basic API String
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## String 클래스
java.lang.String 클래스
C언어에서는 문자열을 char형 배열로 표현하지만, 자바에서는 문자열을 위한 String이라는 클래스를 별도로 제공합니다.

String 클래스에는 문자열과 관련된 작업을 할 때 유용하게 사용할 수 있는 다양한 메소드가 포함되어 있습니다.

이러한 String 클래스는 java.lang 패키지에 포함되어 제공됩니다.

 

String 인스턴스는 한 번 생성되면 그 값을 읽기만 할 수 있고, 변경할 수는 없습니다.

이러한 객체를 자바에서는 불변 객체(immutable object)라고 합니다.

즉, 자바에서 덧셈(+) 연산자를 이용하여 문자열 결합을 수행하면, 기존 문자열의 내용이 변경되는 것이 아니라 내용이 합쳐진 새로운 String 인스턴스가 생성되는 것입니다.

charAt() 메소드
charAt() 메소드는 해당 문자열의 특정 인덱스에 해당하는 문자를 반환합니다.

만약 해당 문자열의 길이보다 큰 인덱스나 음수를 전달하면, IndexOutOfBoundsException 오류가 발생합니다.

 

다음 예제는 문자열의 각 문자를 charAt() 메소드를 이용하여 하나씩 출력하는 예제입니다.

예제
String str = new String("Java");

System.out.println("원본 문자열 : " + str);

 

for (int i = 0; i < str.length(); i++) {

    System.out.print(str.charAt(i) + " ");

}

System.out.println("\ncharAt() 메소드 호출 후 원본 문자열 : " + str);

코딩연습 ▶

실행 결과
원본 문자열 : Java

J a v a 

charAt() 메소드 호출 후 원본 문자열 : Java

compareTo() 메소드
compareTo() 메소드는 해당 문자열을 인수로 전달된 문자열과 사전 편찬 순으로 비교합니다.

이 메소드는 문자열을 비교할 때 대소문자를 구분하여 비교합니다.

만약 두 문자열이 같다면 0을 반환하며, 해당 문자열이 인수로 전달된 문자열보다 작으면 음수를, 크면 양수를 반환합니다.

 

만약 문자열을 비교할 때 대소문자를 구분하지 않기를 원한다면, compareToIgnoreCase() 메소드를 사용하면 됩니다.

 

다음 예제는 compareTo() 메소드와 compareToIgnoreCase() 메소드를 이용하여 두 문자열을 비교하는 예제입니다.

예제
String str = new String("abcd");

System.out.println("원본 문자열 : " + str);

 

System.out.println(str.compareTo("bcef"));

System.out.println(str.compareTo("abcd") + "\n");

 

System.out.println(str.compareTo("Abcd"));

System.out.println(str.compareToIgnoreCase("Abcd"));

System.out.println("compareTo() 메소드 호출 후 원본 문자열 : " + str);

코딩연습 ▶

실행 결과
원본 문자열 : abcd

-1

0

32

0

compareTo() 메소드 호출 후 원본 문자열 : abcd

concat() 메소드
concat() 메소드는 해당 문자열의 뒤에 인수로 전달된 문자열을 추가한 새로운 문자열을 반환합니다.

만약 인수로 전달된 문자열의 길이가 0이면, 해당 문자열을 그대로 반환합니다.

 

다음 예제는 concat() 메소드를 이용하여 두 문자열을 연결하는 예제입니다.

예제
String str = new String("Java");

System.out.println("원본 문자열 : " + str);

 

System.out.println(str.concat("수업"));
System.out.println("concat() 메소드 호출 후 원본 문자열 : " + str);

코딩연습 ▶

실행 결과
원본 문자열 : Java

Java수업

concat() 메소드 호출 후 원본 문자열 : Java

indexOf() 메소드
indexOf() 메소드는 해당 문자열에서 특정 문자나 문자열이 처음으로 등장하는 위치의 인덱스를 반환합니다.

만약 해당 문자열에 전달된 문자나 문자열이 포함되어 있지 않으면 -1을 반환합니다.

 

다음 예제는 indexOf() 메소드를 이용하여 특정 문자나 문자열이 처음 등장하는 위치의 인덱스를 찾는 예제입니다.

예제
String str = new String("Oracle Java");

System.out.println("원본 문자열 : " + str);

 

System.out.println(str.indexOf('o'));

System.out.println(str.indexOf('a'));

System.out.println(str.indexOf("Java"));

System.out.println("indexOf() 메소드 호출 후 원본 문자열 : " + str);

코딩연습 ▶

실행 결과
원본 문자열 : Oracle Java

-1

2

7

indexOf() 메소드 호출 후 원본 문자열 : Oracle Java

 

위의 예제처럼 indexOf() 메소드는 문자나 문자열을 찾을 때 대소문자를 구분합니다.

trim() 메소드
trim() 메소드는 해당 문자열의 맨 앞과 맨 뒤에 포함된 모든 공백 문자를 제거해 줍니다.

 

다음 예제는 trim() 메소드를 이용하여 문자열에 포함된 띄어쓰기와 탭 문자를 제거하는 예제입니다.

예제
String str = new String(" Java     ");

System.out.println("원본 문자열 : " + str);

 

System.out.println(str + '|');

System.out.println(str.trim() + '|');

System.out.println("trim() 메소드 호출 후 원본 문자열 : " + str);

코딩연습 ▶

실행 결과
원본 문자열 :  Java

  Java        |

Java|

trim() 메소드 호출 후 원본 문자열 :  Java

toLowerCase()와 toUpperCase() 메소드
toLowerCase() 메소드는 해당 문자열의 모든 문자를 소문자로 변환시켜 줍니다.

또한, toUpperCase() 메소드는 해당 문자열의 모든 문자를 대문자로 변환시켜 줍니다.

 

다음 예제는 toLowerCase() 메소드와 toUpperCase() 메소드를 이용하여 문자열의 대소문자를 변경하는 예제입니다.

예제
String str = new String("Java");

System.out.println("원본 문자열 : " + str);

 

System.out.println(str.toLowerCase());

System.out.println(str.toUpperCase());

System.out.println("두 메소드 호출 후 원본 문자열 : " + str);

코딩연습 ▶

실행 결과
원본 문자열 : Java

java

JAVA

두 메소드 호출 후 원본 문자열 : Java

대표적인 String 메소드
String 클래스의 메소드는 매우 다양하며, 그중에서 많이 사용되는 메소드는 다음과 같습니다.

메소드	설명
char charAt(int index)	
해당 문자열의 특정 인덱스에 해당하는 문자를 반환함.

int compareTo(String str)	
해당 문자열을 인수로 전달된 문자열과 사전 편찬 순으로 비교함.

int compareToIgnoreCase(String str)	해당 문자열을 인수로 전달된 문자열과 대소문자를 구분하지 않고 사전 편찬 순으로 비교함.
String concat(String str)	
해당 문자열의 뒤에 인수로 전달된 문자열을 추가한 새로운 문자열을 반환함.

int indexOf(int ch)

int indexOf(String str)

해당 문자열에서 특정 문자나 문자열이 처음으로 등장하는 위치의 인덱스를 반환함.

int indexOf(int ch, int fromIndex)

int indexOf(String str, int fromIndex)

해당 문자열에서 특정 문자나 문자열이 전달된 인덱스 이후에 처음으로 등장하는 위치의 인덱스를 반환함.
int lastIndexOf(int ch)	해당 문자열에서 특정 문자가 마지막으로 등장하는 위치의 인덱스를 반환함.
int lastIndexOf(int ch, int fromIndex)	해당 문자열에서 특정 문자가 전달된 인덱스 이후에 마지막으로 등장하는 위치의 인덱스를 반환함.
String[] split(String regex)	해당 문자열을 전달된 정규 표현식(regular expression)에 따라 나눠서 반환함.
String substring(int beginIndex)	해당 문자열의 전달된 인덱스부터 끝까지를 새로운 문자열로 반환함.
String substring(int begin, int end)	해당 문자열의 전달된 시작 인덱스부터 마지막 인덱스까지를 새로운 문자열로 반환함.
String toLowerCase()	해당 문자열의 모든 문자를 소문자로 변환함.
String toUpperCase()	해당 문자열의 모든 문자를 대문자로 변환함.
String trim()	해당 문자열의 맨 앞과 맨 뒤에 포함된 모든 공백 문자를 제거함.
length()	해당 문자열의 길이를 반환함.
isEmpty()	해당 문자열의 길이가 0이면 true를 반환하고, 아니면 false를 반환함.
