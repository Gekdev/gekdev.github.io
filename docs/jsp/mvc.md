---
layout: default
title: MVC Pattern
parent: JSP
nav_order: 14
---

# JSP MVC Pattern
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### 커맨드 패턴 기반의 프로그램

MVC패턴에서 컨트롤러 서블릿이 수행하는 작업은 사용자가 어떤 기능을 요청했는지를 분석하는 것

사용자의 요청을 판단하기 위해서 사용하는 방법 중 가장 일반적인 방법은 명령어를 사용하는 것

1. 사용자가 게시판 목록보기, 글쓰기 등의 명령을 서블릿에 전송하고 

2. 컨트롤러 서블릿은 사용자가 전송한 요청에 해당하는 기능을 수행한 후에

3. View를 통해 결과를 보여주는 패턴을 커맨드 패턴이라고 한다

커멘트 패턴에서 파라미터에 명령어 정보를 전달하는 두가지 방법

1. 특정 이름의 파라미터에 명령어 정보를 전달하는 방법(ControllerUsingFile.java)

	```jsp
	localhost:8088/mvc/ControllerUsingFile?cmd=hello
	```

2. 요청되는 URI자체를 명령어로 사용하는 방법(ControllerUsingURI.java)

    ```jsp
    localhost:8088/mvc/member.do
    ```

---

## Model 2 & MVC Pattern

JSP 웹 어플리케이션의 구조는 크게 모델 1, 모델 2로 나뉜다

JSP에서 모든 로직과 출력을 처리하느냐 아님 JSP에서는 출력만 처리하느냐에 따라 1과 2구조로 나뉨

### Model 1 Structure

**웹 브라우저의 요청을 JSP가 직접 처리함**

* 모델 1을 구성하는 요소

    1. JSP

    2. 자바빈 혹은 서비스 클래스

&#9656; 웹 브라우저의 요청을 받은 JSP는 자바빈이나 서비스 클래스를 이용해서 웹 브라우저가 요청한 작업을 처리하고 그 결과를 클라이언트에 출력함

&#9656; 비즈니스 로직을 처리하기 위한 코드와 웹 브라우저에 결과를 출력하는 코드가 섞임

&#9656; 과거에 가장 많이 사용되었던 아키텍쳐

![](model1.gif)

모델 1 구조의 장점과 단점
{: .label .label-red .mt-2}

| 장점 | 단점 |
|:-----|:-----|
| 구조가 단순하여 익히기가 쉬움 | 출력을 위한 뷰 코드와 로직 처리를 위한 자바 코드가 함께 섞이기 때문에 JSP 코드 자체가 복잡해진다 |
| 위와 같은 이유로 숙련된 개발자가 아니더라도 구현이 용이 | JSP 코드에서 백엔드와 프론트엔드가 혼재되기 때문에 분업이 용이하지 않음 |
| | 코드가 복잡해져 유지보수가 어려움 |

### Model 2 Structure

**웹 브라우저의 요청을 하나의 서블릿이 받음(로직을 처리)**

* 모델 2를 구성하는 요소

    1. 서블릿 : 모든 흐름 제어는 컨트롤러(Controller)인 서블릿 담당

    2. JSP : 요청 결과는 유저에게 결과를 보여줄 뷰(View)단인 JSP 담당

    3. 자바빈 혹은 서비스 클래스 : 요청에 대한 로직 처리 담당
    
&#9656; 서블릿은 웹 브라우저의 요청을 알맞게 처리한 후 그 결과를 보여줄 JSP 페이지로 포워딩함

&#9656; 포워딩을 통해 요청 흐름을 받은 JSP 페이지는 결과 화면을 클라이언트에 전송함

&#9656; 모델 2 구조의 이러한 특징 때문에 MVC 패턴을 이용해서 웹 어플리케이션을 구현할 때 모델 2 구조를 사용함

![](model2.gif)

### MVC pattern

MVC(Model-View-Controller: 모델-뷰-컨트롤러) 패턴은 웹 개발자라면 반드시 알아야 할 패턴

MVC 패턴은 스윙(swing)과 같은 UI컴포넌트 뿐만 아니라 웹 어플리케이션 개발 영역에서도 보편적으로 사용됨

