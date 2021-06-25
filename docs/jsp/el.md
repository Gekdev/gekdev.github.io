---
layout: default
title: Expression Language
parent: JSP
nav_order: 6
has_children: true
---

# JSP Expression Language
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Expression Language, EL

### What is Expression Language?

**${와 }사이에 정해진 문법을 따르는 식을 입력**

JSP 스크립트 코드를 사용하는 것보다 표현 언어를 사용하는 것이 코드를 간결하고 이해하기 좋게 만들어주기 때문에 특별한 이유가 없는 한 표현 언어를 주로 사용함

## Expression Language, EL

표현언어

표현언어는 다른 형태의 스크립트 언어로서 스크립트 요소 중 하나

표현언어는 표현식보다 간결하고 코딩하기가 편하기 때문에 많이 사용함

EL은 JSTL(JSP Standard Tag Library) 규약에 나오는 내용으로서 JSP2.0부터 EL이 JSP에 포함됨

EL은 값을 표현하는데 사용하는 언어로서 JSP의 스크립트 요소를 보완하는 역할

### EL의 기능

1. JSP의 네가지 기본 객체가 제공하는 영역의 속성

2. 수치 연산자, 관계 연산자, 논리 연산자를 제공

3. 자바 클래스의 메서드 호출가능

4. 쿠키, 기본객체의 속성 등 JSP를 위한 표현언어의 기본 객체를 제공

5. 람다식을 이용한 함수의 정의와 실행(ES3.0)

6. 스트림 API를 통한 컬렉션 처리(EL3.0)

7. 정적 메서드 실행가능(EL3.0)

### EL의 구성

"${ 표현식 }"의 형태로 사용

EL은 JSP의 스크립트 요소(스크립트릿, 표현식, 선언부)를 제외한 나머지 부분에서 사용할 수 있음

JSP2.1버전 부터는 ${expr}형식과 #{expr}형식의 구문을 지원하고 있는데 차이점은 실제로 EL의 값을 언제 생성하느냐에 차이가 있음

${expr}은 구문을 분석할 때 곧바로 값을 계산하지만 #{expr}은 실제로 값이 사용될 때 계산이 됨
   
### EL의 데이터타입

1. Boolean

2. 정수 : EL에서 정수타입은 java.lang.Long 타입
    
3. 실수 : EL에서 실수타입은 java.lang.Double 타입

4. 문자열 : 작은 따옴표, 큰 따옴표, \의 문자는 이스케이프 문자로 사용해야 함 

5. null

### EL의 기본객체

| 기본객체          | 설명                                                                              |
| pageContext       | JSP의 page 기본객체와 동일                                                        |
| pageScope         | pageContext객체에 저장된 속성의 Map객체(<속성, 값>)                               |
| requestScope      | request객체에 저장된 속성의 Map객체(<속성, 값>)                                   |
| sessionScope      | session객체에 저장된 속성의 Map객체(<속성, 값>)                                   |
| applicaionScope   | application객체에 저장된 속성의 Map객체(<속성, 값>)                               |
| param             | 요청 파라미터의 <이름, 값>의 Map객체, request.getParameter()와 동일               |
| paramValues       | 요청 파라미터의 <이름, 값배열>의 Map객체, request.getParameterValues()와 동일     |
| header            | 요청 파라미터의 <헤더이름, 값>의 Map객체, request.getHeader()와 동일              |
| headerValues      | 요청 파라미터의 <헤더이름, 값배열>의 Map객체, request.getHeaders()와 동일         |
| cookie            | <쿠키이름, Cookie>의 Map객체, request.getCookies()와 동일                         |
| initParam         | 초기화파라미터<이름,값>의 Map객체, application.getInitParameter()와 동일          |

### 객체 사용

EL 언어는 객체에 저장된 값에 접근할 때 dot(.) or 대괄호([])를 사용함

<표현>.<표현> or <표현>[표현]형식으로 접근

#### 객체 접근과정

1. <표현>을 <값>의 형태로 변환

2. <값>이 null일 경우 null값을 리턴

3. <값1>이 null이 아닐경우 <표현2>의 <값2>를 반환

4. <값1>이 Map, List, 배열일 경우

    1. <값1>이 Map일 경우
    
        1. <값1>.containKey(<값2>)이 false이면 null
        
        2. 아니면 <값1>.get(<값2>)
    
    2. <값1>이 List, 배열일 경우

        <값2>가 정수값인지 여부를 겁사(정수가 아니면 에러 발생)

        <값1>.get(<값2>) or Arrays.get(<값1>, <값2>) 결과를 리턴

5. <값1>이 다른 객체일 경우

    값2를 문자열로 리턴
    
### EL의 연산자

1. 수치 연산자 : +, -, *, /, %

    예를들어 ${"10" + 1} 결과는 11 (자바는 101)

    ${"일" + 1}의 결과는 에러발생 (자바는 일1)
    
    ${null + 1}의 결과는 1
    
2. 비교 연산자 : ==, !=, <, <=, >, >=

3. 논리 연산자 : &&, ||, !

4. empty연산자 : empty<값>의 형태로 사용

5. 삼항연산자 : 수식 ? 값1 : 값2

6. 세미콜론(;) 연산자 

    ${1+1; 10+10}의 결과는 20만 출력 즉 ${A;B}의 EL결과는 B값만 출력
    
    ${var = 10}의 결과는 10으로 출력
