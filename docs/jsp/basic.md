---
layout: default
title: Basic
parent: JSP
nav_order: 2
has_children: true
---

# JSP Basic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSP

### Web Programming Language, JSP

웹 프로그래밍 언어는 클라이언트 측 실행 언어와 서버 측 실행 언어로 구분

자바를 기반으로 하는 JSP는 서버 측 웹 프로그래밍 언어 중 하나

### Why Use JSP?

원래 자바를 기반으로 하는 서버 측 프로그래밍 방식인 서블릿을 먼저 개발했으나, 서블릿 개발 방식이 쉽지 않아 HTML 코드에 직접 삽입할 수 있도록 개발된 기술이 JSP임

&#8594; 실제로 웹 애플리케이션 서버에서 클라이언트에게 서비스 될 때는 JSP가 서블릿으로 변경됨

### Features of JSP

1. JSP는 서블릿 기술의 확장

    &#9656; JSP에서는 서블릿의 모든 기능을 사용 가능
    
    &#9656; 서블릿과 마찬가지로 API를 사용할 수 있음

    (= API : JDBC, JNDI, EJB 등을 모두 포함하고 있는 강력한 엔터프라이즈 자바)

    &#9656; 쉽게 개발할 수 있도록 JSP에서는 내장 객체, 미리 정의된 태그, 표현식 언어와 사용자 정의 태그를 사용할 수 있음
    
2. JSP는 유지 관리가 용이

    &#9656; 서블릿 기술에는 프레젠테이션 로직과 비스니스 로직이 섞여있음

    &#9656; JSP 기술의 경우 프레젠테이션 로직과 비즈니스 로직을 분리할 수 있기 때문에 관리가 쉬움

3. JSP는 빠른 개발이 가능

    &#9656; 코드를 수정했을 때 서블릿에서는 업데이트를 하고 다시 컴파일 해야함

    &#9656; JSP의 경우 다시 컴파일하고 프로젝트를 배포할 필요가 없음

4. JSP로 개발하면 코드 길이를 줄일 수 있음

    &#9656; JSP에서는 액션 태그, JSTL(JavaServer Pages Standard Tag Library), 사용자 정의 태그 등의 다양한 태그와 표현 언어, 내장 객체 등을 사용함으로써 서블릿보다 코드를 줄일 수 있음

### Processing of JSP Pages

**JSP 페이지의 처리 과정**

JSP 페이지는 하나의 서블릿 프로그램으로 변환되어 실행

1. 웹 브라우저가 웹 서버에 JSP를 요청. 웹 서버는 요청된 Hello-jsp에서 jsp 확장자를 발견하여 JSP 페이지임을 확인하고 웹 서버에 있는 JSP 컨테이너에 전달

2. JSP 컨테이너는 JSP 페이지를 서블릿 프로그램인 Hello_jsp.java로 변환

3. JSP 컨테이너가 서블릿 프로그램을 컴파일하여 Hello_jsp.class로 만들고 이를 웹 서버에 전달

4. 웹 서버는 정적 웹 페이지처럼 *.class의 실행 결과를 웹 브라우저에 응답으로 전달하므로 웹 브라우저는 새로 가공된 HTML 페이지를 동적으로 처리한 결과를 보여줌

![](https://gekdev.github.io/docs/jsp/basic/example/proc.png)

웹 컨테이너(Web Container)
{: .label .mt-2}
<div class="code-example" markdown="1">
- JSP와 서블릿을 실행할수 있는 프로그램으로 서블릿 컨테이너 라고도 불림

- 웹 서버에서 JSP를 요청하면 톰캣에서는 JSP 파일을 서블릿으로 변환하여 컴파일을 수행하고, 서블릿의 수행 결과를 웹 서버에 전달함

- 서블릿 컨테이너의 개념과 동일한 JSP 컨테이너가 탑재되어 있는 WAS(Web Application Server)는 JSP 페이지를 컴파일하여 동적 페이지를 생성
</div>

### JSP Life Cycle

JSP 페이지를 컴파일한 *.class에는 jspInit( ), _jspService( ), jspDestroy( ) 메소드가 존재하며, JSP 생성부터 파괴까지의 과정에서 다음과 같은 역할을 수행함

![](https://gekdev.github.io/docs/jsp/basic/example/life.png)

1. 번역(translation) 단계

    &#9656; JSP 컨테이너가 JSP 소스 파일을 자바 코드(서블릿)로 변환

    &#9656; 번역 단계에서 JSP 컨테이너는 JSP 파일을 일고 구문을 분석함

    &#9656; JSP 컨테이너는 JSP 페이지와 페이지에 사용된 태그 라이브러리를 참조하는 사용자 정의 태그와 표준 디렉티브, 액션 태그의 구문 정확성을 검증함

2. 컴파일(Compilation) 단계

    &#9656; JSP 컨테이너가 번역 단계에서 생성된 자바 코드인 서블릿을 컴파일하여 클래스 파일을 생성함

    &#9656; 컴파일 단계에서는 자바 코드의 모든 구문을 검사함

    &#9656; JSP 내의 선언문, 처리문, 표현문 등의 스크립트 태그를 사용하여 삽입된 자바 코드의 구문 오류를 검사

3. 로딩(loading) 및 초기화(initialization) 단계

    &#9656; JSP 컨테이너가 앞의 두 단계에서 생성된 *.class를 로디아고 클래스의 인스턴스를 작성

    &#9656; JSP 컨테이너는 서블릿의 init( ) 메서드, 즉 jspInit( )를 호출하여 인스턴스가 된 객체를 초기화

    &#9656; 일반적으로 초기화는 한 번만 수행되고 데이터베이스 연결, 파일 열기, 룩업 테이블 생성 등을 초기화함

4. 실행(execution) 단계

    &#9656; 각 클라이언트의 요청에 대해 JSP 컨테이너가 요청 및 응답 객체를 전달하는 _jspService( ) 메서드를 실행함

    &#9656; JSP 생명 주기가 끝날 때까지 모든 클라이언트의 요청에 대해 상호 작용을 함

5. 소멸(destruction) 단계

    &#9656; JSP 생명 주기를 완료함

    &#9656; JSP 컨테이너는 실행되고 있는 JSP를 jspDestroy( ) 메서드를 사용하여 제거함

    &#9656; jpsDestroy( ) 메서드는 서블릿의 destroy( ) 메서드에 해당

    &#9656; 데이터베이스 연결 해제 또는 열려 이쓴 파일 닫기 등을 수행해야 할 때 jspDestroy( ) 메서드를 오버라이딩함

    &#9656; JSP 컨테이너가 해당 서블릿 인스턴스를 제거할 떄 어떤 활동을 정리하기 위해 jspDestroy( ) 메서드를 호출함

note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
jspInit( )와 jspDestroy( ) 메서드는 컨테이너가 기본 기능을 제공하기 때문에 오버라이딩이 선택 사항이지만, 기본적으로 _jspService( ) 메서드는 컨테이너가 추가하기 때문에 오버라이딩할 수 없음
</div>