---
layout: default
title: Cookie
parent: JSP
nav_order: 10
---

# JSP Cookie
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

--- 

## Cookie

### Cookie basic

**쿠키 : 웹 브라우저가 보관하는 데이터**

&#9656; 웹 브라우저는 웹 서버에 요청을 보낼 때 쿠키를 함께 전송함

&#9656; 웹 서버는 웹 브라우저가 전송한 쿠키를 사용해서 필요한 데이터를 얻을 수 있음

&#9656; 쿠키는 웹 서버와 웹 브라우저 양쪽에서 생성가능

&#9656; JSP에서 생성하는 쿠키는 웹 서버에서 생성하는 쿠키

### How Cookie Works

웹 브라우저에 쿠키가 저장되면 웹 브라우저는 쿠키가 삭제되기 전까지 웹 서버에 쿠키를 전송하기 때문에 **웹 어플리케이션을 사용하는 동안 지속적으로 유지해야 하는 정보는 쿠키를 사용해서 저장하면 됨**

1. 쿠키 생성 

	&#9656; 쿠키를 사용하려면 먼저 쿠키를 생성해야 함 
	
	&#9656; JSP 프로그래밍에서 쿠키는 웹 서버 측에서 생성
	
	&#9656; 생성한 쿠키를 응답 데이터의 헤더에 저장해서 웹브라우저에 전송

2. 쿠키 저장 
	
	&#9656; 웹 브라우저는 응답 데이터에 포함된 쿠키를 쿠키 저장소에 보관

	&#9656; 쿠키의 종류에 따라 메모리나 파일에 저장

3. 쿠키 전송 

	&#9656; 웹 브라우저는 저장한 쿠키를 요청이 있을 때 마다 웹 서버에 전송
	
	&#9656; 웹 서버는 웹 브라우저가 전송한 쿠키를 사용해서 필요한 작업을 수행

