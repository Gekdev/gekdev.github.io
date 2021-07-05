---
layout: default
title: Processing
parent: Basic
grand_parent : JSP
nav_order: 2
---

# Basic Processing
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSP Processing

### Processing of JSP (Simple)

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

### WAS

**웹 어플리케이션 서버(Web Application Server)**

단순 웹 서버가 정적인 HTML파일이나 이미지를 제공하는 것과 달리 톰켓, 제티, JBoss EAP 웹서버와 같은 서버는 웹을 위한 연결, 프로그래밍 언어, 데이터베이스 연동과 같이 어플리 케이션을 구현하는데 필요한 기능을 제공하고 있음

WAS는 웹 브라우저로부터 요청이 오면 알맞은 프로그램을 찾아 실행하고 프로그램의 실행결과를 응답으로 전송

### Processing of JSP (Complicate)

&#9656; jsp 페이지를 요청할 때에는 JSP를 직접 실행하는 것이 아니라, JSP를 자바 소스코드로 변환한 뒤 컴파일 해서 생성한 서블릿을 실행하는 것

&#9656; 여기서 JSP페이지를 자바 코드로 변경하는 단계를 변환(translation)단계 [과정 1.2]라고 하며, 자바 코드를 서블릿 클래스로 변경하는 단계를 컴파일(compile)단계 [과정 1.3]이라고 함

★ 즉, jsp를 실행한다는 말은 jsp페이지를 컴파일한 결과 서블릿 클래스를 실행한다는 말과 동일함

&#8594; 정확하게 말한다면 jsp페이지를 컴파일 한 서블릿을 실행한다는 의미

JSP 페이지에 대한 요청의 WAS 처리
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/jsp/example/jspdispose.png)

*  **[과정 1.1] JSP에 해당하는 서블릿이 존재하지 않을 경우**

    1. [과정 1.2] JSP 페이지(hello.jsp)로부터 자바 코드(servlet)를 생성함 (Hello_jsp.java) : 변환 단계

    2. [과정 1.3] 자바 코드를 컴파일해서 서블릿 클래스 바이트 파일을 생성(Hello_jsp.class) : 컴파일 단계

    3. [과정 2.1] 서블릿에 웹브라우저(클라이언트)의 요청 request(파라미터와 값)을 전달

    4. [과정 2.2] 서블릿 처리결과를 응답

    5. [과정 3.3] 응답(response)을 웹 브라우저에 전달

* **[이미 과정1.1 ~ 1.3을 거친 경우] JSP에 해당하는 서블릿이 존재하는 경우**

    0. 위 1~2 과정을 건너뜀 (servlet이 있기 때문에)

    1. [과정 2.1] 서블릿에 웹브라우저(클라이언트)의 요청 request(파라미터와 값)을 전달

    2. [과정 2.2] 서블릿 처리결과를 응답

    3. [과정 3.3] 응답(response)을 웹 브라우저에 전달
</div>

#### work folder

**톰켓은 work 폴더에 JSP를 변환한 자바 소스 코드와 서블릿 클래스를 생성함**

```html
C:/apache-tomcat/work/Catalina/localhost/...
```

### JSP Life Cycle

JSP 페이지를 컴파일한 *.class에는 jspInit( ), _jspService( ), jspDestroy( ) 메소드가 존재하며, JSP 생성부터 파괴까지의 과정에서 다음과 같은 역할을 수행함

1. **변환(translation) 단계**

    &#9656; JSP 컨테이너가 JSP 소스 파일을 자바 코드(서블릿)로 변환

    &#9656; 번역 단계에서 JSP 컨테이너는 JSP 파일을 일고 구문을 분석함

    &#9656; JSP 컨테이너는 JSP 페이지와 페이지에 사용된 태그 라이브러리를 참조하는 사용자 정의 태그와 표준 디렉티브, 액션 태그의 구문 정확성을 검증함

