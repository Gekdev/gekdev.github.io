---
layout: default
title: Session
parent: Implicit Object
grand_parent : JSP
nav_order: 3
---

# Session Implicit Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Session

### Session basic

웹 브라우저에 정보를 보관할 때 쿠키를 사용한다면 **세션은 웹서버(웹 컨테이너)에 정보를 보관할 때 사용**

&#9656; 서버는 세션을 사용해서 클라이언트 상태를 유지할 수 있기 때문에, 로그인한 사용자 정보를 유지하기 위한 목적으로 세션을 사용

&#9656; 세션은 오직 웹 서버에만 생성이 됨

&#9656; 웹 컨테이너는 기본적으로 한 웹브라우저마다 한 세션을 생성하고, 각 브라우저 별 세션이 존재하기 때문에 웹 브라우저와 관련된 정보를 저장하기에 사용

★ 즉, 쿠키가 클라이언트 측의 데이터 저장소라면 세션은 웹 브라우저와 연관된 서버측의 저장소

![](https://gekdev.github.io/docs/jsp/example/session01.png)

### Create Session

**JSP에서는 세션을 생성하려면 page디렉티브의 session 속성을 true(기본값)으로 지정하면 됨**

&#9656; 세션을 생성하면 session 기본객체를 이용해 세션을 사용할 수 있게 됨

&#9656; 웹 브라우저가 처음 접속할 때 세션을 생성하고 이후로는 이미 생성된 세션을 사용하기 때문에 한번만 사용해주면 계속 쓸 수 있음

syntax
{: .label .mt-2}
```jsp
<%@ page session = "true" %>
<%

    session.setAttribute("userInfo", userInfo);

%>
```

#### request.getSession()

**HttpSession(session 객체)를 생성하는 또 다른 방법은 request.getSession() 메서드를 이용하는 것**

&#9656; 현재 요청과 관련된 session 객체를 리턴, session이 존재하면 해당 session을 리턴하고 없다면 새로운 session 객체를 생성해서 리턴

&#9656; request.getSession()을 이용해서 세션을 구하므로 page디렉티브의 session 속성값은 false로 지정

syntax
{: .label .mt-2}
```jsp
<%@ page session="false" %>
<%
    HttpSession httpSession = request.getSession();
    List list = (list) httpSession.getAttribute("list");
    list.add(productID);
%>
```

&#9656; session이 생성된 경우에만 session 객체를 구하고 싶을 경우 매개값으로 false를 지정하면 세션이 존재하는 경우만 리턴하고 없을 경우엔 null리턴

예제
{: .label .label-purple .mt-2}
```jsp
<%@ page session="false" %>
<%
    HttpSession httpSession = request.getSession(false);
    List list = null;
    if(httpSession != null){
        list = (List)httpSession.getAttribute("list");   
    }else{
        list = Collections.emptyList();
    }
%>
```

### Read session

세션을 사용한다는 것은 session 기본객체를 사용한다는 것

session 객체는 request객체와 마찬가지로 속성을 제공하고 setAttribute(), getAttrubute() 메서드를 사용해 session의 속성값을 저장하거나 읽을 수 있음

다만 session객체는 세션만의 고유 정보를 제어할 수 있는 메서드가 추가로 제공됨

세션 정보 관련 메서드
{: .label .label-red .mt-2}

| 메서드 | 리턴타입 | 설명 |
|:-------|:---------|:-----|
| getId() | String |세션ID(세션마다 고유의 ID값)를 리턴 |
| getCreationTime() | long | 세션이 생성된 시간을 리턴 |
| getLastAccessedTime() | long | 웹 브라우저가 마지막에 접근한 시간을 리턴 |

예제
{: .label .label-purple .mt-2}
```jsp
<%@page import="java.text.SimpleDateFormat"%>
<%@page import="java.util.Date"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page session="true" %>
<%
	Date time = new Date();
	SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
%>
...

<h3>세션 정보 읽기</h3>
session ID = <%= session.getId() %> <br>

<% time.setTime(session.getCreationTime()); %>
session 생성 시간 = <%= sdf.format(time) %> <br>

<% time.setTime(session.getLastAccessedTime());	%>
session 마지막 접근 시간 = <%= sdf.format(time) %> <br>
```

![](https://gekdev.github.io/docs/jsp/example/readsession.jpg)

#### JSESSIONID

웹 브라우저마다 각 세션을 구분하기 위해 고유 ID를 할당하는데 이걸 세션 ID라고 함

웹 서버는 웹 브라우저에 세션ID를 전송

웹 브라우저는 웹 서버에 연결할 때 마다 매번 세션 ID를 보내서 웹 서버가 어떤 세션을 사용할지 판단할 수 있게 함

웹 서버와 웹 브라우저가 세션 ID를 공유하기 위해 사용하는 것이 쿠키인데

**쿠키 목록 중 JSESSIONID 쿠키가 세션 ID를 공유할 때 사용하는 쿠키**

&#9656; 다른 JSESSIONID값을 사용할 때는 두 경로가 서로 다른 웹 어플리케이션일 때 사용(세션 ID를 보관할 때 사용할 JSESSIONID 쿠키의 경로로 웹 어플리케이션의 컨텍스트 경로를 사용)

&#8594; 서로 다른 두 웹 어플리케이션이 다른 세션 ID를 사용하고 다른 JSESSIONID쿠키를 사용한다는 것은, 세션을 공유하지 않음을 의미

### Save and Get Session

한번 생성된 세션은 지정한 유효시간동안 유지가 되기 때문에 웹 애플리케이션을 실행하는 동안 지속적으로 사용해야 하는 데이터의 저장소로 세션을 사용

request객체가 하나의 요청을 처리하는데 사용된다면 session 객체는 웹 브라우저의 여러 요청을 처리하는 JSP페이지에서 공유됨

로그인한 회원정보 등 웹브라우저와 일대일로 관련 값을 저장할 때 에는 쿠키보다는 세션을 사용하는게 좋음

syntax
{: .label .mt-2}
```jsp
<% session.setAttribute("세션이름", "세션값"); %>

<%= session.getAttribute("세션이름") %>
```

예제
{: .label .label-purple .mt-2}
```jsp
<h3>세션에 정보를 저장하기</h3>

<%
    session.setAttribute("session1_id", "sohyang");
    session.setAttribute("session2_pw", "12345");
    session.setAttribute("session3_name", "소향");
%>

<p>session1_id = <%= session.getAttribute("session1_id") %></p>
<p>session2_pw = <%= session.getAttribute("session2_pw") %></p>
<p>session3_name = <%= session.getAttribute("session3_name") %></p>
```

![](https://gekdev.github.io/docs/jsp/example/setsession.jpg)

### End Session

**세션을 유지할 필요가 없다면 session.invalidate() 메서드를 사용해서 세션을 종료**

세션을 종료하면 사용중인 session기본객체를 삭제하고 session객체에 저장되었던 속성정보도 삭제가 됨

종료 후 다시 생성하면 새로운 session 기본객체를 생성함

syntax
{: .label .mt-2}
```jsp
<%
	session.invalidate();
%>
```

예제
{: .label .label-purple .mt-2}
```jsp
<%
	session.invalidate();
%>
...

<!--세션 객체가 없어져서 확인하면 오류가 발생함-->

<p>session1_id = <%= session.getAttribute("session1_id") %></p>
<p>session2_pw = <%= session.getAttribute("session2_pw") %></p>
<p>session3_name = <%= session.getAttribute("session3_name") %></p>

```

### Session Validity Time

세션은 최종 접근시간 정보를 가지고 있는데 session 객체를 사용할 때 마다 최종 접근시간이 갱신됨 (session.getLastAccessedTime())

세션은 최종 접근시간 이후, 일정시간 내에 다시 세션에 접근하지 않을 경우에는 자동으로 세션을 종료하는 기능을 가지고 있음

&#9656; 세션 유효시간 설정은 두가지 방법이 있음

1. web.xml에 <session-config> 태그를 사용해 분단위로 지정

    session-timeout 태그 값을 세션의 유효시간으로 사용, 분단위
    
    예제
    {: .label .label-purple .mt-2}  
    ```jsp
    <session-config>
        <session-timeout>50</session-timeout>    // 50분
    </session-config>
    ```
    
    warning!
    {: .label .label-red .mt-2}
    <div class="code-example" markdown="1">
    0이나 음수로 지정하면 세션은 유효시간을 갖지 않음
    
    이 경우 명시적으로 session.invalidate메서드를 호출하기 전까지 세션 객체가 서버에 유지
    
    즉, 유효시간이 없는 상태에서 session.invalidate()를 실행하지 않으면 세션 객체가 계속 메모리에 남게되어 메모리 부족 현상이 발생
    
    따라서 제거되지 않은 세션 객체로 인해 메모리가 부족해지는 현상을 방지하려면 반드시 타임아웃시간을 지정해줘야함
    </div>
    
2. setMaxInactiveInterval() 메서드를 사용해 초단위로 지정

    예제
    {: .label .label-purple .mt-2}  
    ```jsp
    <%
	   session.setMaxInactiveInterval(60); //60초
    %>
    ...
    세션이 60초 후에 종료됩니다
	
	<p>session1_id = <%= session.getAttribute("session1_id") %></p>
	<p>session2_pw = <%= session.getAttribute("session2_pw") %></p>
	<p>session3_name = <%= session.getAttribute("session3_name") %></p>
    ```
    
### Why use Session instead of Cookie?

1. 쿠키 대신 세션을 사용하는 가장 큰 이유는 세션이 쿠키보다 보안에서 더 안정적이라는 점에 있음
	
	쿠키의 이름이나 값은 네트워크를 통해 전달되기 때문에 http 프로토콜을 사용하는 경우 중간에 쿠키값을 해킹할 수 있지만
	
	세션의 값은 오직 웹 서버에만 저장되기 때문에 중요한 자료를 보관할 때 알맞은 저장소가 됨

2. 웹 브라우저가 쿠키를 지원하지 않을 경우 또는 강제적으로 쿠키를 사용하지 못하게 할 경우 

    세션은 쿠키 설정여부와 상관없이 사용할 수 있음
    
하지만 세션은 여러 서버에서 공유할 수 없어서 여러 도메인 주소에 공유해야 하는 값을 사용할 경우에는 쿠키를 이용해서 로그인 정보를 저장

---

## Maintain login using Session

세션을 사용해서 로그인을 처리하는 방식은 쿠키를 사용한 방식과 비슷

1. 로그인에 성공하며 session 기본객체의 특정 속성에 데이터를 기록

2. 이후로 session 기본 객체의 특정 속성이 존재하면 로그인한 것으로 간주

3. 로그아웃 할 경우 session.invalidate()메서드를 호출하여 세션을 종료

### Login Form

로그인폼 : 아이디와 비밀번호를 입력할 페이지
{: .label .label-purple .mt-2}
```jsp
<div class="container" align="center">
    <h3>로그인폼</h3>
    <hr>
    <form class="form-inline" action="<%=request.getContextPath()%>/jsp09_session/jsp09_04_02_login.jsp">
        <div class="input-group mb-2 mr-sm-2">
           <div class="input-group-prepend">
              <span class="input-group-text"><i class="fas fa-user"></i></span>
           </div>
           <input type="text" name="id" class="form-control"/>
        </div>
        <div class="input-group mb-2 mr-sm-2">
          <div class="input-group-prepend">
            <span class="input-group-text"><i class="fas fa-lock"></i></span>
          </div>
         <input type="password" name="pw" class="form-control" />
        </div>
        <input type="submit" class="btn btn-primary mb-2" value="로그인"/> 
    </form>
</div>
```

### Login Processing

**아이디와 암호가 같으면(id=pw) 로그인에 성공한다고 가정**

로그인 : 아이디와 비밀번호를 처리 페이지
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%
	String id = request.getParameter("id");
	String pw = request.getParameter("pw");
	
	if(id.equals(pw)) {
		session.setAttribute("memberId", id);	
%>
		<!DOCTYPE html>
		<html>
		<head>
		</head>
		<body>
			<p>로그인 성공</p>
		</body>
		</html>
<% } else {%>
	<script>
		alert("로그인 실패");
		history.go(-1);
	</script>
<% } %>
```

### Determining Whether to Login or not

**Session이 존재하면 로그인했다고 판단**

로그인 여부 검사
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%
	String memberId = (String) session.getAttribute("memberId");
	boolean loginCheck = memberId==null ? false:true;
%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>

<%
	if(loginCheck){
%>		
		아이디 : <%= memberId %> 로그인 중입니다 
<%
	}else{
%>
		로그인을 하지 않았습니다
<%
	}
%>

</body>
</html>
```

### Logout Processing

로그아웃
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%

session.invalidate();

%>
<!DOCTYPE html>
<html>
<head>
</head>
<body>

로그아웃 되었습니다

</body>
</html>
```

아니면 로그인 상태를 보관할 때 사용한 session 객체를 삭제해도 같은 효과

```jsp
session.removeAttribute("MEMBERID");
```

### 연관된 정보 저장을 위한 클래스 작성

아이디 다음 이름이나 비밀번호처럼 연관된 정보를 관리해야 할 때는 클래스로 묶어서 저장하면 각 정보를 개별 속성으로 저장하지 않고 한개의 속성으로 저장해야 관리하기가 편함

클래스 예제
{: .label .label-purple .mt-2}
```java
public class MemberInfo{
    private String id;
    private String name;
    private String email;                    
    private boolean male;
    ...
    
    // get메서드
}
```

jsp set
{: .label .label-purple .mt-2}
```jsp
<%
    MemberInfo memberInfo = new MemberInfo(id, name);
    session.setAttribute("memberInfo", memberinfo);
%>
```

jsp get
{: .label .label-purple .mt-2}
```jsp
<%
    MemberInfo member = (MemberInfo) session.getAttribute("memberInfo");
%>

...
<%= member.getEmail().toLowerCase() %>
```