![](https://gekdev.github.io/docs/jsp/example/cookie.png)

### Cookie Components

* **이름 : 각각의 쿠키를 구별하는데 사용되는 이름**
    
    쿠키이름의 네이밍룰
    {: .label .label-red .mt-2}
    <div class="code-example" markdown="1">
    쿠키의 이름은 콤마, 세미콜론, 공백, 등호기호(=)를 제외한 출력 가능한 아스키 문자로 구성

    보통 쿠키 이름을 작성할 때는 알파벳과 숫자만 이용
    </div>

* **값 : 쿠키의 이름과 관련된 값**

    서버는 값을 이용해서 원하는 작업을 수행함

    쿠키값의 네이밍룰
    {: .label .label-red .mt-2}
    <div class="code-example" markdown="1">
    쿠키값은 콤마, 세미콜론, 공백 문자를 제외한 나머지 출력이 가능한 아스키문자를 사용

    값으로 사용할 수 있는 문자가 한정되어있기 때문에 쿠키값을 생성할 때에는 알맞은 방식으로 인코딩해야 함
    </div>
    
* 유효시간 : 쿠키의 유지 시간, 별도로 지정하지 않으면 브라우저를 종료할 때 쿠키를 함께 삭제함

* 도메인 : 쿠키를 전송할 도메인, 쿠키를 제한함

* 경로 : 쿠키를 전송할 요청경로, 쿠키를 제한함

### Create Cookie

JSP에서 쿠키를 생성할 때에는 Cookie클래스를 사용함

syntax
{: .label .mt-2}
```jsp
<%
    Cookie cookie = new Cookie("쿠키이름", "쿠키값")   //쿠키 정보를 담고 있는 Cookie객체 생성
    response.addCookie(cookie)                         //쿠키 추가, 웹브라우저에 쿠키전송
%>
```

### Cookie Class Methods

**Cookie 클래스가 제공하는 메서드**

| 메서드 | 리턴 타입 | 설명 |
|:-------|:----------|:-----|
| getName() | String | 쿠키 이름을 구함 |
| getValue() | String | 쿠키 값을 구함 |
| setValue(String value) | void | 쿠키 값을 지정함 |
| setDomain(String pattern) | void | 이 쿠키가 전송될 서버의 도메인을 지정함 |
| getDomain() | String | 쿠키의 도메인을 구함 |
| setPath(String uri) | void | 쿠키를 전송할 경로를 지정 |
| getPath() | String | 쿠키의 전송 경로를 구함 |
| setMaxAge(int expiry) | void | 쿠키의 유효시간을 초단위로 지정. 음수로 입력할 경우 웹 브라우저를 닫을 때 쿠키가 함께 삭제됨 |
| getMaxAge() | int | 쿠키의 유효시간을 구함 |

### Read Cookie

**쿠키의 값 읽어오기**

&#9656; 쿠키를 생성한 후 그 이후부터 해당 쿠키를 사용할 수 있음. 웹 브라우저는 요청 헤더에 쿠키를 저장해서 보냄

&#9656; 읽어올 쿠키가 없으면 null 리턴, 따라서 NullPointerException 예외처리를 하거나 if문을 사용해야 함

&#9656; 배열로 들어오기 때문에 for문을 사용해서 출력해줌

syntax
{: .label .mt-2}
```jsp
<%
    Cookie[] cookies = request.getCookies();
%>
```

### Example

**쿠키 이름과 값 읽어오기**

```jsp
<%
    Cookie[] cookies = request.getCookies();            //쿠키의 값 읽어오기

    if(cookies != null && cookies.length > 0){          //쿠키값 null 처리
        for(int i=0 ; i<cookies.length ; i++){          //배열로 들어오는 쿠키 for문으로 출력
    %>    
            <%= cookies[i].getName() %>                  //쿠키클래스 메서드를 사용해 쿠키 이름 불러오기
            =
            <%= URLDecoder.decode(cookies[i].getValue(),"utf-8") %> <br/> // 메서드로 쿠키 값을 디코딩해서 가져오기
    <%    
        }
    }else{
    %>
        쿠키가 존재하지 않습니다
    <%
    }
%>
```

### Change Cookie Value

쿠키값을 변경하려면 같은 이름의 쿠키를 새로 생성해서 응답 데이터로 보내면 됨

예를들어 이름이 name인 쿠키 값을 면경하려면 새로운 name쿠키를 생성해서 응답데이터에 추가함

쿠키 값을 변경한다는 것은 기존에 존재하는 쿠키를 변경한다는 것 따라서 쿠키가 있는지 유무부터 판단해야 함

syntax
{: .label .mt-2}
```jsp
<%
    Cookie cookie = new Cookie("name", URLEncoder.encode("새로운 값","utf-8"));
    response.addCookie(cookie);
%>
```

### Example

**쿠키 이름이 name인 쿠키 변경하기**

```jsp
<%
    Cookie[] cookies = request.getCookies();              //쿠키 전체를 가져오기

    if(cookies != null && cookies.length > 0){          
        for(int i=0 ; i<cookies.length ; i++){          
            if(cookies[i].getName().equals("name")){      //쿠키들 중 쿠키이름이 내가 지정한 이름과 같은 쿠키의 존재 여부를 확인
                Cookie cookie = new Cookie(name, value);  //맞다면 새로 생성해 변경
                response.addCookie(cookie);
            }
         }
    }
>%
```

### Delete Cookie

**쿠키 클래스의 setMaxAge()의 인자값을 0으로 주면 삭제됨**

정확하게 말하면 지속시간을 0초로 바꿔버려서 없어지게 하는것

반대로 지속시간을 지정하면 쿠키를 오래동안 [유효]()하게 할 수 있음 

syntax
{: .label .mt-2}
```jsp
<%
    Cookie cookie = new Cookie("name", "");
    cookie.setMaxAge(0)
%>
```

### Example

**쿠키 이름이 name인 쿠키 삭제하기**

```jsp
<%
    Cookie[] cookies = request.getCookies();           

    if(cookies != null && cookies.length > 0){          
        for(int i=0 ; i<cookies.length ; i++){          
            if(cookies[i].getName().equals("name")){   
                Cookie cookie = new Cookie(name, "");  
                cookie.setMaxAge(0);                    //쿠키 삭제하기
                response.addCookie(cookie);
            }
         }
    }
>%
```

#### Delete All Cookies

**전체 쿠키를 삭제하고 싶을 때 사용함**

현재 페이지 경로의 쿠키만 삭제함, 만약 더 깊은 경로로 관련 도메인에 모두 쿠키를 전송했다면 깊은 경로에 있는 쿠키는 삭제되지 않음

예를들어 A파일에서 쿠키를 삭제하는 프로그램을 작성하더라도 쿠키인스턴스.setPath("");를 어떻게, 얼마나 깊게 작성했느냐에 따라 달라짐

(경로를 설정하지 않았으면 삭제됨, /이라고 주면 삭제되지 않음)

```jsp
<h3>쿠키값 전체 삭제하기</h3>

<% 
	Cookie[] cookies = request.getCookies();
	if(cookies != null && cookies.length>0 ){
		for(int i=0;i<cookies.length;i++){
			Cookie cookie = new Cookie(cookies[i].getName(), "");
			cookie.setMaxAge(0);
			response.addCookie(cookie);
		}
	}
%>

name 쿠키값을 삭제했습니다
```

### Cookie Domain

#### Why Use setDomain()?

기본적으로 쿠키는 그 쿠키를 생성한 서버에만 전송됨

예를들어 http://xxx.com에 연결해서 생성된 쿠키는 다른 사이트로 연결할 때는 전송되지 않고 http://xxx.com에 연결할때만 전송됨

하지만 같은 도메인을 사용하는 모든 서버에 쿠키를 보내야 할 때가 있음 (www.xxx.com &#8594; mail.xxx.com / zzz.xxx.com서버로)

이럴때 setDomain()메서드를 사용함

#### Cookie Domain Basic

**setDomain() : 생성한 쿠키를 전송할 수 있는 도메인을 지정**

1. .somehost.com : 점으로 시작하는 경우 관련 도메인에 모두 쿠키를 전송

    ex) .somehost.com &#8594; (mail.somehost.com / www.somehost.com / javacan.somehost.com) 에 모두 쿠키 전송

2. www.somehose.com : 특정 도메인에 대해서만 쿠키를 전송

&#9656; 주의할점은 setDomain()의 값으로 현재 서버의 도메인 및 상위 도메인만 전달할 수 있다는 것 

ex) mail.somehost.com 은 (mail.somehost.com / .somehost.com)은 가능하지만 (www.somehost.com)와 같은 다른 주소값은 쿠키 생성 불가