2. **컴파일(Compilation) 단계**

    &#9656; JSP 컨테이너가 번역 단계에서 생성된 자바 코드인 서블릿을 컴파일하여 클래스 파일을 생성함

    &#9656; 컴파일 단계에서는 자바 코드의 모든 구문을 검사함

    &#9656; JSP 내의 선언문, 처리문, 표현문 등의 스크립트 태그를 사용하여 삽입된 자바 코드의 구문 오류를 검사

3. **로딩(loading) 및 초기화(initialization) 단계**

    &#9656; JSP 컨테이너가 앞의 두 단계에서 생성된 *.class를 로디아고 클래스의 인스턴스를 작성

    &#9656; JSP 컨테이너는 서블릿의 init( ) 메서드, 즉 jspInit( )를 호출하여 인스턴스가 된 객체를 초기화

    &#9656; 일반적으로 초기화는 한 번만 수행되고 데이터베이스 연결, 파일 열기, 룩업 테이블 생성 등을 초기화함

4. **실행(execution) 단계**

    &#9656; 각 클라이언트의 요청에 대해 JSP 컨테이너가 요청 및 응답 객체를 전달하는 _jspService( ) 메서드를 실행함

    &#9656; JSP 생명 주기가 끝날 때까지 모든 클라이언트의 요청에 대해 상호 작용을 함

5. **소멸(destruction) 단계**

    &#9656; JSP 생명 주기를 완료함

    &#9656; JSP 컨테이너는 실행되고 있는 JSP를 jspDestroy( ) 메서드를 사용하여 제거함

    &#9656; jpsDestroy( ) 메서드는 서블릿의 destroy( ) 메서드에 해당

    &#9656; 데이터베이스 연결 해제 또는 열려 있는 파일 닫기 등을 수행해야 할 때 jspDestroy( ) 메서드를 오버라이딩함

    &#9656; JSP 컨테이너가 해당 서블릿 인스턴스를 제거할 떄 어떤 활동을 정리하기 위해 jspDestroy( ) 메서드를 호출함

![](https://gekdev.github.io/docs/jsp/basic/example/life.png)

override method
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
jspInit( )와 jspDestroy( ) 메서드는 컨테이너가 기본 기능을 제공하기 때문에 오버라이딩이 선택 사항이지만, 기본적으로 _jspService( ) 메서드는 컨테이너가 추가하기 때문에 오버라이딩할 수 없음
</div>

---

## JSP Buffer

### Buffer Basic

jsp페이지는 응답결과를 곧바로 웹 브라우저에 전송하는 것이 아니라 출력 버퍼(buffer)에 임시로 저장했다가 한번에 웹 브라우저로 전달

버퍼 출력 장점

* 데이터 전송 성능 향상

    &#9656; 네트워크를 비롯한 모든 데이터 교환에서는 큰 단위로 데이터를 전송하는 것이 성능이 높음

* JSP 실행 도중에 버퍼를 비우고 새로운 내용 전송 가능

    &#9656; jsp:forward 기능과 에러 페이지 처리 기능이 가능함

    &#9656; JSP페이지가 생성한 결과를 일단 버퍼에 저장하기 때문에 버퍼에 보관된 데이터가 일정 크기가 될 때 까지 웹 브라우저에 전송되는 데이터는 없음

    &#9656; 따라서 JSP 페이지가 생성한 내용이 있다 하더라도 버퍼에 저장된 데이터가 웹 브라우저로 전송되기 전 까지는 버퍼에 보관된 데이터를 지우고 새로운 내용을 전송할 수 있음

    ex) JSP 실행과정에서 에러가 발생하면, 지금 까지 생성한 내용을 버퍼에서 지우고 에러 화면을 출력할 수 있음