* Model(모델) : 비즈니스 영역의 로직을 처리

* View(뷰) : 비즈니스 영역에 대한 프레젠테이션 뷰를 담당

* Controller(컨트롤러) : 사용자의 입력처리와 흐름 제어를 담당

| MVC 패턴 | 모델 2 | 역할 |
|:---------|:-------|:---|
| Model | 서비스 클래스 or 자바빈 | 비즈니스 로직을 처리하는 모든것들이 모델에 속함. 컨트롤러로부터  특정 로직에 대한 처리 요청(ex: 게시판 글쓰기, 회원가입, 로그인 등)이 들어오면 이를 수행하고 수행 결과를 컨트롤러에 반환. 필요한 정보는 request 객체나 session 객체에 저장하기도 함. |
| View | JSP 페이지 |  클라이언트에 출력되는 화면. 모델1과 달리 로직 처리를 위한 코드가 내포되어 있지 않음. 요쳥 결과의 출력 뿐만 아니라 컨트롤러에 요청을 보내는 용도로도 사용됨. request 객체나 session 객체에 저장된 정보를 토대로 화면을 출력. |
| Controller | 서블릿 |  MVC 패턴(모델 2)모든 흐름 제어를 맡음. 브라우져로부터 요청이 들어오면, 어떤 요청인지를 분석하여 이 요청을 처리하기 위한 모델을 사용하여 처리. 사용한 모델로부터 처리 결과를 받으면 추가로 처리하거나 가공해야할 정보가 있다면 처리 후 request 객체나 session객체에 저장하고, 뷰(JSP 페이지)를 선택하여 foward나 redirect 하여 클라이언트에 출력. |

MVC의 장점과 단점
{: .label .label-red .mt-2}

| 장점 | 단점 |
|:-----|:-----|
| 출력을 위한 뷰 코드와 로직 처리를 위한 자바 코드를 분리하기 때문에 JSP 모델1에 비해 코드가 복잡하지 않음 | 구조가 복잡하여 습득이 어렵고 작업량이 많음|
| 뷰, 로직처리에 대한 분업이 용이 | JAVA에 대한 깊은 이해가 필요|
| 기능에 따라 분리되어있기 때문에 유지보수가 용이 | |

#### Controller : Servlet

컨트롤러 역할을 하는 서블릿은 다음 과정을 거쳐서 웹 브라우저의 요청을 처리함

1. 웹 브라우저가 전송한 HTTP 요청을 받음. 서블릿의 doGET() 메소드 or doPost()메소드가 호출

2. 웹 브라우저가 어떤 기능을 요청했는지 분석.

3. 모델을 사용해서 요청한 기능을 수행한다.

4. 모델로부터 전달받은 결과물을 알맞게 가공한 후 , request 나 session 의 setAttribute() 메소드를 사용하여 결과값을 속성에 저장. 이렇게 저장된 결과값은 뷰 ( JSP ) 에서 사용됨.

5. 웹 브라우저에 보여질 JSP를 선택한 후, 해당 JSP로 포워딩. 경우에 따라서 리다이렉트를 하기도 함

![](mvcservlet.png)

비즈니스 로직의 처리는 모델에서 이루어짐

서블릿은 모델이 내부적으로 어떻게 비즈니스 로직을 처리하는지 알 필요없이, 웹 브라우저의 요청에 따라 알맞게 모델을 사용하여 요청 기능을 실행하고 그 결과를 뷰인 JSP에 전달하면 됨

웹 브라우저의 결과를 보여줄 JSP 페이지는 컨트롤러 서블릿이 선택함, 이때 요청 처리 결과는 request나 session에 저장해서 뷰 역할을 하는 JSP 페이지에 전달함

#### View : JSP

비즈니스 로직과 관련된 코드가 없는 점을 제외하면 일반 JSP와 동일한 형태를 취함

컨트롤러에서 request객체나 session 기본 객체에 저장한 데이터를 사용하여 웹 브라우저에 알맞은 결과를 출력

뷰 JSP는 컨트롤러 서블릿처럼 일반적인 처리 순서가 정해져 있지 않음