syntax
{: .label .mt-2}
```jsp
<%
    Cookie cookie1 = new Cookie("id", "sohayng");
    cookie1.setDomain("anonymous.com");
    response.addCookie(cookie1);
%>
```

#### Example

**도메인이 있고, 없고, 다른 도메인을 사용하는 쿠키 3개를 생성해 웹 브라우저에 저장되는지 확인**

```jsp
<%

Cookie cookie1 = new Cookie("id", "cookie1_value");   //도메인이 anonymous.com인 id 쿠키를 추가
cookie1.setDomain("anonymous.com");
response.addCookie(cookie1);

Cookie cookie2 = new Cookie("only", "cookie2_value");  // 도메인을 설정하지 않은 only 쿠키 추가
response.addCookie(cookie2);

Cookie cookie3 = new Cookie("invalid", "cookie3_value");   //도메인이 www.daum.net인 invalid 쿠키 추가
cookie3.setDomain("www.daum.net");
response.addCookie(cookie3);

%>

<p>생성된 쿠키 이름 = 쿠키 값 [ 쿠키 도메인 ]</p>
<%= cookie1.getName() %> = <%= cookie1.getValue() %> [<%= cookie1.getDomain() %>]<br>
<%= cookie2.getName() %> = <%= cookie2.getValue() %> [<%= cookie2.getDomain() %>]<br>
<%= cookie3.getName() %> = <%= cookie3.getValue() %> [<%= cookie3.getDomain() %>]<br> //웹브라우저에 저장되지 않음
```

