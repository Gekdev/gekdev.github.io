---
layout: default
title: Filter
parent: JSP
nav_order: 14
has_children: true
---

# JSP Filter
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Filter

### What is Filter?

**JSP/Servlet에서 요청이 들어오면 요청 이전에 이 요청이 올바른지 또는 특정 장원에 접근권한의 여부를 사전에 처리 하는것**

&#8594; 즉, HTTP의 request와 response를 변경할 수 있는 클래스임

&#9656; 클라이언트의 요청이 웹 서버의 서블릿, JSP, HTML 페이지 같은 정적리소스에 도달하기 전과, 반대로 정적 리소스에서 클라이언트로 응답하기 전에 필요한 전처리를 가능하게 함

&#9656; 필터는 HTTP 요청과 응답을 변경할 수 있는 코드로 재사용 가능

&#9656; 클라이언트와 정적 리소스 사이에 여러 개의 필터로 이루어진 필터 체인을 제공하기도 함

![](https://gekdev.github.io/docs/jsp/example/filter.png)

필터의 기능
{: .label .label-red .mt-2}

| 필터 | 기능 |
|:-----|:-----|
| Requset 필터 | 인증(사용자 인증), 요청 정보를 로그 파일로 작성, 암호화 인코딩 작업 | 
| Response 필터 | 응답 결과 데이터 압축, 응답 결과에 내용 추가/수정, 총 서비스 시간 측정 |

### Filter 구현 클래스들

&#9656; 필터를 구현하기 위해서는 3개의 핵심 클래스가 필요함

1. javax.servlet.Filter 인터페이스 : 웹브라우저와 최종자원사이에 위치하는 필터를 구현하는 객체가 상속하는 인터페이스

2. javax.servlet.ServletRequestWrapper : 필터가 요청한 결과를 저장하는 클래스

3. javax.servlet.ServletResponseWrapper : 필터가 응답한 결과를 사용하는 클래스

---

## Filter 인터페이스

### What is Filter Interface?

**필터 기능을 구현하는데 핵심적인 역할**

&#9656; 클라이언트와 서버의 리소스 사이에 위치한 필터의 기능을 제공하기 위해 자바 클래스로 구현해야 함

syntax
{: .label .mt-2}
```java
import javax.servlet.Filter;

public class 클래스이릅 implements Filter{
    ...
}
```

Filter 인터페이스 메서드
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
* init() : 필터를 초기화할 때 호출

* doFilter() : 필터 기능을 수행, chain()메서드를 이용해서 다음 필터로 이동

* destory() : 필터가 웹컨테이너에서 삭제될 때 호출
</div>

### Filter 구현절차

1. init()을 호출해서 초기화 작업을 수행

2. doFilter()

    1) request파라미터를 이용해서 요청의 필터작업을 수행

    2) chain.doFilter(req, res)를 이용해 체인의 다음 필터를 수행

    3) response를 이용해서 응답의 필터링 작업을 수행

3. destory() : 필터가 사용하는 자원들을 반납

### init() Method

**JSP 컨테이너가 필터를 초기화할 때 호출되는 메소드**

&#9656; JSP 컨테이너 내에서 초기화 작업을 수행할 필터 인스턴스를 생성한 후 한 번만 호출

&#9656; JSP 컨테이너에 의해 호출되어 필터 서비스가 시작되고 있음을 나타냄

syntax
{: .label .mt-2}
```java
public void init(FilterConfig filterConfig) throws ServletException
```

![](https://gekdev.github.io/docs/jsp/example/initmethod.png)

### doFilter() Method

**JSP 컨테이너가 필터를 리소스에 적용할 때마다 호출되는 메소드**

&#9656; init() 메소드 후에 호출되며, 필터가 어떤 기능을 수행할 필요가 있을 때마다 호출

syntax
{: .label .mt-2}
```java
public void dofilter(ServletRequest requset,
                     ServletResponse response,
                     FilterChain chain) throws java.io.IOException, ServletException
```
<div class="code-example" markdown="1">
&#9656; 첫 번째 매개변수 ServletRequest 객체는 체인을 따라 전달하는 요청

&#9656; 두 번째 매개변수 ServletResponse 객체는 체인을 따라 전달하는 응답

&#9656; 세 번째 매개변수 FilterChain 객체는 체인에서 다음 피렅를 호출하는데 사용. 만약 호출 필터가 체인의 마지막 필터의 끝에서 리소스를 호출
</div>

![](https://gekdev.github.io/docs/jsp/example/dofilter.png)

### destory() Method

**필터 인스턴스를 종료하기 전에 호출하는 메소드**

&#9656; JSP 컨테이너가 필요 인스턴스턴스를 삭제하기 전에 청소 작업을 수행하는 데 사용되며, 이는 필터로 열린 리소스를 모두 닫을 수 있는 방법

&#9656; destory() 메소드는 필터의 수명 동안 한 번만 호출

syntax
{: .label .mt-2}
```java
public void destroy()
```

---

## web.xml 파일의 필터 구성

### web.xml 파일에 필터를 설정

**필터를 사용하려면 어떤 필터가 어떤 필터가 어떤 리소스에 대해 적용되는지 JSP 컨테이너에 알려주어야 함**

&#9656; `<filter>`와 `<filter-mapping>` 요소를 사용

&#9656; web.xml 파일에 여러 개의 필터가 설정되어 있으면 선언된 순서대로 실행

web.xml 필터의 요소들
{: .label .label-red .mt-2}

| 요소 | 하위요소 | 설명 |
|:-----|:---------|:-----|
| `<filter>` | <filter-name> | 필터의 이름을 설정 |
| | <filter-class> | 자바 클래스의 이름을 설정 |
| | <init-param> | 매개변수와 값을 설정 |
| <filter-Mapping> | <filter-name> | 필터 이름을 설정 |
| | <url-pattern> | URL 패턴을 설정 |