뷰 역할을 하는 JSP는 웹 브라우저가 요청한 결과를 보여주는 프레젠테이션의 역할을 할 뿐만 아니라 웹 브라우저의 요청을 컨트롤러에 전달해주는 매개체가 됨

JSP는 웹브라우저가 지속적으로 컨트롤러에 요청을 보낼 수 있는 링크나 폼을 제공해서 웹 브라우저가 업무 흐름에 따라 컨트롤러에 알맞은 요청을 보낼 수 있도록 함

#### Model

**비즈니스 로직을 처리하는 것이 모두 모델**

기능 : 웹 브라우저의 요청을 처리하는데 필요한 기능(ex. 계좌이체를 시켜주는 기능)

컨트롤러 역할을 하는 서블릿과 모델간의 통신
{: .label .mt-2}

![](mvcmodel.jpg)

&#9656; 컨트롤러 서블릿이 웹 브라우저의 요청을 분석해 알맞은 모델을 호출하면서부터 모델의 기능 시작

&#9656; 모델은 컨트롤러가 요청한 작업을 처리한 후 알맞은 결과를 컨트롤러에게 전달하는데 이 때 처리한 결과값을 저장하는 객체로 보통 자바 빈을 사용

&#9656; 모델은 서비스 클래스나 DAO 클래스를 이용해서 비즈니스 로직을 수행하게 됨

### Model 1 or Model 2 ?

| 모델 | 장점 | 단점 |
|:-----|:-----|:-----|
| 모델 1 | 배우기쉬움, 자바 언어를 몰라도 어느정도 구현 가능 | 로직 코드와 뷰 코드가 혼합되어 JSP 코드가 복잡해짐 |
| | 기능과 JSP가 직관적으로 연결됨 | 뷰 변경 시 논리 코드의 빈번한 복사가 반복해서 코드 중복이 발생하기 쉬워 유지 보수가 힘들어짐 |
| 모델 2 | 로직 코드와 뷰 코드를 분리해서 유지 보수가 쉬워짐 | 자바 언어에 치숙하지 않으면 접근하기가 쉽지 않음 |
| | 컨트롤러 서블릿에서 권한 검사나 인증과 같은 공통 기능 처리가 가능 | 작업량이 많음 |
| | 확장이 용이함 | |

---

## 모델 2 구조를 이용한 MVC 패턴의 구현

### 기본 MVC 패턴 구현 기법

서블릿 클래스(컨트롤러 역할)의 동작방식

1. HTTP 요청 받음

2. 요청 분석

3. 모델을 사용하여 요청한 기능을 수행

4. request나 session에 처리 결과를 저장

5. RequestDispatcher를 사용해 알맞은 뷰로 포워딩

전형적인 서블릿 클래스의 코드
{: .label .mt-2}
```java
package com.lec.servlet;

import java.io.IOException;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class ControllerServlet extends HttpServlet{

	//1단계 : HTTP 요청 받음
	@Override
	protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		processRequest(req, res);
	}
	
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		processRequest(req, res);
	}

	private void processRequest(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		//2단계 : 요청 분석
		//request 객체로부터 사용자의 요청을 분석하는 코드
		String type = req.getParameter("type");
		
		//3단계 : 모델을 사용하여 요청한 기능을 수행
		//사용자 요청에 따라 필요한 기능을 수행한 뒤 결과값을 생성
		Object resultObject = null;
		if(type==null || type.equals("A")) {
			resultObject = "안녕하세요";
		} else if (type.equals("B")){ 
			resultObject = new java.util.Date();			
		} else {
			resultObject = "Invalid Type";
		}
		
		//4단계 : request나 session에 처리 결과를 저장
		req.setAttribute("result", resultObject);
		
		//5단계 : RequestDispatcher를 사용해 알맞은 뷰로 포워딩
		RequestDispatcher dispatcher = req.getRequestDispatcher("/view.jsp");
		dispatcher.forward(req, res);
	}
}
```

위 코드를 출력하는 jsp 뷰 페이지
{: .label .label-purple .mt-2}
```jsp
<html>
<body>
결과 : ${result}
</body>
</html>
```

