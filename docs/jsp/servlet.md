---
layout: default
title: Servlet
parent: JSP
nav_order: 12
has_children: true
---

# JSP Servlet
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Servlet Basic

### What is Servlet?

JSP 표준이 나오기 전에 만들어진 표준

자바로 웹 어플리케이션을 개발할 수 있도록 하기 위해 만들어짐

서블릿을 이용하면 자바 클래스를 이용해서 웹 어플리케이션을 개발하게 됨

서블릿 컨테이너가 클라이언트 요청을 처리하기 위해 객체에 대해 호출하는 메서드의 규칙

클라이언트 요청을 처리하는 클래스를 만들 때는 반드시 이 규칙에 따라 만들어야 함

이 규칙에 따라 만든 클래스를 '서블릿(Servlet)'이라고 부름

아파치 톰켓 서버를 가져오지 않으면 사용할 수 없음

### Development of Servlet

1. 서블릿 규약에 따라 자바 코드를 작성

2. 자바 코드를 컴파일 해서 클래스 파일을 생성

3. 클래스 파일을 /WEB-INF/classes 폴더에 패키지에 알맞게 위치시킴

4. web.xml 파일에 서블릿 클래스를 설정

5. 톰캣 등의 컨테이너를 실행

6. 웹 브라우저에서 확인

### Why Use Servlet?

JSP와 비교하면 몇가지 과정이 더 들어가기 때문에 복잡해서 JSP를 더 많이 사용함

**하지만 MVC패턴을 지원하는 프레임워크를 만들어야 하는 경우 서블릿으로 기반 코드를 개발하는 경우가 많음**

따라서 서블릿 코드를 직접 구현하지는 않더라도 웹 개발을 배울 때 서블릿 자체에 대해서 이해하는 것은 중요함

---

## Create Servlet

### Servlet Implementation Method

**서블릿 구현 방법**

1. 서블릿 클래스를 구현하려면 먼저 HttpServlet 클래스를 상속받은 클래스를 작성해야 함
    
    ```java
    public class HelloWorld extends HttpServlet
    ```

2. 처리하고자 하는 HTTP 방식에 따라 알맞은 메서드를 재정의 해서 구현해야 함

    GET방식의 요청을 처리 : doGet() 메서드 재정의
    
    doGet()은 HttpServletRequest와 HttpServletResponse의 두 파라미터를 갖는데 이 두 파라미터는 각각 JSP의 request 기본 객체와 response기본객체에 해당

    ```java
    @Override
	protected void doGet(HttpServletRequest request, HttpServletResponse response) 
			throws ServletException, IOException {
    ```
    
3. 재정의한 메서드는 request를 이용해서 웹 브라우저의 요청 정보를 읽어오거나 response를 이용해서 응답을 전송

    응답을 전송하려면 먼저 response.setContentType() 메서드를 이용해 응답의 컨텐츠 타입을 지정해야 함
    
    ```java
    response.setContentType("text/html; charset=UTF-8");
    ```
    
4. 응답의 컨텐츠 타입을 지정했다면 실제로 응답 결과를 웹 브라우저에 전송

    웹 브라우저에 데이터를 전송하려면 response.getWriter() 메서드로 문자열 데이터를 출력할 수 있는 PrintWriter를 구해야 함
    
    PrintWriter은 println() 메서드를 제공 : 전송할 응답 데이터를 웹브라우저에 전달(출력)
    
    ```java
    PrintWriter out = response.getWriter();
    out.println("<html>");
    ...
    ```

간단한 서블릿 모습 : HelloWorld.java
{: .label .label-purple .mt-2}
```java
package com.lec.servlet;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.Date;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class HelloWorld extends HttpServlet{
	
	@Override
	protected void doGet(HttpServletRequest req, HttpServletResponse resp) 
			throws ServletException, IOException {
		
		resp.setContentType("text/html; charset=UTF-8");
		//자바는 만들어줘야됨 jsp랑 다름
		PrintWriter out = resp.getWriter();
		out.println("<html>");
		out.println("<head><title>Current Time</title></head>");
		out.println("<body>");
		out.println("<p>안녕하세요?</p>");
		out.println("현재시간은 : " + new Date() + " 입니다");
		out.println("</body>");
		out.println("</html>");	
	}
}
```

