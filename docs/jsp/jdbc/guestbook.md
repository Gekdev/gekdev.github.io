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

1. Dynamic Web Project 생성

2. 웹 서버 유형 Tomcat v9.0으로 설정하기

3. 라이브러리 가져오기 

![](https://gekdev.github.io/docs/jsp/example/lib.jpg)
    
4. 새로운 데이터베이스 생성 하기

```sql
create database guestbook;
```

5. 새로운 테이블 생성
```sql
create table guestbook_message (
    message_id int not null auto_increment primary key,
    guest_name varchar(50) not null,
    password varchar(10) not null,
    message text not null
) engine=InnoDB default character set = utf8;
```

6. Message 클래스 생성

**메세지의 내용, 게터세터, 비밀번호 메서드 생성**

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

7. MessageDAO 클래스 생성

**메세지 싱글톤 인스턴스를 가지고 메세지의 메서드들을 정의**

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
			return rs.getInt(1);
		} finally {
			JDBCUtil.close(stmt, rs);
		}
	}
	
	public List<Message> selectList(Connection conn, int firstRow, int endRow) throws SQLException {
		
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		String sql = "select * from guestbook_message order by message_id desc limit ?, ?";
		
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setInt(1, firstRow);
			pstmt.setInt(2, endRow);
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