서블릿 클래스를 실행하기 위한 web.xml 코드
```xml
<!--ControllerServlet를 서블릿으로 등록-->
<servlet>
    <servlet-name>ControllerServlet</servlet-name>
    <servlet-class>com.lec.servlet.ControllerServlet</servlet-class>
</servlet>

<servlet-mapping>
    <servlet-name>ControllerServlet</servlet-name>
    <!--/simple 요청 URI를 SimpleController가 처리하도록 설정-->
    <url-pattern>/simple</url-pattern>
</servlet-mapping>
```

### 커맨드 패턴 기반의 코드

컨트롤러 서블릿의 작업 중 두번째 작업인 요청분석을 판단하는 방법중에는 가장 일반적인 방법은 명령어를 사용하는 것

웹 브라우저를 통해서 명령어를 전달하는 방법은 두가지가 있음

1. 특정 이름의 파라미터에 명령어 정보를 전달

2. 요청 URI 자체를 명령어로 사용

#### 커맨드 패턴을 이용한 명령어 처리기의 분리

http://localhost:8088/chap01/controller?cmd=BoardList&... 와 같은 URL을 전달받는다면

ControllerServlet은 cmd 파라미터값에 따라 알맞은 기능을 수행하도록 작성함

```java
String command = request.getParameter("cmd");
String viewPage = null;
if(command == null){
    //명령어 오류 처리
    viewPage = "error/invalidCommand.jsp";
} else if(command.equals("BoardList")){
    //글 목록 읽기 요청 처리
    ...                 
   viewPage = "board/list.jsp";
} else if(command.equals("BoardWriteForm"){
    //글쓰기 입력 폼 요청 처리
    ...                                       
    viewPage = "board/writeForm.jsp";
}

RequsetDispatcher dispatcher = request.getRequestDispatcher(viewPage)
dispatcher.forward(req, res);          
```

명령어와 관련된 로직 처리를 컨트롤러 서블릿에서 처리하면 위와같이 복잡해짐

**커멘드 패턴 : 각 명령어에 해당하는 로직 처리 코드를 별도 클래스로 작성**

하나의 명령어를 하나의 클래스에서 처리하도록 구현하는 패턴

CommandHandler는 인터페이스

NullHandler나 BoardListHandler 등의 클래스는 각각의 명령어에 해당하는 로직 실행 코드를 담고 있는 클래스

![](commandinterface.png)

이 로직 처리 클래스는 로직을 수행하기 위해 process() 메서드를 호출하고 결과를 보여줄 뷰 페이지 정보를 리턴

즉, 컨트롤러 서블릿은 명령어에 해당하는 CommandHandler 인스턴스를 생성하고 실제 로직의 처리는 생성한 CommandHandler 인스턴스에서 실행되는 구조

```jsp
String command = request.getParameter("cmd");
CommandHandler handler = null;

if(command == null){
    handler = new NullHandler();
} else if(command.equals("BoardList")){
    handler = new BoardListHandler();
} else if(command.equals("BoardWriteForm"){
    handler = new BoardWriteFormHandler();
}

String viewPage = handler.process(req, res);

RequsetDispatcher dispatcher = request.getRequestDispatcher(viewPage)
dispatcher.forward(req, res);
```

컨트롤러 서블릿에서 로직 처리 코드를 CommandHandler로 분리
{: .label .label-red .mt-2}
![](commandhandler.png)

CommandHandler Interface
{: .label .label-purple .mt-2}
```java
package com.lec.servlet;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

//CommandHandler 인터페이스를 정의
public interface CommandHandler {
	
	//모든 명령어 핸들러가 공통으로 구현해야 하는 메서드를 선언
	//process() 메서드를 이용해서 알맞은 로직 코드를 구현하고 결과를 보여줄 JSP의 URI를 리턴
	public String process(HttpServletRequest req, HttpServletResponse res) throws Exception;
	
}
```

SomeHandler Class
{: .label .label-label .mt-2}
```java
package com.lec.servlet;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class SomeHandler implements CommandHandler {

	@Override
	public String process(HttpServletRequest req, HttpServletResponse res) throws Exception {
		String value = "";
		
		//1. 명령어와 관련된 비즈니스 로직 처리
		//사용자가 요청한 작업을 수행
		
		//2. 뷰페이지에서 사용할 정보 저장
		req.setAttribute("someValue", value);
		
		//3. 처리결과를 보여줄 뷰페이지의 URI 리턴
		return "/view/someView.jsp";
	}

}
```