서블릿 자바 코드를 직접 컴파일 하기
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
이클립스를 사용하면 이클립스가 알아서 서블릿 관련 클래스 패스를 잡아주고 자바 코드를 컴파일해서 컴파일 관련 부분을 신경쓰지 않아도 되지만, **직접 자바 코드를 작성하고 컴파일하면 서블릿 API를 클래스패스에 추가해야 함**

&#9656; **서블릿 관련 jar파일은 톰켓/lib/servlet-api.jar파일에 포함되어 있음**

&#9656; 다음 아래 코드는 컴파일 하는 과정 (webapps폴더의 chap17 폴더에 WEB-INF/src/sample/aaa.java 경로에 작성했다는 가정)

&#9656; 컴파일에 성공하면 WEB-INF\classes\example 폴더에 aaa.class파일이 생성된것을 확인할 수 있음
</div>
```java
c:\ cd apache-tomcat-8.0.21\webapps\chap17\WEB-INF
c:\...\ WEB-INF \ mkdir classes
c:\...\ WEB-INF \ set CLASSPATH=c:\apache-tomcat-8.0.21\lib\servlet-api.jar
c:\...\ WEB-INF \ set CLASSPATH=classes;%CLASSPATH%
c:\...\ javac -d classes src\example\aaa.java
```

### web.xml Mapping

서블릿 클래스를 생성했다면 **WEB-INF 폴더의 web.xml파일에 서블릿 클래스를 등록해야 함**

**서블릿을 등록하려면 서블릿으로 사용할 클래스, 서블릿과 URL간의 매핑 두가지를 설정해야 함**

1. 서블릿으로 사용할 클래스설정

    * <servlet> : 서블릿 클래스를 등록

    * <servlet-name> : 해당 서블릿을 참조할 때 사용할 이름

    * <servlet-class> : 서블릿으로 사용할 클래스의 완전한 이름

2. 서블릿과 URL간의 매핑 설정

    * <servlet-mapping> : 해당 서블릿이 어떤 URL을 처리할지에 대한 매핑 정보를 등록
    
    * <servlet-name> : 매핑할 서블릿의 이름을 지정 (servlet-name 태그와 동일하게 지정함)

    * <url-pattern> : 매핑할 URL 패턴을 지정
    
        한 번 이상을 사용할 수 있음, 이 경우 각각의 URL 패턴에 해당 서블릿을 매핑

web.xml의 모습
{: .label .label-purple .mt-2}
```xml
<servlet>
    <servlet-name>hello</servlet-name>
    <servlet-class>com.lec.servlet.HelloWorld</servlet-class>
</servlet>

<servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>/xxx</url-pattern>
    <url-pattern>/yyy</url-pattern>
</servlet-mapping>
```

### @WebServlet Mapping 

**서블릿 3.0부터 위의 방법을 사용하지 않고 @WebServlet 애노테이션을 사용하면 서블릿으로 등록됨**

서블릿 3.0을 지원하는 웹 컨테이는 @WebServlet이 적용된 클래스를 검색해서 서블릿으로 자동으로 등록

urlPatterns을 생략하고 사용할 수 있음 `@WebServlet(urlPatterns={ "/CurrentTime", "/now" })`

```java
package com.lec.servlet;
...
    
@WebServlet({ "/CurrentTime", "/now" })
public class CurrentTime extends HttpServlet {
```

### URL Pattern Mapping Rules

**URL 패턴 매핑 규칙**

servlet-mapping 태그는 url-pattern태그를 사용해서 서블릿과 url을 매핑하고, @WebServlet의 경우 urlPatterns속성을 이용해서 서블릿과 url을 매핑함

URL패턴은 다음 규칙에 따라 서블릿을 매핑함

* '/'로 시작하고 '/*'로 끝나는 url-pattern은 경로 매핑을 위해서 사용

* '*.'로 시작하는 url-pattern은 확장자에 대한 매핑을 할 떄 사용

* 오직 '/'만 포함하는 경우 어플리케이션의 기본 서블릿으로 매핑

* 이 규칙 외, 나머지 다른 문자열은 정확한 매핑을 위해서 사용

예시 매핑 규칙 
{: .label .lable-purple .mt-2}