* 버퍼가 다 차기 전까지는 헤더정보를 변경 가능

    &#9656; HTTP 프로토콜의 구조상 응답 상태 코드와 함께 헤더 정보를 가장 먼저 웹 브라우저에 전송해야 함. 이런 이유로 WAS는 처음 버퍼의 내용을 웹 브라우저로 전송하기 전에 헤더 정보를 전송함

    &#9656; 따라서 첫번째로 버퍼의 내용을 웹 브라우저에 전송하기 전까지는 헤더 정보를 얼마든지 변경할 수 있음

    &#9656; 하지만 일단 버퍼 내용이 웹 브라우저에 전송되면 그 이후로는 헤더 정보를 변경해도 적용되지 않음

![](https://gekdev.github.io/docs/jsp/example/buffer.png)

### buffer & autoFlush Property

page 디렉티브는 buffer, autoFlush 속성을 제공하고 있음

&#9656; **buffer속성 : JSP 페이지가 사용할 버퍼의 크기를 지정할 때 사용, 킬로바이트 단위로 버퍼 크기를 지정함**

&#9656; buffer를 사용하고 싶지 않다면 buffer="none"으로 지정하면 됨 

&#9656; none으로 지정한다면 jsp가 출력하는 내용을 즉시 웹브라우저로 전송하기 때문에 제약사항이 있음 (그래서 거의 사용 안함)

1. <jsp:forward> 기능을 사용할 수 없음

2. 곧바로 전송되기 때문에 출력한 내용을 취소할 수 없음

&#9656; autoFlush속성 : 버퍼가 다 찼을 때 어떻게 처리할지 결정

예제
{: .label .label-purple .mt-2}
```jsp
<%@ page buffer = "8kb" autoFlush= "true" %>
```

* autoFlush = "true" : 버퍼가 다 찼을 경우 버퍼를 플러시하고 계속해서 작업 진행

* autoFlush = "false" : 버퍼가 다 차면 익셉션을 발생시키고 작업을 중지

### Process of Buffer

![](https://gekdev.github.io/docs/jsp/example/buffer2.png)

위 그림의 3번 과정에서 출력 버퍼에 보관한 데이터를 웹 브라우저에 전송하는데, 이때 버퍼에 보관된 응답 데이터를 전송하기 전에 응답 상태 코드와 응답 헤더를 먼저 전송. 따라서 이후에는 응답 헤더값을 변경해도 웹 브라우저에 전송되지 않고 무시됨

위 3번 과정을 Flush(버퍼가 다 찼을 때 버퍼에 쌓긴 데이터를 실제로 전송해야 할곳에 전송하고 버퍼를 비우는 것)라고 함

note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
일반적으로 JSP페이지를 작성할 때에는 buffer속성을 지정하지 않음

JSP 규약은 buffer 속성을 지정하지 않으면 최소한 8kb 이상의 크기를 갖는 버퍼를 사용하도록 규약하고 있음
</div>

---

## Web Application Folder Structure and URL Mapping

JSP를 이용해서 웹 어플리케이션을 개발하려면 기초 문법 뿐만 아니라 웹 어플리케이션의 폴더 구조에 대해서도 알고 있어야 함

Servlet/JSP은 웹애플리케이션이 특정의 폴더 구조를 따르도록 강제화 함

이 구조를 모르면 제대로 동작하는 프로그램을 개발할 수 없게 됨

웹 어플리케이션 폴더는 WEB-INF폴더와 그 하위폴더를 포함함

Servlet/JSP의 기본폴더 구조
{: .label .mt-2}
<div class="code-example" markdown="1">
웹애플리케이션이름 &#8594; root &#8594; 
	
	... WEB-INF : 웹애플리케이션의 설정정보를 위치함, 대표적인 설정정보는 web.xml파일에 위치

	... WEB-INF \ classes : 웹애플리케이션에 사용하고 있는 클래스파일이 위치하는 폴더
	
	... WEB-INF \ lib : 웹애플리케이션에서 사용하는 jar파일이 위치하는 폴더
	
	... WEB-INF \ 사용자폴더 : css, js, jsp, html등 사용자가 사용하는 파일이 위치하는 폴더 
</div>

WEB-INF 폴더와 그 하위폴더를 제외한 나머지 폴더에는 웹 어플리케이션에서 사용할 JSP, HTML, 이미지 등의 파일이 위치함

web.xml
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
JSP 2.0에서는 web.xml파일을 반드시 포함하도록 제한하고 있었는데 JSP2.1부터 없어짐

따라서 2.1버전 이후를 사용한다면 web.xml파일을 작성하지 않아도 됨

**하지만 서블릿을 직접 설정하는 경우, 리스너를 직접 설정하는 경우, 특정 URL에 속하는 JSP들에 대해 공통 속성값을 설정하는 경우에는 web.xml파일을 직접 작성해야 함**
</div>

### Relationship between Web Application Folder and URL

한개의 웹 어플리케이션은 한개의 폴더를 차지함 (jsp01_...)

톰켓에서 웹 어플리케이션은 [톰켓]/webapps 폴더에 위치하고, 그 하위폴더는 자동으로 웹 어플리케이션에 포함됨

각 폴더의 이름은 웹 어플리케이션을 실행할 때 사용되는 URL과 관련이 있는데 context path를 따로 설정한 경우 폴더의 이름이 아니라 context path명으로 사용됨

**[톰켓]/webapps/[웹경로] = http://host:port[/웹경로]**

[톰켓]/webapps에는 root라는 특수 폴더가 존재하는데, root는 context path가 빈 문자열("")임

request.getContextPath() : 컨텍스트 경로를 얻을 수 있음

웹 어플리케이션의 경로 구하기
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">

</div>
```jsp
웹 어플리케이션 컨텍스트 경로 : <%=request.getContextPath()%>
```

### Using Subfolders within the Web Application Folder

JSP페이지가 너무 많아지면 관리하기 힘들어짐. 이 문제를 해결하는 쉬운 방법은 웹 어플리케이션 폴더 밑에 하위 폴더를 생성해서 JSP 페이지를 기능 별로 분류하는 것

하위 폴더를 사용하면 JSP 페이지를 알맞게 기능별로 분류할 수 있으므로 웹 어플리케이션을 구현할 때에는 하위 폴더를 적극적으로 사용하는 것이 개발 과정이나 유지 보수에 이로움

### Web Application Deployment

개발된 웹애플리케이션을 WAS에 배포하는 방법은 2가지가 있음

1. 개발된 폴더 그대로 파일을 WAS에 직접 복사

    예제를 실행할 때 이미 사용하는 방법!

    톰켓의 webapps/jsp01...과 같은 폴더에 직접 JSP 파일을 저장했는데, 이는 톰캣 서버의 특정 폴더에 파일을 직접 복사하는 방식을 사용한 것

2. war파일로 압축해서 배포하는 방법

    **war은 Web Application Archive의 약자로 웹 어플리케이션의 구성 요소를 하나로 묶어놓은 파일**

    war파일로 묶으려면 jdk의 jar.exe 명령어를 사용해서 war파일을 생성

    jar 명령어는 javac 명령어와 동일하게 JDK설치폴더/bin 폴더에 포함되어있음
    
    Path 환경변수에 JDK설치폴더/bin 폴더를 추가해주면 전체 경로를 입력할 필요 없이 jar 명령어를 실행할 수 있음
	
    ```jsp
	C:/apache-tomcat/webapps/jsp01.../jar cvf 웹애플리케이션이름.war *
    ```
    
    * c : 새로운 파일을 생성함
    
    * v : 세부 정보를 콘솔에 표시
    
    * f : 생성할 파일의 이름을 지정함
    
    * * : 현재 폴더의 모든 파일과 하위 폴더가 대상
    
    위 jar 명령어를 실행하면 war파일이 생성됨, 이 파일을 실 서버의 [톰캣]/webapps 폴더에 복사해주면 배포가 됨 