### 설정 파일에 커맨드와 클래스의 관계 명시

if-else 코드는 새로운 명령어가 추가되면 컨트롤러 서블릿 클래스의 코드를 직접 변경해야 하는 단점이 있음

이 단점을 해결하는 방법은 <명령어, 핸들러클래스>의 매핑 정보를 설정 파일에 저장하는 것

컨트롤러 서블릿은 설정 파일에서 명령어와 핸들러 클래스의 매핑 정보를 읽어와 명령어에 해당하는 핸들러 클래스 객체를 미리 생성해 두었다가 process() 메서드에서 사용하면 됨

컨트롤러 서블릿에서 설정파일을 읽어오기에 가장 좋은 위치는 init() 메서드

설정파일을 이용해서 핸들러 객체를 생성하는 기능을 구현한 컨트롤러 서블릿
{: .label .label-purple .mt-2}
```java
package com.lec.servlet;

import java.io.FileReader;
import java.io.IOException;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Properties;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class ControllerUsingFile extends HttpServlet{
	
	//<커맨드, 핸들러인스턴스> 매핑정보 저장
	private Map<String, CommandHandler> commandHandlerMap = new HashMap<>();
	
	@Override
	public void init() throws ServletException {
		
		//configFile 초기화 파라미터 값을 읽어옴, 설정파일의 경로를 구함
		String configFile = getInitParameter("configFile");
		Properties prop = new Properties();
		String configFilePath = getServletContext().getRealPath(configFile);
		
		//설정파일로부터 매핑정보를 읽어와 prop객체에 저장
		//프로퍼티 이름을 커맨드 이름으로 사용하고 값을 클래스 이름으로 사용함
		try (FileReader fis = new FileReader(configFilePath)){
			prop.load(fis);
		} catch (IOException e) {
			throw new ServletException(e);
		}
		
		//Properties에 저장된 각 프로퍼티의 키에 대해 다음 작업을 반복함
		Iterator keyIter = prop.keySet().iterator();
		while(keyIter.hasNext()) {
			//1.프로퍼티 이름을 커멘드 이름으로 사용
			String command = (String) keyIter.next();
			//2.커맨드 이름에 해당하는 핸들러 클래스 이름을 Properties에서 구함
			String handlerClassName = prop.getProperty(command);
			
			try {
				//3.핸들러 클래스 이름을 이용해서 Class 객체를 구함
				Class<?> handlerClass = Class.forName(handlerClassName);
				//4.Class로부터 핸들러 객체를 생성
				//즉, 2번과정에서 구한 이름에 해당하는 클래스의 객체를 생성함
				CommandHandler handlerInstance = (CommandHandler) handlerClass.newInstance();
				//5.commandHandlerMap에 (커맨드, 핸들러 객체) 매핑 정보를 저장
				commandHandlerMap.put(command, handlerInstance);
			} catch (ClassNotFoundException | InstantiationException | IllegalAccessException e) {
				throw new ServletException(e);
			}
			
		}
	}
	
	@Override
	protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		process(req, res);
	}
	
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		process(req, res);
	}

	private void process(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		
		//클라이언트가 요청한 명령어를 구함, cmd파라미터 사용
		String command = req.getParameter("cmd");
		//commandHandlerMap에서 요청을 처리할 핸들러 객체를 구함
		CommandHandler handler = commandHandlerMap.get(command);
		
		//명령어에 해당하는 핸들러 객체가 존재하지 않을 경우 NullHandler를 사용
		if(handler == null) {
			handler = new NullHandler();
		}
		
		String viewPage = null;
		
		try {
			//구한 핸들러 객체의 process() 메서드를 호출해서 요청을 처리하고
			//결과로 보여줄 뷰 페이지 경로를 리턴 값으로 전달받음
			//process()메서드는 클라이언트 요청을 알맞게 처리하고 뷰 페이지에 보여줄 값을 request나 session속성에 저장해야 함
			viewPage = handler.process(req, res);			
		} catch (Exception e) {
			throw new ServletException(e);
		}
		
		//viewPage가 null이 아닐경우 핸들러 인스턴스가 리턴한 뷰 페이지로 이동함
		if(viewPage!=null) {
			RequestDispatcher dispatcher = req.getRequestDispatcher(viewPage);
			dispatcher.forward(req, res);
		}
	}
	
}
```

