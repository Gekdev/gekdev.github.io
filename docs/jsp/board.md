
## 회원 관련 주요 기능

회원제 게시판은 크게 회원 관련 기능과 게시판 기능으로 구성됨

* 회원 관련 기능 

    * 회원 가입
    
    * 회원 정보 수정하기
    
        * 로그인/로그아웃
        
        * 로그인 한 사람만 특정 기능 수행하기
    
* 게시판기능

---

## 회원 관련 기능

### 데이터베이스 만들기

1. mariaDB에 board 데이터베이스 생성

    ```sql
    create database board;
    ```

2. board 데이터베이스에 member 테이블 생성

    ```sql
    DROP TABLE IF EXISTS `member_copy1`;
    CREATE TABLE `member_copy1`  (
      `ID` varchar(50) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
      `NAME` varchar(50) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
      `PASSWORD` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
      `REGNUMBER` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
      `MILEAGE` int(10) NULL DEFAULT 0,
      `REGDATE` datetime NOT NULL DEFAULT curdate,
      PRIMARY KEY (`ID`) USING BTREE
    ) ENGINE = InnoDB CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
    ```

### Dynamic Web Project 생성

jsp08_member로 생성

라이브러리는 connection pool 라이브러리 3개와, DB커넥터, JSTL을 가져옴(총 5개)

![](boardlib.jpg)

### Member.dto

**Member 데이터베이스에서 가져올 값들을 저장하거나, 가져오거나, 비교할 객체 생성**

Member.java
{: .label .label-purple .mt-2}
```java
package com.lec.member.dto;

import java.util.Date;

public class Member {
	
	//Member 데이터베이스에서 가져올 값들을 저장할 변수 필드
	private String id;
	private String password;
	private String name;
	private String regNumber;
	private int mileage;
	private Date regDate;
	
	//생성자
	public Member(String id, String password, String name, String regNumber, int mileage) {
		this.id = id;
		this.password = password;
		this.name = name;
		this.regNumber = regNumber;
		this.mileage = mileage;
	}

	//GETTER, SETTER
	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public String getPassword() {
		return password;
	}

	public void setPassword(String password) {
		this.password = password;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getRegNumber() {
		return regNumber;
	}

	public void setRegNumber(String regNumber) {
		this.regNumber = regNumber;
	}

	public int getMileage() {
		return mileage;
	}

	public void setMileage(int mileage) {
		this.mileage = mileage;
	}

	public Date getRegDate() {
		return regDate;
	}

	public void setRegDate(Date regDate) {
		this.regDate = regDate;
	}

	//toString() 재정의
	@Override
	public String toString() {
		return "Member [id=" + id + ", password=" + password + ", name=" + name + "]";
	}
	
	//동등비교를 할 함수 재정의
	@Override
	public boolean equals(Object obj) {
		if(this == obj) return true;
		if(obj == null) return false;
		if(getClass() != obj.getClass()) return false;	//객체를 비교해서 다르면 다른 객체
	
		Member other = (Member) obj;
	
		if(id == null) {
			if(other.id != null) return false;
		}else if(!id.equals(other.id)) {
			return false;
		}
		
		if(name == null) {
			if(other.name != null) return false;
		}else if(!name.equals(other.name)) {
			return false;
		}
			
		if(password == null) {
			if(other.password != null) return false;
		}else if(!password.equals(other.password)) {
			return false;
		}
		
		if(regNumber == null) {
			if(other.regNumber != null) return false;
		}else if(!regNumber.equals(other.regNumber)) {
			return false;
		}
		
		if(regDate == null) {
			if(other.regDate != null) return false;
		}else if(!regDate.equals(other.regDate)) {
			return false;
		}
		
		if(mileage != other.mileage) {
			return false;
		}
		
		//위 조건을 다 통과해야 true
		return true;
	}
	
	@Override
	public int hashCode() {
		final int seed = 42;
		int result = 1;
		result = seed * result + ((id==null) ? 0 : id.hashCode());
		result = seed * result + ((name==null) ? 0 : name.hashCode());
		result = seed * result + ((password==null) ? 0 : password.hashCode());
		result = seed * result + ((regNumber==null) ? 0 : regNumber.hashCode());
		result = seed * result + ((regDate==null) ? 0 : regDate.hashCode());
		result = seed * result + mileage;
		return result;
	}
}
```

### 드라이버 로딩

DB와 연동을 하기 위해서 커넥션 관련 코드를 작성해야 함

DBConnectListener.java
{: .label .label-purple .mt-2}
```java
package com.lec.member.listener;

import javax.servlet.ServletContext;
import javax.servlet.ServletContextEvent;
import javax.servlet.ServletContextListener;

public class DBConnectListener implements ServletContextListener{

	public DBConnectListener() {}
	
	@Override
	public void contextInitialized(ServletContextEvent sce) {
		// web.xml의 Context 읽기
		ServletContext context = sce.getServletContext();
		// context의 매개변수 driverClass가져오기 = org.mariadb.jdbc.Driver
		String driverClass= context.getInitParameter("driverClass");		
		// Driver 로딩하는 try/catch문
		try {
			Class.forName(driverClass);
		} catch (ClassNotFoundException e) {
			System.out.println("DB 로딩 실패!");
			e.printStackTrace();
		}
	}
	
	@Override
	public void contextDestroyed(ServletContextEvent sce) {
		ServletContextListener.super.contextDestroyed(sce);
	}
	
}
```

### web.xml 초기화 파라미터 지정

위 서블릿 컨텍스트 리스너를 등록하기 위해 web.xml에 등록해야 함

DBConnectListener는 컨텍스트 초기화 파라미터를 이용해서 커넥션 풀 설정정보를 생성하므로 초기화 파라미터 값을 설정함

web.xml
{: .label .label-purple .mt-2}
```xml
<listener>
    <listener-class>com.lec.member.listener.DBConnectListener</listener-class>
</listener>

<context-param>
    <param-name>driverClass</param-name>
    <param-value>org.mariadb.jdbc.Driver</param-value>
</context-param>  

<context-param>
    <param-name>url</param-name>
    <param-value>jdbc:mariadb://localhost:3306/board</param-value>
</context-param>

<context-param>
    <param-name>user</param-name>
    <param-value>root</param-value>
</context-param>

<context-param>
    <param-name>pass</param-name>
    <param-value>12345</param-value>
</context-param>
```

### server.xml 파일 경로 지정

서버에 있는 다른 dynamic web project 지우고 jsp08_member만 등록

server.xml 에서 Context docBase="jsp08_member" path="/" 로 변경하면 폴더명을 지정하지 않고 바로 index.jsp를 찾음

### index.jsp Form

index.jsp

다른 폼으로 들어가는 가장 큰 jsp 폼을 생성

index.jsp
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
![](indexhtml.jpg)
</div>
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head> 
</head>
<body>
<h3>회원관리</h3>
    <!--회원가입-->
    <input type="button" value="회원가입" onclick="location.href='/register_form.jsp'"/>
    <!--로그인-->
    <input type="button" value="로그인" onclick="location.href='/login_form.jsp'"/>
    <!--회원조회-->
    <input type="button" value="회원조회" onclick="location.href='/list_member.jsp'"/>
</body>
</html>
```

### 회원가입 로직

index에서 회원가입을 누르면 register_form.jsp로 들어옴


---

## 게시판 기능