| URL 패턴    | 매핑 서블릿 | 요청경로            | 
|:------------|:------------|:--------------------|
| /foo/bar/*  | servlet1    | /foo/bar/index.html |
|             |             | /foo/bar/index.bop  |
| /bax/*      | servlet2    | /baz                |
|             |             | /baz/index.html     |
| /catalog    | servlet3    | /catalog            |
| *.bop       | servlet4    | /catalog/race.bop   |
|             |             | /index.bop          |

### web.xml or @WebServlet?

**서블릿이 범용적으로 사용되는 서블릿인지의 여부에 따라 나뉨**

예를들어 MVC 프레임워크는 어떤 URL을 서블릿이 처리할지 미리 알 수 없음. 단지 다양한 요청 URL을 MVC프레임워크가 처리할 수 있는 기능을 구현할 뿐임

* @WebServlet 애노테이션을 사용할 경우 서블릿이 처리해야 할 URL 패턴이 변경될 때 마다, 자바 소스 코드의 urlPatterns 속성값을 변경하고 다시 컴파일해야 함

* web.xml파일을 사용하면 URL의 경로가 바뀌어도 web.xml파일만 변경하면됨

따라서 서블릿의 용도에 따라서 결정해야 함

@WebServlet 애노테이션이 적용된 서블릿을 web.xml파일에 등록한다면?
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
@WebServlet 애노테이션이 적용된 URL패턴과 web.xml 파일에 등록된 URL패턴에 모두 매핑됨

정확하게 말하면 @WebServlet애노테이션이 적용된 클래스의 객체가 생성되고, web.xml파일에서 지정한 클래스의 객체가 생성됨

**즉, 서로 다른 두 개의 객체가 생성되고 각각 @WebServlet 애노테이션에서 지정한 URL 패턴과 web.xml파일에 지정한 URL 패턴에 매핑됨**
</div>

### HTTP Implementation Method for Each Method

HTTP는 다양한 방식을 지원하지만 일반적으로 웹과 웹브라우저가 지원하는 방식은 GET, POST방식임

HttpServlet은 Http의 각 방식에 따라 알맞은 메서드를 이용해서 구현하도록 정의

두가지 모두 처리해야 한다면 둘다 재정의해서 알맞게 처리하면 됨

* GET방식 : doGet() 메서드를 이용해서 처리

    GET방식
    {: .label .label-purple .mt-2}
    ```java
    protected void doGet(HttpServletRequest request, HttpServletResponse response) 
			throws ServletException, IOException {
        ...// GET방식에 대한 처리. 예, 폼 출력하기
    }
    ```

* POST방식 : doPost()메서드를 이용해서 처리

    POST방식
    {: .label .label-purple .mt-2}
    ```java
    protected void doPost(HttpServletRequest request, HttpServletResponse response) 
			throws ServletException, IOException {
        ...// POST방식에 대한 처리. 예, 폼 출력하기
    }
    ```
    
### Servlet Loading and Initialization

서블릿 컨테이너는 처음 서블릿을 실행 할 떄 서블릿 객체를 생성함

![](https://gekdev.github.io/docs/jsp/example/servletloading.png)

위 그림과 같이 서블릿을 최초 요청할 때 서블릿 객체를 생성하고, 이후 요청이 오면 앞서 생성한 서블릿 객체를 그대로 사용

웹 컨테이너가 서블릿 객체를 생성하고 init()메서드를 호출하는 과정을 '서블릿 로딩' 과정이라고 함

서블릿 로딩 과정을 보면 init()메서드를 호출해서 필요한 초기화 작업을 수행함

init()메서드의 기본 구현
{: .label .label-purple .mt-2}
```java
// GenericServlet 구현
public void init(ServletConfig config) throws ServletException{
    this.config = config;
    this.init();
}

public void init() throws ServletException{}
```

서블릿 컨테이너는 서블릿을 초기화하기위해 ServletConfig 파라미터를 갖는 init()메서드를 실행함

init(ServletConfig config) 메서드는 다시 파라미터가 없는 init()메서드를 호출함

따라서 초기화가 필요한 서블릿은 파라미터가 없는 init()메서드를 재정의 하면 됨 (ServletConfig가 필요하면 있는걸로 재정의)

JDBC에서 DBCPInit에서 이미 해봤음!

DBCPInit : 커넥션 풀 초기화하는 서블릿 클래스
{: .label .label-purple .mt-2}
```java
package com.lec.web.jdbc;
...
    
public class DBCPInit extends HttpServlet {

    @Override
    public void init() throws ServletException {    //서블릿을 초기화할 때 사용
        loadJDBCDriver();
        initConnectionPool();
    }
}
```

#### load-on-startup Tag

보통 초기화 작업은 상대적으로 시간이 오래 걸리기 때문에 웹 컨테이너를 처음 구동하는 시점에 초기화를 진행하는게 좋음

이를 위한 설정이 load-on-startup 태그, DBCP 초기화를 위해 web.xml파일에 추가해야 함

load-on-startup 태그 값은 로딩 순서를 의미

값을 기준으로 오름차순으로 서블릿을 로딩(1,2,3 순서)

@WebServlet 태그를 사용하는 경우에는 loadOnStartUp 속성을 이용해 로딩값을 지정

web.xml: load-on-startup
{: .label .label-purple .mt-2}
```xml
<servlet>
    <servlet-name>DBCPInit</servlet-name>
    <servlet-class>jdbc.DBCPInit</servlet-class>
    <load-on-startup>1</load-on-startup>
</servlet>
```

![](https://gekdev.github.io/docs/jsp/example/load.png)

### Initialization Parameters

수정해야 하는 클래스가 자바 클래스 안에 있을 경우 수정하기 불편함

서블릿은 코드를 직접 수정하지 않고 초기화 과정에서 필요한 값을 수정할 수 있는 초기화 파라미터 방법을 제공

web.xml의 <init-param> 태그를 이용해 서블릿을 초기화 할 떄 필요한 값을 전달하는 방법을 제공함

* <init-param> : 서블릿의 초기화 파라미터를 지정할 떄 사용

* <param-name> : 초기화 파라미터의 이름을 지정

* <param-value> : 초기화 파라미터의 값을 지정

web.xml : 초기화 파라미터 예시
{: .label .label-purple .mt-2}
```xml
  <servlet>
     <servlet-name>DBCPInit</servlet-name>
     <servlet-class>com.lec.web.jdbc.DBCPInit</servlet-class>
     
     <init-param>
        <param-name>jdbcdriver</param-name>
        <param-value>org.mariadb.jdbc.Driver</param-value>
     </init-param>
     
     <init-param>
        <param-name>url</param-name>
        <param-value>jdbc:mariadb://localhost:3306/guestbook</param-value>
     </init-param>
     
     <init-param>
        <param-name>user</param-name>
        <param-value>root</param-value>
     </init-param>
     <init-param>
        <param-name>pass</param-name>
        <param-value>12345</param-value>
     </init-param>
     
     <init-param>
        <param-name>poolName</param-name>
        <param-value>guestbook</param-value>
     </init-param>
     
     <load-on-startup>1</load-on-startup>
  </servlet>
```

아래와 같이 사용하면 됨

DBCPInit
{: .label .label-purple .mt-2}
```java
private void initConnectionPool() {
    String url =  getInitParameter("url");
    String usr =  getInitParameter("user");
    String pwd =  getInitParameter("pass");
   ...
}
```

JDBC URL이나 다른 설정을 바꾸려면 서블릿을 변경할 필요 없이 web.xml파일의 초기화 파라미터 값을 변경하면 됨

예를들어 커넥션 풀의 이름을 변경하고 싶다면 poolName 초기화 파라미터 값을 다른 이름으로 변경한 후 톰캣을 재시작 하면됨

초기화 파라미터가 없다면 null을 리턴함

```java
String poolName = getInitParameter("poolName");
if(poolName == null) poolName = "pool";
```

#### @WebInitParam

@WebServlet 애노테이션으로 매핑한 경우 web.xml파일에서 init-param 속성을 지정했던것 처럼 초기화 파라미터를 전달하려면 initParams 속성값으로 @WebInitParam 애노테이션 목록을 전달하면 됨

소스코드에서 수정하는거라서 초기화 설정을 변경할 때 마다 자바 코드를 수정해야 하기 때문에 귀찮음 = 거의 사용 안함

@WebInitParam 예시
{: .label .label-purple .mt-2}
```java
import javax.servlet.annotation.WebInitParam;
...
    
@WebServlet
(urlPatterns="/yyy", 
    initParams = 
        {@WebInitParam(name="user", value="root"),
         @WebInitParam(name="pass", value="12345")})
```