NullHandler 클래스: 404 에러 출력
{: .label .label-purple .mt-2}
```java
package com.lec.servlet;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class NullHandler implements CommandHandler {

	@Override
	public String process(HttpServletRequest req, HttpServletResponse res) throws Exception {
		
		res.sendError(HttpServletResponse.SC_NOT_FOUND);
		
		return null;
	}

}
```

config 초기화 파라미터를 설정 파일 경로로 사용하므로 web.xml파일에 설정 파일 경로를 지정해야 함

web.xml
{: .label .label-purple .mt-2}
```xml
<servlet>
    <servlet-name>ControllerUsingFile</servlet-name>
    <servlet-class>com.lec.servlet.ControllerUsingFile</servlet-class>
    <init-param>
        <param-name>configFile</param-name>
        <param-value>/WEB-INF/commandHandler.properties</param-value>
    </init-param>
    <load-on-startup>1</load-on-startup>
</servlet>

<servlet-mapping>
    <servlet-name>ControllerUsingFile</servlet-name>
    <url-pattern>/controllerUsingFile</url-pattern>
</servlet-mapping>
```

#### Properties와 프로퍼티 파일

**자바의 Properties는 프로퍼티를 관리할 때 사용하는 클래스**

&#9656; 프로퍼티는 (이름, 값)으로 구성됨

사용방법
{: .label .mt-2}
```java
Properties prop = new Properties();
prop.setProperty("name1", "value1")         //이름이 name1이고 값이 value1인 프로퍼티 설정
String name1 = prop.getProperty("name1")    //name1인 프로퍼티 값 구하기
```

&#9656; Properties 클래스는 프로퍼티 목록을 파일에서 읽어올 수 있음. 이때 이 파일을 프로퍼티 정보를 갖고 있다고 해서 프로퍼티 파일이라고 함 

Properties 파일
{: .label .mt-2}
```properties
#주석
프로퍼티이름1=프로퍼티값1
프로퍼티이름2=프로퍼티값2
```

&#9656; Properties의 load() 메서드를 사용하면 설정 파일로부터 프로퍼티 정보를 읽어올 수 있음

commandHandler.properties
{: .label .label-purple .mt-2}
```properties
#com.lec.servlet.NullHandler 클래스 설정
null=com.lec.servlet.NullHandler
#someCommand=any.SomeHandler
hello=com.lec.servlet.HelloHandler
```

#### final check

위 코드가 잘 되는지 확인하기

아래 파일을 실행시키고 http://localhost:8088/servlet/controllerUsingFile?cmd=hello 치기

index.jsp
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>
    <%= request.getAttribute("hello") %>
</body>
</html>
```

![](hello.jpg)

### 요청 URI를 명령어로 사용하기

cmd파라미터를 명령어로 사용하면 컨트롤러의 URL이 사용자에게 노출된다는 단점이 있음

노출을 막기위해 요청 URI 자체를 명령어로 사용함

컨트롤러 서블릿의 process() 메서드에서 request.getParameter("cmd")대신 다음과 같은 코드를 사용하면 됨

```java
String command = request.getRequestURI();
if(command.indexOf(request.getContextPath()) == 0){
    //웹어플리케이션 내에서의 요청 URI만을 사용하기 위함
    command = command.substring(request.getContextPath().length());
}
```

설정파일을 이용해서 핸들러 객체를 생성하는 기능을 구현한 컨트롤러 서블릿
{: .label .label-purple .mt-2}
```java
package board.controller;

import java.io.FileReader;
import java.io.IOException;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Properties;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import board.handler.CommandHandler;
import board.handler.NullHandler;

public class ControllerUsingURI extends HttpServlet{

	//<커맨드, 핸들러인스턴스> 매핑정보 저장
	private Map<String, CommandHandler> commandHandlerMap = new HashMap<>();
	
