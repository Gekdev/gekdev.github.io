---
layout: default
title: Board
parent: JDBC
grand_parent: Java
nav_order: 1
---

# JDBC Board
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## DAO And DTO(VO) Basic

**게시판 프로그램(only Java)을 만들기 위한 기본 개념과 로직을 공부하기**

### DAO (Data Access Object)

1. 개념

    **Database에 접근을 위한 객체라는 의미로 Database에 접근을 하기 위한 로직과 비즈니스 로직을 분리하는 개념**

2. 역할

    **DB를 사용해 데이터를 조회하거나 조작하는 기능을 전담하도록 만든 객체**

    사용자는 자신이 필요한 Interface를 DAO에게 전달하고 DAO는 이 인터페이스를 구현한 객체를 사용자에게 사용할 수 있도록 반환

3. 사용 이유

    DB에 대신 접근을 DAO가 전담하도록 하여 데이터베이스에 엑세스를 DAO에서만 하게되면 다수의 원격호출을 통한 오버헤드를 DTO를 통해 줄일수 있고 다수의 DB호출을 해결할 수 있음 

### DTO (Data Transfer Object, VO Value Object)

1. 개념 

    DTO는 데이터를 교환하는 즉, 데이터를 담는 그릇으로 이해

2. 특징

    일반적으로 DTO는 로직을 가지고 있지 않고 데이터의 속성에 접근하기 위한 getter/setter메서드만 가진 클래스를 말함

3. VO

    동일한 개념이지만 VO는 일반적으로 ReadOnly

---

## Board Application

### 1. Board 테이블 생성 

**Scott에 테이블과 Sequence를 생성함**

```sql
create table scott.board 
(
     bno       number          not null primary key
   , subject    varchar2(100)    not null
   , writer     varchar2(50)   not null
   , crtdate   date         default  sysdate
   , readcnt   number         default    0
   , content   varchar2(256)
);

create sequence scott.board_bno_s;
```

### 2. jdbc.properties 생성

**공통적으로 사용해야 하는 정보들을 따로 Properties 파일에 생성**

아래 파일에서는

1. 데이터베이스에 연결하기 위한 정보들(JDBC 드라이버 클래스, 연결문자열, 데이터베이스ID&PW)
2. SQL 명령문
3. Oracle이외의 데이터베이스 접근 정보들을 적어둠

```properties
jdbc.drv=oracle.jdbc.OracleDriver
jdbc.url=jdbc:oracle:thin:@localhost:1521:XE
jdbc.usr=scott
jdbc.pwd=tiger

insert=insert into board(bno, subject, writer, content) values(board_bno_s.nextval,?,?,?)
select=select * from board
update=update board set subject=?, content=? where bno=?
delete=delete from board where bno=?

mysql.drv=com.mysql.jdbc.Driver
mysql.url=jdbc:mysql://localhost:3306/board
mysql.usr=root
mysql.pwd=12345

mariadb.drv=
mariadb.url=
mariadb.usr=
mariadb.pwd=
```

### 3. Board 프로그램

#### BoardVO : 게시판 Model 클래스

```java
package com.lec.ex02_board;

public class BoardVO {

	private int bno;
	private String subject;
	private String writer;
	private String crtdate;
	private int readcmt;
	private String content;
	
    // 초기화를 따로 시켜줌 (안해도 되는 부분)
	public BoardVO() {
		this.bno =	0;
		this.subject = null;
		this.writer = null;
		this.crtdate = null;
		this.readcmt = 0;
		this.content = null;
	}

    //Getter, Setter
	public int getBno() {
		return bno;
	}

	public void setBno(int bno) {
		this.bno = bno;
	}

	public String getSubject() {
		return subject;
	}

	public void setSubject(String subject) {
		this.subject = subject;
	}

	public String getWriter() {
		return writer;
	}

	public void setWriter(String writer) {
		this.writer = writer;
	}

	public String getCrtdate() {
		return crtdate;
	}

	public void setCrtdate(String crtdate) {
		this.crtdate = crtdate;
	}

	public int getReadcmt() {
		return readcmt;
	}

	public void setReadcmt(int readcmt) {
		this.readcmt = readcmt;
	}

	public String getContent() {
		return content;
	}

	public void setContent(String content) {
		this.content = content;
	}

    //toString()
	@Override
	public String toString() {
		return + bno + "\t\t" + subject + "\t\t" + writer + "\t\t" +  content;
	}	
}
```

#### ConnectionFactory : 데이터 접속 정보를 공통으로 사용하기 위한 클래스

#### BoardDAOService : 게시판 인터페이스

#### BoardDAOImpl : 게시판 구현 클래스

#### BoardFactory : 게시판 생성 클래스 (Singleton)

#### BoardUI : 게시판 처리 프로그램의 화면구성(메뉴)을 담당하는 클래스 

#### Board : 메인클래스