![](https://gekdev.github.io/docs/jsp/example/cookie2.jpg)

세번째 쿠키가 저장되지 않는 이유
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
웹 브라우저가 타 도메인으로 지정한 쿠키를 받지 않는 이유는 보안 문제 때문임

어떤 서버의 프로그램이 쿠키 값으로 보안 정책을 하고 있는데 다른 서버에서 쿠키 값을 마음대로 변경할 수 있다면 보안정책이 뚫리게 됨

이런 이유로, 웹 브라우저는 현재 서버의 도메인과 다른 도메인에 대한 쿠키 생성은 허용하지 않음
</div>

### Cookie Path

#### Cookie Path Basic

도메인이 쿠키를 공유할 도메인 범위를 지정한다면, 경로는 쿠키를 공유한 기준 경로를 지정

쿠키의 경로(URL에서 도메인 이후의 부분에 해당)를 지정할 때에는 Cookie 클래스의 setPath()를 이용

쿠키는 지정한 경로 또는 그 하위 경로에만 전송

쿠키의 경로
{: .label .mt-2}
<div class="code-example" markdown="1">
http://localhost:8088/chap09/path2/view.jpg 여기에서 경로는 서버이후부터인 /chap09/path2/view.jpg을 나타냄 

쿠키에서 사용하는 경로는 디렉터리 수준의 경로를 사용하기 때문에 '/', '/chap09', '/chap09/path2/'등을 쿠키 경로로 사용
</div>

syntax
{: .label .mt-2}
```jsp
<%
    Cookie cookie1 = new Cookie("name", "value");
    cookie.setPath(경로);
%>
```

#### Example

**각각 경로를 다르게 한 쿠키4개를 생성해서 쿠키의 목록을 보기**

경로를 지정하지 않은 쿠키는 쿠키가 생성된 url의 경로 부분을 사용해서 쿠키를 저장함

```jsp
<%@ page import="java.net.URLEncoder"%>
...

<h3>쿠키경로 지정하기</h3>

<%
    Cookie cookie1 = new Cookie("path1", URLEncoder.encode("경로:/basic/jsp08_cookies/path1", "utf-8"));
    cookie1.setPath("basic/jsp08_cookies/path1");
    response.addCookie(cookie1);

    Cookie cookie2 = new Cookie("path2", URLEncoder.encode("경로:", "utf-8"));
    response.addCookie(cookie2);

    Cookie cookie3 = new Cookie("path3", URLEncoder.encode("경로:/", "utf-8"));
    cookie3.setPath("/");
    response.addCookie(cookie3);

    Cookie cookie4 = new Cookie("path4", URLEncoder.encode("경로:/basic/jsp08_cookies/path2", "utf-8"));
    cookie4.setPath("basic/jsp08_cookies/path2");
    response.addCookie(cookie4);
%>

<p>쿠키이름 = 쿠키 값 [쿠키 경로]</p>
<%= cookie1.getName() %> = <%=cookie1.getValue() %> [<%= cookie1.getPath() %>] <br>
<%= cookie2.getName() %> = <%=cookie2.getValue() %> [<%= cookie2.getPath() %>] <br>
<%= cookie3.getName() %> = <%=cookie3.getValue() %> [<%= cookie3.getPath() %>] <br>
<%= cookie4.getName() %> = <%=cookie4.getValue() %> [<%= cookie4.getPath() %>] <br>
```

![](https://gekdev.github.io/docs/jsp/example/cookie3.jpg)

1. 같은 레벨의 경로에서(jsp08_cookies) 쿠키보기

    &#9656; 경로가 지정이 안되어있거나(같은 레벨의 경로), /인 쿠키만 출력됨
    
    ![](https://gekdev.github.io/docs/jsp/example/cookiespath1.jpg)

2. 아래 레벨의 경로1(path1)에서 쿠키보기

    &#9656; 경로 지정 X, 경로 /, 경로 path1 출력 (path2출력 X)

    ![](https://gekdev.github.io/docs/jsp/example/path1.jpg)

3. 아래 레벨의 경로2(path2)에서 쿠키보기

    &#9656; 경로 지정 X, 경로 /, 경로 path2 출력 (path1출력 X)

    ![](https://gekdev.github.io/docs/jsp/example/path2.jpg)

### Effective Time for Cookies

**쿠키는 유효시간이 있음** 

&#9656; 쿠키의 유효시간을 지정하지 않으면 웹 브라우저를 종료할 때 쿠키를 함께 삭제

&#9656; 웹 브라우저 종료 후 다시 웹 브라우저를 실행하면 삭제한 쿠키는 서버에 전송되지 않음

&#9656; 쿠키의 유효시간을 정해놓으면 그 유효시간 동안 쿠키가 존재하며, 웹 브라우저를 종료해도 유효시간이 지나지 않으면 쿠키를 삭제하지 않음

&#9656; 유효 시간을 지정하려면 setMaxAge()메서드를 사용(초 단위로 유효시간을 지정)

syntax
{: .label .mt-2}
```jsp
<%
    Cookie cookie = new Cookie("time", "1hour");
    cookie.setMaxAge(초단위 시간); 
    response.addCookie(cookie);
%>
```

#### Example

**쿠키 유효시간(1시간) 설정하기**

```jsp
<%
    Cookie cookie = new Cookie("time", "1hour");
    cookie.setMaxAge(60*60);        // 60초 * 60분 = 1시간
    response.addCookie(cookie);
%>
```

![](https://gekdev.github.io/docs/jsp/example/1hour.jpg)

### Cookie and Header

response.addCookie()로 쿠키를 추가하면 쿠키 유효시간 설정했을 때의 이미지 처럼 실제로 Set-Cookie 헤더를 통해 전달됨

한개의 Set-Cookie 헤더는 한 개의 쿠키값을 전달함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
쿠키이름=쿠키값; Domain=도메인값; Path=경로값; Expires=GMT형식의만료일시
</div>

![](https://gekdev.github.io/docs/jsp/example/cookies.jpg)

Cookie and Buffer
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
출력 버퍼에 저장되어 있는 내용을 플러시해서 웹 브라우저에 데이터가 전송되면 그 다음부터는 응답 헤더에 새로운 값을 추가할 수 없는것과 마찬가지로

쿠키는 응답 헤더를 사용해서 웹 브라우저에 전달하기 때문에 쿠키 역시 출력 버퍼가 플러시 된 이후에는 새롭게 추가할 수 없음

**따라서 쿠키는 출력 버퍼를 플러시하기 전에 출력해야 함**
</div>

---

## Utility Class for Cookie Processing

**쿠키 처리를 위한 유틸리티 클래스**

### Why Use Utility Class for Cookie?

특정 쿠키의 값을 읽을려면 [위에서 설명한것]()과 같이 쿠키 이름값에 따라 if, else if문을 작성해야 함

이런 구조는 사용할 쿠키가 많아질수록 if-else코드가 복잡해져서 문제가 생김

따라서 보조 유틸리티 클래스(직접 생성한 쿠키 클래스)를 사용해서 작성하면 더욱 편리하게 작성할 수 있음

### Cookies.java

**쿠키를 만들고, 확인하고, 가져오는 쿠키 클래스 생성하기**

```java
package com.lec.cookie;

import java.net.URLDecoder;
import java.net.URLEncoder;
import java.util.HashMap;
import java.util.Map;
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServletRequest;

public class Cookies {

	// 1. 쿠키를 <쿠키이름, Cookie객체> 쌍 형태로 저장하는 맵을 생성
	private Map<String, Cookie> cookieMap = new HashMap<>();
	
	// 2. Cookies 생성자
	public Cookies(HttpServletRequest req) {
		Cookie[] cookies = req.getCookies();	//파라미터로 전달받은 req로 쿠키를 읽어 
		if(cookies!=null) {
			for(int i=0;i<cookies.length;i++) {
				cookieMap.put(cookies[i].getName(), cookies[i]);	//각 쿠키객체를 cookieMap에 저장함 
			}
		}
	}
	
	// 3. Cookies 게터 메서드 (쿠키 가져오기)
	// 3-1) cookieMap에서 지정한 이름의 Cookie객체를 구함
	public Cookie getCookie(String name) {
		return cookieMap.get(name);	//이름이 존재하지 않으면 null
	}
	
	// 3-2) 도메인을 설정하지 않은 only 쿠키를 추가
	public String getValue(String name) throws Exception{
		Cookie cookie = cookieMap.get(name);
		if(cookie==null) return null;
		return URLDecoder.decode(cookie.getValue(),"utf-8");
	}
	
	// 4. Cookies 메서드 (쿠키 확인하기)
	// 4-1) 지정한 이름의 쿠키가 존재하는 경우 true, 아니면 false리턴
	public boolean exists(String name) {
		return cookieMap.get(name) != null;
	}
	
	// 5. Cookies 메서드 (쿠키 만들기)
	// 5-1) 이름이 name이고 값이 value인 Cookie객체를 생성해서 리턴
	public static Cookie createCookie(String name, String value) throws Exception{
		return new Cookie(name, URLEncoder.encode(value, "utf-8"));
	}

	// 5-2) 이름이 name이고 값이 value, 경로가 path, 유효시간이 maxAge인 Cookie객체를 생성해서 리턴
	public static Cookie createCookie(String name, String value, String path, int maxAge) throws Exception{
		Cookie cookie = new Cookie(name, URLEncoder.encode(value, "utf-8"));
		cookie.setPath(path);
		cookie.setMaxAge(maxAge);
		return cookie;
	}
	
	// 5-3) 이름이 name이고 값이 value, 경로가 path, 도메인이 domain, 유효시간이 maxAge인 Cookie객체를 생성해서 리턴
	public static Cookie createCookie(String name, String value, String path, String domain, int maxAge) throws Exception {
		Cookie cookie = new Cookie(name, URLEncoder.encode(value, "utf-8"));
		cookie.setPath(path);
		cookie.setDomain(domain);
		cookie.setMaxAge(maxAge);
		return cookie;
	}	
}
```

### Generate Cookies using Cookie Class

**쿠키 클래스를 이용한 쿠키 생성**

```jsp
<%@ page import="com.lec.cookie.Cookies"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
   <meta charset="UTF-8">
</head>
<body>

	<h3>java클래스로 Cookie생성하기</h3>

	<%
	response.addCookie(Cookies.createCookie("cookieName1", "쿠키값1"));
	response.addCookie(Cookies.createCookie("cookieName2", "쿠키값2", "/", -1));
	response.addCookie(Cookies.createCookie("cookieName3", "쿠키값3", "/", "xxx.com", -1));
	%>

	<p>java클래스 Cookies로 쿠키를 생성했습니다</p>
	
</body>
</html>
```

### Read Cookies using Cookie Class

**쿠키 클래스를 이용한 쿠키 읽기**

```jsp
<%@ page import="com.lec.cookie.Cookies"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
   <meta charset="UTF-8">
</head>
<body>

	<h3>java클래스로 Cookie읽기</h3>
	
	<%
		Cookies cookies = new Cookies(request); //request 기본객체로부터 쿠키 정보를 얻어옴
	%>
	
	<p>cookieName1 쿠키값 : <%= cookies.getValue("cookieName1") %></p>
	<% if (cookies.exists("cookieName2")){ %>    <!--쿠키가 존재하는지 확인-->
	<p>cookieName2 쿠키값 : <%= cookies.getValue("cookieName2") %></p>
	<%} %>
	<% if (cookies.exists("cookieName3")){ %>   <!--값만 사용할 경우 getValue 메서드 사용 (쿠키를 가져올수도 있음)-->
	<p>cookieName3 쿠키값 : <%= cookies.getValue("cookieName3") %></p>
	<%} %>
	
</body>
</html>
```

---

## Login with Cookie

**웹 사이트의 기본 기능중 하나, 로그인 상태를 확인할 때 가장 많이 사용하는 방법**

쿠키를 이용하면 다음과 같은 방법으로 로그인 상태를 유지할 수 있음

1. 로그인에 성공하면 특정 이름을 갖는 쿠키를 생성

2. 해당 쿠키가 존재하면 로그인한 상태라고 판단

3. 로그아웃하면 해당 쿠키를 삭제

### Login Form

로그인폼 : 아이디와 비밀번호를 입력할 페이지
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
   <meta charset="UTF-8">
</head>
<body>
	<form action="<%= request.getContextPath() %>/jsp08_cookies/jsp08_09_login.jsp" method="post">
		<p>아이디 : <input type="text" name="id" size="10" /></p>
		<p>비밀번호 : <input type="password" name="pw" size="10" /></p>
		<p><input type="submit" value="로그인"/></p>
	</form>
</body>
</html>
```

### Login Processing

**아이디와 암호가 같으면(id=pw) 로그인에 성공한다고 가정**

추가 ) 로그인했을 때 로그아웃 버튼을 처리할 수 있게 만들었음

로그인 : 아이디와 비밀번호를 처리 페이지
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="com.lec.cookie.Cookies"%>
<%
	String id = request.getParameter("id");
	String password = request.getParameter("pw");

	if(id.equals(password)){
		//id와 password가 같으면 로그인에 성공
		response.addCookie(
			Cookies.createCookie("AUTH", id, "/", -1)
		);
%>
		<!DOCTYPE html>
		<html>
		<head>
		   <meta charset="UTF-8"> 
		</head>
		<body>
		<form action="<%= request.getContextPath() %>/jsp08_cookies/jsp08_09_logout.jsp">
			<p>로그인에 성공했습니다</p>
			<input type="submit" value="로그아웃"/>
		</form>
		</body>
		</html>
<% } else { %>
	<script>
		alert("로그인에 실패했습니다");
		history.go(-1);
	</script>
<% } %>
```

### Determining Whether to Login or not

**AUTH 쿠키가 존재하면 로그인했다고 판단**

로그인 여부 검사
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="com.lec.cookie.Cookies"%>
<!DOCTYPE html>
<html>
<head>
   <meta charset="UTF-8">
</head>
<body>
	<h2>로그인 여부 검사</h2>
	
	<%
	Cookies cookies = new Cookies(request); //request 기본객체로부터 쿠키 정보를 얻어옴
	if(cookies.exists("AUTH")){
	%>
		<p>아이디 "<%= cookies.getValue("AUTH")%>"로 로그인한 상태 </p>
	<%
	} else {
	%>
		<p>로그인하지 않은 상태</p>
	<%
	}
	%>
</body>
</html>
```

Note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
아이디를 평문 형태로 쿠키 값으로 사용하면 보안에 큰 문제가 생김

웹 브라우저는 개발도구를 사용하면 쿠키 값을 쉽게 변경할 수 있기 때문에 개발도구를 사용하면 다른 아이디로 서버에 접근할 수 있음

이런 이유로 쿠키에 아이디를 저장할 때에는 평문으로 저장하지 않고 다양한 암호화 방식을 혼합해서 저장
</div>

### Logout Processing

**로그아웃을 하려면 쿠키를 삭제하면 됨**

&#8594; AUTH 쿠키의 유효시간을 0으로 지정하면 됨 

로그아웃
{: .label .label-purple .mt-2}
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="com.lec.cookie.Cookies"%>
<!DOCTYPE html>
<html>
<head>
   <meta charset="UTF-8">
</head>
<body>

<%
	response.addCookie(Cookies.createCookie("AUTH", "", "/", 0));
%>

<p>로그아웃 했습니다</p>

</body>
</html>
```
