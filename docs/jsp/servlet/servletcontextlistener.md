---
layout: default
title: ServletContextListener
parent: Servlet
grand_parent : JSP
nav_order: 1
---

# ServletContextListener
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## ServletContextListener 구현하기

서블릿은 다양한 시점에서 발생하는 이벤트와 이벤트를 처리하기 위한 인터페이스를 정의

이들 이벤트와 인터페이스를 이용하면 웹 어플리케이션에서 필요로 하는 데이터의 초기화나 요청 처리 등을 추적할 수 있게 됨

서블릿 규약은 다양한 이벤트를 처리할 수 있는 인터페이스를 정의하는데 여기는 그 중 ServletContextListener인터페이스의 활용법을 설명함

### ServletContextLisenter를 이용한 이벤트 처리

웹 컨테이너는 웹 어플리케이션(컨텍스트)이 시작되거나 종료되는 시점에 특정 클래스의 메서드를 실행할 수 있는 기능을 제공함

이 기능을 사용하면 웹 어플리케이션을 실행할 때 필요한 초기화 작업이나 웹 어플리케이션이 종료된 후 사용된 자원을 반환하는 등의 작업을 수행할 수 있음

웹 어플리케이션이 시작되고 종료될 때 특정한 기능을 실행하려면 다음과 같이 코드를 작성하면 됨

1. javax.servlet.ServletContextListener 인터페이스를 구현한 클래스를 작성
    
2. web.xml파일에 1번에서 작성한 클래스를 등록

### javax.servlet.ServletContextListener 인터페이스

웹 어플리케이션이 시작되거나 종료될 때 호출할 메서드를 정의한 인터페이스

두개의 메서드를 정의하고 있음

* public void contextInitialized(ServletContextEvent sce) : 웹 어플리케이션을 초기화할 때 호출

* public void contextDestroyed(ServletContextEvent sce) : 웹 어플리케이션을 종료할 때 호출

### web.xml

웹 어플리케이션이 시작되거나 종료될 떄 ServletContextListener 인터페이스를 구현한 클래스를 실행하려면 web.xml파일에 listener, listener-class 태그를 사용해서 완전한 클래스 이름을 명시하면 됨

한개 이상의 listener 태그를 등록할 수 있음

각 listener 태그는 반드시 한개의 listener-class 태그를 자식 태그로 가져야 함

listener-class 태그는 웹 어플리케이션의 시작/종료 이벤트를 처리할 리스터 클래스의 완전한 이름을 값을 갖음

```xml
<listener>
  		<listener-class>com.lec.servlet.DBCPInitListener</listener-class>
</listener>
```

### ServletContext Class

**톰캣 컨테이너 실행 시 각 컨텍스트(웹 애플리케이션)마다 한 개의 ServletContext객체를 생성**

톰캣 컨테이너가 종료하면 ServletContext객체 역시 소멸

웹 애플리케이션이 실행되면서 애플리케이션 전체의 공통 자원이나 정보를 미리 바인딩(binding)해서 서블릿들이 공유하여 사용

#### getServletContext() 메서드

ServletContextListener 인터페이스에 정의된 두 메서드는 모두 파라미터로 javax.servlet.ServletContextEvent 타입의 객체를 전달받음

ServletContextEvent클래스는 웹 어플리케이션 컨텍스트를 구할 수 있는 getServletContext()메서드를 제공

public ServletContext getServletContext() 메서드가 리턴하는 ServletContext 객체는 JSP의 application 기본객체와 동일한 객체

ServletContext 객체를 이용하면 web.xml파일에 설정된 컨텍스트 초기화 파라미터를 구할 수 있음

컨텍스트 초기화 파라미터는 context-param 태그를 사용해서 web.xml파일에 저장함

ServletContextListener를 이용해서 커넥션 풀을 초기화하는 클래스
{: .label .label-purple .mt-2}

```xml
<context-param>
    <param-name>dbConnect</param-name>
    <param-value>
        jdbcdriver=org.mariadb.jdbc.Driver
        url=jdbc:mariadb://localhost:3306/jspstudy
        user=root
        pass=12345
        poolName=guestbook
    </param-value>
</context-param>
```

#### 초기화 파라미터 값을 구하는데 사용되는 ServletContext의 메서드

주로 웹 어플리케이션의 초기화 작업을 수행하는데 필요한 값을 설정할 때 사용

* String getInitParameter(String name)

    **지정한 이름을 갖는 컨텍스트 초기화 파라미터의 값을 리턴**
    
    존재하지 않는 경우 null을 리턴
    
    name 파라미터에는 param-name태그로 지정한 이름을 리턴

* java.util.Enumeration<String> getInitParameterNames()

    컨텍스트 초기화 파라미터의 이름 목록을 Enumeration 타입으로 리턴

#### ServletContext클래스의 특징

* javax.servlet.ServletContext 로 정의 

* 서블릿과 컨테이너 간의 연동을 위해 사용

* 컨텍스트(웹 어플리케이션)마다 하나의 ServletContext가 생성

* 서블릿끼리 자원(데이터)을 공유하는 데 사용

* 컨테이너 실행시 생성되고 컨테이너 종료 시 소멸

#### ServletContext가 제공하는 기능

* 서블릿에서 파일 접근 기능

* 자원 바인딩 기능

* 로그 파일 기능

* 컨텍스트에서 제공하는 설정 정보 제공 기능

톰캣 컨테이너를 실행할 때 각 애플리케이션에서 생성되는 ServletContext와 ServletConfig 객체를 나타낸 그림
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
ServletContext는 컨텍스트당 생성되는 반면에 ServletConfig는 각 서블릿에 대해 생성

![](servletconfig.png)
</div>

---



### 리스너의 실행 순서

### 리스너에서의 익셉션 처리

### 애노테이션을 이용한 리스터 등록

---
