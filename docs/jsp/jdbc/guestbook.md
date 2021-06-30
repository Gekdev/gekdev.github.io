---
layout: default
title: GuestBook
parent: JDBC / MariaDB
grand_parent : JSP
nav_order: 2
---

# JDBC GuestBook
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### GuestBook Setting

1. **Dynamic Web Project 생성**

2. **웹 서버 유형 Tomcat v9.0으로 설정하기**

3. **라이브러리 가져오기** 

    ![](https://gekdev.github.io/docs/jsp/example/lib.jpg)

### Create New Database 

1. **새로운 데이터베이스 생성 하기**

    ```sql
    create database guestbook;
    ```

2. **새로운 테이블 생성**

    ```sql
    create table guestbook_message (
        message_id int not null auto_increment primary key,
        guest_name varchar(50) not null,
        password varchar(10) not null,
        message text not null
    ) engine=InnoDB default character set = utf8;
    ```

3. **테이블에 1000건의 데이터 넣기**

    ```sql
    delimiter //
    begin not atomic 
        declare i int default 1;
        while(i <= 1001) do
            insert into guestbook_message(guest_name, password, message)
                values(concat('작성자_',i), '12345', concat('메시지내용_', i));
                set i = i + 1;
        end while;
    end;
    ```

4. **테이블 조회하기**

    ```sql
    select * from guestbook_message order by message_id desc limit 0, 10;   //10건씩 나오는지 확인

    select count(*) from guestbook_message; //마지막 건수 확인
    ```

### Create Message Model

**메시지의 내용, 게터세터, 비밀번호 메서드 생성**

```java
package com.lec.web.model;

public class Message {
	
	private int id;
	private String guestName;
	private String password;
	private String message;
	
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	public String getGuestName() {
		return guestName;
	}
	public void setGuestName(String guestName) {
		this.guestName = guestName;
	}
	public String getPassword() {
		return password;
	}
	public void setPassword(String password) {
		this.password = password;
	}
	public String getMessage() {
		return message;
	}
	public void setMessage(String message) {
		this.message = message;
	}
	
	public boolean hasPassword(){
		return password!=null && !password.isEmpty();
	}
	
	public boolean matchPassword(String pwd) {
		return password!=null && password.equals(pwd);
	}

}
```

### Create JDBC Package

1. **데이터베이스 커넥션 생성 객체 생성**

    JDBC를 이용해서 데이터베이스를 사용하려면 데이터베이스와 연결된 커넥션

    ConnectionProvider
    {: .label .label-purple .mt-2}
    ```java
    package com.lec.web.jdbc;

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.SQLException;

    public class ConnectionProvider {

        public static Connection getConnection() throws SQLException {
            return DriverManager.getConnection("jdbc:apache:commons:dbcp:guestbook");
        }
    }
    ```

2. **드라이버 로딩, 커넥션풀을 생성하는 객체 생성**

    커넥션 풀을 사용해서 생성함

    DBCPInit
    {: .label .label-purple .mt-2}
    ```java
    package com.lec.web.jdbc;

    import java.sql.DriverManager;

    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServlet;

    import org.apache.commons.dbcp2.ConnectionFactory;
    import org.apache.commons.dbcp2.DriverConnectionFactory;
    import org.apache.commons.dbcp2.DriverManagerConnectionFactory;
    import org.apache.commons.dbcp2.PoolableConnection;
    import org.apache.commons.dbcp2.PoolableConnectionFactory;
    import org.apache.commons.dbcp2.PoolingDriver;
    import org.apache.commons.pool2.impl.GenericObjectPool;
    import org.apache.commons.pool2.impl.GenericObjectPoolConfig;

    public class DBCPInit extends HttpServlet {

        @Override
        public void init() throws ServletException {
            loadJDBCDriver();
            initConnectionPool();
        }

        private void loadJDBCDriver() {
            String driverClass = getInitParameter("jdbcdriver");	

            try {
                Class.forName(driverClass);
            } catch (ClassNotFoundException e) {
                throw new RuntimeException("JDBC 드라이버 로딩 실패!!");		
            }
        }

        private void initConnectionPool() {

            String url =  getInitParameter("url");
            String usr =  getInitParameter("user");
            String pwd =  getInitParameter("pass");

            // A. Connection Pool 생성
            // 1. 커넥션풀이 새로운 커넥션을 생성할 떄 사용하는 커넥션팩토리를 생성
            ConnectionFactory connFactory = new DriverManagerConnectionFactory(url, usr, pwd);

            // 2. PoolableConnection을 생성하는 팩토리생성 DBCP는 커넥션풀에 커넥션을 보관할 떄 PoolableConnection을 사용
            // 이 클래스는 내부적으로 커넥션을 보관하고 있으며 커넥션풀을 관리하는데 필요한 기능을 제공
            // 예를 들어서 connection을 close하면 커넥션을 완전히 종료하지 않고 커넥션풀에 connection을 반환
            PoolableConnectionFactory poolFactory = new PoolableConnectionFactory(connFactory, null);

            // 3. 커넥션이 유효한지여부를 검사하기 위한 SQL을 지정
            poolFactory.setValidationQuery("select 1"); // 커넥션유효성을 검사 : mariadb or mysql;
            // poolFactory.setValidationQuery("select * from dual"); // oracle

            // B. 커넥션플의 설정정보
            // 1. 설정정보를 관리할 객체를 생성
            GenericObjectPoolConfig poolConfig = new GenericObjectPoolConfig();		
            // 2. 커넥션의 검사주기
            poolConfig.setTimeBetweenEvictionRunsMillis(1000l * 60l * 5l); // 사용가능한 검사주기
            // 3. 풀에 보관중인 커넥션유효여부를 검사할지 안할지 여부설정
            poolConfig.setTestWhileIdle(true);
            // 4. 커넥션의 최소 갯수
            poolConfig.setMinIdle(4);
            // 5. 커넥션의 최대 갯수
            poolConfig.setMaxIdle(50);

            // C. 커넥션풀을 생성
            // 1. PoolableConnection을 생성할 떄 사용할 커넥션팩토리와 설정정보를 이용해서 커넥션풀을 생성
            GenericObjectPool<PoolableConnection> connPool = new GenericObjectPool<>(poolFactory, poolConfig);
            // 2. 생성한 커넥션풀을 연결
            poolFactory.setPool(connPool);

            // D. 커넥션풀을 제공할 JDBC드라이버 등록
            try {
                Class.forName("org.apache.commons.dbcp2.PoolingDriver");
                PoolingDriver driver = (PoolingDriver) DriverManager.getDriver("jdbc:apache:commons:dbcp:");
                String poolName = getInitParameter("poolName");
                driver.registerPool(poolName, connPool);
            } catch (Exception e) {
                throw new RuntimeException();
            }	
        }
    }
    ```

3. **커넥션을 종료하거나 롤벡할 수 있는 객체 생성**

    JDBCUtil
    {: .label .label-purple .mt-2}
    ```java
    package com.lec.web.jdbc;

    import java.sql.Connection;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;

    public class JDBCUtil {

        public static void close(ResultSet rs) {
            try { 
                if(rs!=null) rs.close();
            } catch (SQLException e) {}
        }

        public static void close(Statement stmt) {
            try { 
                if(stmt!=null) stmt.close();
            } catch (SQLException e) {}
        }

        public static void close(Connection conn) {
            try { 
                if(conn!=null) conn.close();
            } catch (SQLException e) {}
        }

        public static void close(Connection conn, Statement stmt) {
            try { 
                if(stmt!=null) stmt.close();
                if(conn!=null) conn.close();
            } catch (SQLException e) {}
        }

        public static void close(Statement stmt, ResultSet rs) {
            try { 
                if(rs!=null) rs.close();
                if(stmt!=null) stmt.close();
            } catch (SQLException e) {}
        }

        public static void close(Connection conn, Statement stmt, ResultSet rs) {
            try { 
                if(rs!=null) rs.close();
                if(stmt!=null) stmt.close();
                if(conn!=null) conn.close();
            } catch (SQLException e) {}
        }

        public static void rollback(Connection conn) {
            try { 
                if(conn!=null) conn.rollback();
            } catch (SQLException e) {}
        }	
    }
    ```

### MessageDAO 클래스 생성

Statement 생성, 쿼리 실행, 쿼리 실행결과 리턴

**메시지 싱글톤 인스턴스를 가지고 메세지의 메서드들을 정의**

```java
package com.lec.web.dao;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

import com.lec.web.jdbc.JDBCUtil;
import com.lec.web.model.Message;

public class MessageDAO {

	//singleton pattern
	private MessageDAO() {}
	private static MessageDAO messageDAO = new MessageDAO();
	
	public static MessageDAO getInstance() {
		return messageDAO;
	}
	
    //select 메세지 리턴
	public Message select(Connection conn, int messageId) throws SQLException{
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		String sql = "select * form guestbook_message where message_id = ?";
		try {
			pstmt= conn.prepareStatement(sql);
			pstmt.setInt(1, messageId);
			rs=pstmt.executeQuery();
			if(rs.next()) return makeMessage(rs);
			else return null;
		} finally {
			JDBCUtil.close(pstmt, rs);
		}
	}
	
	public Message makeMessage(ResultSet rs) throws SQLException {
		Message message = new Message();
		message.setId(rs.getInt("message_id"));
		message.setGuestName(rs.getString("guest_name"));
		message.setPassword(rs.getString("password"));
		message.setMessage(rs.getString("message"));
		return message;
	}
	
	public int insert(Connection conn, Message message) throws SQLException {
		
		PreparedStatement pstmt = null;
		String sql = "insert into guestbook_message(guest_name, password, message) values(?,?,?)";
		
		try {
			pstmt=conn.prepareStatement(sql);
			pstmt.setString(1, message.getGuestName());
			pstmt.setString(2, message.getPassword());
			pstmt.setString(3, message.getMessage());
			return pstmt.executeUpdate(); //추가된 건수(int)가 리턴 
		} finally {
			JDBCUtil.close(pstmt);
		}
	}
	
	public int delete(Connection conn, int messageId) throws SQLException  {
		
		PreparedStatement pstmt = null;
		String sql = "delete from guestbook_message where message_id =?";
		
		try {
			pstmt=conn.prepareStatement(sql);
			pstmt.setInt(1, messageId);
			return pstmt.executeUpdate(); //추가된 건수(int)가 리턴 
		} finally {
			JDBCUtil.close(pstmt);
		}
		
	}
	public int update(Connection conn, int messageId, String message) throws SQLException {
		
		PreparedStatement pstmt = null;
		String sql = "update guestbook_message set message = ? " + " where message_id =?";
		
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, message);
			pstmt.setInt(2, messageId);
			return pstmt.executeUpdate();
		} finally {
			JDBCUtil.close(pstmt);
		}
	}
	
	public int selectCount(Connection conn) throws SQLException {
		
		Statement stmt = null;
		ResultSet rs = null;
		String sql = "select count(*) from guestbook_message";
		
		try {
			stmt = conn.createStatement();
			rs = stmt.executeQuery(sql);
			rs.next();
			return rs.getInt(1);
		} finally {
			JDBCUtil.close(stmt, rs);
		}
	}
	
	public List<Message> selectList(Connection conn, int start, int end) throws SQLException {
		
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		String sql = "select * from guestbook_message order by message_id desc limit ?, ?";
		
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setInt(1, start);
			pstmt.setInt(2, end);
			rs = pstmt.executeQuery();
			if(rs.next()) {
				List<Message> messageList = new ArrayList<>();
				do {
					messageList.add(makeMessage(rs));
				} while(rs.next());
				return messageList;
			} else {
				return Collections.emptyList();
			}
			
		} finally {
			JDBCUtil.close(pstmt, rs);
		}
	}
}
```

list
{: .label .label-purple .mt-2}
```java
<%@ page import="com.lec.web.service.MessageListView"%>
<%@ page import="com.lec.web.service.GetMessageListService"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%
	int pageNumber = 1;
	if(request.getParameter("page") != null){
		pageNumber = Integer.parseInt(request.getParameter("page")); 
	}
	
	GetMessageListService messageListService = GetMessageListService.getInstance();
	MessageListView view_data = messageListService.getMessageList(pageNumber);
%>
<c:set var="view_data" value="<%= view_data %>"/>
<!DOCTYPE html>
<html>
<head>
   <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1">
     <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
     <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.0/css/all.css" integrity="sha384-lZN37f5QGtY3VHgisS14W3ExzMWZxybE1SJSEsQp9S+oqd12jhcu+A56Ebc1zFSJ"
      crossorigin="anonymous"> 
     <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
     <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>
     <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>   
</head>
<body>
	<div class="writemessage">
		<!--방명록을 입력할 폼-->
		<form class="form-inline" action="writeMessage.jsp" method="post">
			 <!--guestName 입력-->
	         <div class="input-group mb-2 mr-sm-2">
	           <div class="input-group-prepend">
	             <span class="input-group-text"><i class="fas fa-user"></i></span>
	           </div>
	          <input type="text" name="guestName" class="form-control"/>
	         </div>
	         
	         <!--password 입력-->
	         <div class="input-group mb-2 mr-sm-2">
	           <div class="input-group-prepend">
	             <span class="input-group-text"><i class="fas fa-lock"></i></span>
	           </div>
	          <input type="password" name="password" class="form-control" />
	         </div>
	         
	         <!--text 입력-->
	         <div class="input-group mb-2 mr-sm-2">
	           <div class="input-group-prepend">
	             <span class="input-group-text"><i class="fas fa-envelope"></i></span>
	           </div>
	          <input type="text" name="text" class="form-control" />
	         </div>
	         
	          <!--등록버튼 입력-->
	        <input type="submit" class="btn btn-primary mb-2" value="메시지 등록"/> 
	     </form>
	 </div>
	 
	 <!--방명록 (데이터베이스 데이터 출력)-->    
     <div class="container" align="center">
	     <h3>방명록</h3>
	     
	     <!--데이터가 없을 경우-->
	     <c:if test="${view_data.isEmpty()}">
	     	<p class="bg-danger text-white">등록된 메시지가 없습니다</p>
	     </c:if>
	    
	     <!--데이터가 있을 경우-->
	     <table class="table table-hover">
			<tr class="table-primary">
				<th>메시지번호</th>
				<th>게스트이름</th>
				<th>비밀번호</th>
				<th>메시지</th>
				<th>삭제</th>
			</tr>
			<!-- 태그이용 -->
			<c:forEach var="message" items="${view_data.messageList}">
			<tr>
				<td>${message.id}</td>
				<td>${message.guestName}</td>
				<td>${message.password}</td>
				<td>${message.message}</td>
				<td><a href="confirmDelete.jsp?id=${message.id}" class="btn btn-danger btn-sm">X</a></td>
			</tr>
			</c:forEach>
		</table>
		</div>
		
		<!--번호-->
		<div class="container" align="center">
			<ul class="pagination justify-content-center">
				<li class="page-item"><a href="#" class="page-link"><i class="fas fa-backward"></i></a></li>
				<c:forEach var="page_num" begin="1" end="${view_data.totalCount}">
					<li class="page-item"><a href="list.jsp?page=${page_num}" class="page-link">${page_num}</a></li>				
				</c:forEach>
			</ul>
		</div>
</body>
</html>
```