	@Override
	public void init() throws ServletException {
		
		//configFile 초기화 파라미터 값을 읽어옴, 설정파일의 경로를 구함
		String configFile = getInitParameter("configFile");
		Properties prop = new Properties();
		String configFilePath = getServletContext().getRealPath(configFile);
		
		//설정파일로부터 매핑정보를 읽어와 prop객체에 저장
		//프로퍼티 이름을 커맨드 이름으로 사용하고 값을 클래스 이름으로 사용함
		try (FileReader fis = new FileReader(configFilePath)){
			prop.load(fis);
		} catch (IOException e) {
			throw new ServletException(e);
		}
		
		//Properties에 저장된 각 프로퍼티의 키에 대해 다음 작업을 반복함
		Iterator keyIter = prop.keySet().iterator();
		while(keyIter.hasNext()) {
			//1.프로퍼티 이름을 커멘드 이름으로 사용
			String command = (String) keyIter.next();
			//2.커맨드 이름에 해당하는 핸들러 클래스 이름을 Properties에서 구함
			String handlerClassName = prop.getProperty(command);
			
			try {
				//3.핸들러 클래스 이름을 이용해서 Class 객체를 구함
				Class<?> handlerClass = Class.forName(handlerClassName);
				//4.Class로부터 핸들러 객체를 생성
				//즉, 2번과정에서 구한 이름에 해당하는 클래스의 객체를 생성함
				CommandHandler handlerInstance = (CommandHandler) handlerClass.newInstance();
				//5.commandHandlerMap에 (커맨드, 핸들러 객체) 매핑 정보를 저장
				commandHandlerMap.put(command, handlerInstance);
			} catch (ClassNotFoundException | InstantiationException | IllegalAccessException e) {
				throw new ServletException(e);
			}
			
		}
	}
	
	@Override
	protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		process(req, res);
	}
	
	@Override
	protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		process(req, res);
	}

	private void process(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		
		String command = req.getRequestURI();
		if(command.indexOf(req.getContextPath()) == 0){
		    //웹어플리케이션 내에서의 요청 URI만을 사용하기 위함
		    command = command.substring(req.getContextPath().length());
		}
		//commandHandlerMap에서 요청을 처리할 핸들러 객체를 구함
		CommandHandler handler = commandHandlerMap.get(command);
		
		//명령어에 해당하는 핸들러 객체가 존재하지 않을 경우 NullHandler를 사용
		if(handler == null) {
			handler = new NullHandler();
		}
		
		String viewPage = null;
		
		try {
			//구한 핸들러 객체의 process() 메서드를 호출해서 요청을 처리하고
			//결과로 보여줄 뷰 페이지 경로를 리턴 값으로 전달받음
			//process()메서드는 클라이언트 요청을 알맞게 처리하고 뷰 페이지에 보여줄 값을 request나 session속성에 저장해야 함
			viewPage = handler.process(req, res);			
		} catch (Exception e) {
			throw new ServletException(e);
		}
		
		//viewPage가 null이 아닐경우 핸들러 인스턴스가 리턴한 뷰 페이지로 이동함
		if(viewPage!=null) {
			RequestDispatcher dispatcher = req.getRequestDispatcher(viewPage);
			dispatcher.forward(req, res);
		}
	}
	
}
```

config 초기화 파라미터를 설정 파일 경로로 사용하므로 web.xml파일에 설정 파일 경로를 지정해야 함

*.do로 오는 요청은 모두 ControllerUsingURI으로 전달됨

web.xml
{: .label .label-purple .mt-2}
```xml
<servlet>
    <servlet-name>ControllerUsingURI</servlet-name>
    <servlet-class>com.lec.servlet.ControllerUsingURI</servlet-class>
    <init-param>
        <param-name>configFile</param-name>
        <param-value>/WEB-INF/commandHandlerURI.properties</param-value>
    </init-param>
    <load-on-startup>1</load-on-startup>
</servlet>

<servlet-mapping>
    <servlet-name>ControllerUsingURI</servlet-name>
    <url-pattern>*.do</url-pattern>
</servlet-mapping>
```
