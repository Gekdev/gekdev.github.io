---
layout: default
title: JDBC / MariaDB
parent: JSP
nav_order: 11
has_children: true
---

# JSP JDBC
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSP JDBC

[데이터베이스]()나 [JDBC]()에 대한 설명은 앞에서 이미 설명했기 때문에 넘어가고

이번에 공부할 jsp예제에서 사용할 데이터베이스는 mariaDB이기 때문에 mariaDB를 설치해줘야함

### Download MariaDB

1. 다운받은 파일 실행

    https://mariadb.org/download/

2. 설치 위치 지정 

    **C:\MariaDB 10.5\로 만듦**

    ![](https://gekdev.github.io/docs/jsp/example/setmaria.jpg)
    
3. root 계정의 비밀번호를 입력

    **12345로 만들기**

    ![](https://gekdev.github.io/docs/jsp/example/passmaria.jpg)
    
4. 나머지 그냥 쭉 넘겨서 설치 완료!

[참고페이지](https://offbyone.tistory.com/199)

### JDBC MariaDB Connecter Driver

Java와 DB를 연동하기 위해서는 각 DBMS의 버전에 맞는 JRE 실행환경 라이브러리(커텍터 드라이버)를 Java프로젝트에 추가해야 함

&#9656; MSSQL, MySQL, Maria 등 각각 DB버전에 맞는 실행환경 드라이버를 추가해야 함

&#9656; [mariadb-java-client/2.7.3.jar]()을 다운로드 받으면 됨

<span class="fs-2">
[Download Maria Library](https://mvnrepository.com/artifact/org.mariadb.jdbc/mariadb-java-client/2.7.3){: .btn .btn-outline .mt-2}
</span>

#### Add Library

라이브러리(드라이버)를 추가하는 방법

**&#8594; WEB-INF lib폴더에 .jar파일 끌어넣으면 자동으로 라이브러리가 추가됨**

### navicat connection

1. File &#8594; new Connection &#8594; mariaDB 으로 새로운 커넥션 생성

    ![](https://gekdev.github.io/docs/jsp/example/navimaria.jpg)

2. 새로운 데이터베이스 생성

    ```sql
    create database 생성할_데이터베이스명
    ```

3. 생성된 데이터베이스

    ![](https://gekdev.github.io/docs/jsp/example/newdb.jpg)

### JDBC Program Coding Style

[JDBC Program Creation Steps]()에서도 설명한바와 같이 JDBC프로그램의 전형적인 실행순서는 다음과 같음

1. JDBC 드라이버 로딩

2. 데이터베이스 커넥션 구하기

3. 쿼리 실행을 위한 Statement 객체 생성

4. 쿼리 실행

5. 쿼리 실행결과 사용

6. Statement 종료

7. 데이터베이스 커넥션 종료

예제
{: .label .label-purple .mt-2}
```jsp
<%@page import="java.sql.DriverManager"%>
<%@page import="java.sql.Statement"%>
<%@page import="java.sql.ResultSet"%>
<%@page import="java.sql.Connection"%>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<body>
<h3>회원정보</h3>
<%
	//1. JDBC 드라이버 로딩
	Class.forName("org.mariadb.jdbc.Driver");

	Connection conn = null;
	Statement stmt = null;
	ResultSet rs = null;
	
	try {
		String drv = "jdbc:mariadb://localhost:3306/jspstudy";
		String usr = "root";
		String pwd = "12345";
		String sql = "select * from member";
		
		//2. 데이터베이스 커넥션 생성
		conn = DriverManager.getConnection(drv, usr, pwd);
		
		//3. Statement 생성
		stmt = conn.createStatement();
		//4. 쿼리 실행
		rs = stmt.executeQuery(sql);
		
		//5. 쿼리 실행결과 출력
		if(rs.next()) {
%> 
			<table>
				<tr>
					<td width="20%">아이디</td>
					<td><%= rs.getString("id") %></td>
				</tr>
				<tr>
					<td>비밀번호</td>
					<td><%= rs.getString("password") %></td>
				</tr>
				<tr>
					<td>이름</td>
					<td><%= rs.getString("name") %></td>
				</tr>
				<tr>
					<td>이메일</td>
					<td><%= rs.getString("email") %></td>
				</tr>
			</table>
<%		
		}
	} catch(Exception e) {
%>
		DB접속실패 : <%= e.getMessage() %>
<%
	} finally {
		try {
			// 6. 사용한 Statement 종료
			if(rs != null) rs.close();
			if(stmt != null) stmt.close();
			
			// 7. 커넥션 종료
			if(conn != null) conn.close();
		} catch (Exception e) {
			
		}	
	}
%>	
</body>
</html>
```

![](https://gekdev.github.io/docs/jsp/example/basicjbdc.jpg)

### DBMS와의 통신을 위한 JDBC 드라이버

JDBC 드라이버는 DBMS와의 통신을 담당하는 자바 클래스

DBMS마다 별도의 JDBC드라이버가 필요, 각 DBMS는 JDBC드라이버를 jar파일 형태로 제공함

Class.forName() 메서드는 지정한 클래스 정보를 담고 있는 Class 인스턴스를 구해주는 기능만 제공

JDBC드라이버에 해당하는 클래스들은 Class.forName() 메서드를 통해 로딩될 때 자동으로 JDBC 드라이버로 등록됨

JDBC 드라이버를 로딩하는 방법
{: .label .mt-2}
```jsp
try {
    Class.forName("JDBC 드라이버 클래스의 완전한 이름");
} catch (ClassNotFoundException ex){
    //지정한 클래스가 존재하지 않는 경우 에러가 발생함
}
```

주요 데이터베이스의 JDBC 드라이버에 해당하는 클래스
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
1. MySQL : com.mysql.jdbc.Driver

2. 오라클 : oracle.jdbc.driver.OracleDriver

3. MS SQL 서버 : com.microsoft.sqlserver.jdbc.SQLServerDriver

4. MariaDB : org.mariadb.jdbc.Driver
</div>

예제 : MariaDB 드라이버를 로딩 
{: .label .label-purple .mt-2}
```jsp
try {
    Class.forName("org.mariadb.jdbc.Driver");
} catch (ClassNotFoundException ex){
    //지정한 클래스가 존재하지 않는 경우 에러가 발생함
    //에러 처리
}
```

### 데이터베이스 식별을 위한 JDBC URL

데이터베이스를 구분할 때 URL과 비슷한 형식을 갖는 JDBC URL을 사용

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
jdbc:[DBMS]:[데이터베이스식별자]
</div>

* MySQL

    MySQL JDBC URL
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    jdbc:mysql://HOST[:PORT]/DBNAME[?param=value&param1=vale2&...]

    ▸ HOST : 서버의 호스트 주소

    ▸ DBNAME : 데이터베이스 이름
    </div>
    
    한글데이터를 올바르게 출력하기 위해 사용하는 추가 파라미터
    {: .label .label-purple .mt-2}
    ```jsp
    jdbc:[DBMS]://HOST[:PORT]/DBNAME?useUnicode=true&characterEncoding=utf8
    ```

* MariaDB
    
    MariaDB JDBC URL
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    jdbc:mariadb://HOST[:PORT]/DBNAME[?param=value&param1=vale2&...]

    ▸ HOST : 서버의 호스트 주소

    ▸ DBNAME : 데이터베이스 이름
    </div>
    ```jsp
    String drv = "jdbc:mariadb://localhost:3306/jspstudy";
    ```
    
* Oracle

    오라클은 Thin, OCI 두가지 드라이버가 있음
    
    Oracle JDBC URL
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    jdbc:oracle:thin:@HOST:PORT:SID
    
    ▸ HOST : 서버의 호스트 주소

    ▸ PORT : 오라클이 설치된 포트번호
    
    ▸ SID : 사용할 데이터베이스의 SID
    </div>
    ```jsp
    jdbc:oracle:thin:@127.0.0.1:1521:ORCL
    ```
    
### 데이터베이스 커넥션

JDBC를 이용해서 데이터베이스를 사용하려면 데이터베이스와 연결된 커넥션을 구해야 함

**java.sql.Connection 타입이 데이터베이스 커넥션을 나타내며, java.sql.DriverManager 클래스가 제공하는 getConnection() 메서드를 사용해서 커넥션을 구함**

&#9656; 올바른 DB 사용자 계정과 암호를 사용 : DB와 연결된 Connection 객체를 리턴함 

&#8594; 이 객체를 사용해서 필요한 작업을 시작

&#9656; 올바르지 않은 DB 사용자 계정과 암호를 사용 : 객체를 생성하지 못하면 SQLException을 발생시켜서 getConnection()메소드를 사용할 때는 try-catch블럭을 이용해야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* DriverManager.getConnection(String jdbcURL)

* DriverManager.getConnection(String jdbcURL, String user, String password)

▸ jdbcURL : 데이터베이스에 연결할 때 사용할 JDBC URL

▸ user, password : 계정과 암호
</div>

Connection 객체를 다 사용한 뒤에는 close() 메소드를 호출해서 시스템 자원을 반납해야 함

&#8594; 반납하지 않으면 시스템 자원이 불필요하게 소모되어 커넥션을 구할 수 없는 상황이 발생할 수도 있음

&#9656; 익셉션을 발생시킬 경우 conn에 Connection 객체가 할당되지 않으므로 null 인지의 여부를 판단 후에 close() 메소드를 호출

close()
{: .label .label-purple .mt-2}
```jsp
try {
    String drv = "jdbc:mariadb://localhost:3306/jspstudy";
    String usr = "root";
    String pwd = "12345";
    String sql = "select * from member where id = '" + id + "'";
    conn = DriverManager.getConnection(drv, usr, pwd);
    ...
} catch(SQLException e) {
    //에러 발생
} finally {
    try { if(conn != null) conn.close(); } catch (SQLException e) {}	
}
```

### Statement를 사용한 쿼리 실행

Connection 객체를 생성한 후에는 Connection 객체로부터 Statement를 생성하고 쿼리를 실행할 수 있음

Statement는 Connection의 createStatement()메소드를 사용해서 생성함 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
Statement stmt = conn.createStatement();
</div>

Statement 객체는 쿼리를 실행할 수 있음. 쿼리를 실행하는 메소드

* ResultSet executeQuery(String query) : SELECT 쿼리를 실행, 결과값을 java.sql.ResultSet 객체에 저장해서 리턴

* int executeUpdate(String query) : INSERT, UPDATE, DELETE 쿼리를 실행, 변경한 레코드의 개수를 리턴

#### Statement를 이용한 쿼리 실행 시 작은따옴표 처리

SQL 쿼리를 실행할 때 작은 따옴표가 들어가면 작은 따옴표 두 개를 사용하는 형태로 변경해야 함

**String 클래스의 replaceAll()메서드를 사용하면 문자열에 포함된 특정 문자나 단어를 손쉽게 변경할 수 있음**

문자열에 포함되어 있는 작은 따옴표 한 개를 두개로 변경하고 싶다면 다음과 같이 String 클래스의 replaceAll() 메서드를 사용해야 함

예제
{: .label .label-purple .mt-2}
```jsp
String value = "king's choice"

String replaced = value.replaceAll("'", """);
```

매번 치환 처리를 하는게 귀찮고 놓치기 쉽기 때문에 PreparedStatement를 사용함

### ResultSet에서 값 읽어오기

Statement의 executeQuery()는 select쿼리의 결과를 ResultSet에 담아서 리턴

따라서 ResultSet이 제공하는 메서드를 사용해서 결과값을 읽어올 수 있음

* next() : select 결과의 존재 여부를 확인할 수 있음

ResultSet클래스의 주요 데이터 읽기 메서드
{: .label .label-red .mt-2}

| 메서드 | 리턴 타입 | 설명 |
|:-------|:----------|:-----|
| getString(String name) getString(int index) | String | 지정한 칼럼 값을 String으로 읽어옴 |
| getCharacterStream(String name) getCharacterStream(int index) | java.io.Reader | 지정한 칼럼 값을 스트림 형태로 읽어옴. Long VARCHAR타입을 읽어올 때 사용 |
| getInt(String name) getInt(int index) | int | 지정한 칼럼 값을 int 타입으로 읽어옴 |
| getLong(String name) getLong(int index) | long | 지정한 칼럼 값을 long 타입으로 읽어옴 |
| getDouble(String name) getDouble(int index) | double | 지정한 칼럼 값을 double 타입으로 읽어옴 |
| getFloat(String name) getFloat(int index) | float | 지정한 칼럼 값을 float 타입으로 읽어옴 |
| getTimestamp(String name) getTimestamp(int index) | java.sql.Timestamp | 지정한 칼럼 값을 Timestamp 타입으로 읽어옴 |
| getDate(String name) getDate(int index) | java.sql.Date | 지정한 칼럼 값을 Date 타입으로 읽어옴 |
| getTime(String name) getTime(int index) | java.sql.Time | 지정한 칼럼 값을 Time 타입으로 읽어옴 |

#### ResultSet에서 LONG VARCHAR 타입 값 읽어오기

getCharacterStream()메서드를 사용해서 읽어오는 게 원칙이지만 다수의 JDBC 드라이버는 getString()메서드로 읽어올 수 있게 지원하고 있음

따라서 아래 코드를 사용하지 않아도 되지만 원칙으로 아래 코드를 알아두기!

1. LONG VARCHAR타입을 포함하는 테이블 생성

    ```sql
    create table MEMBER_HISTORY(
        MEMBERID VARCHAR(10) NOT NULL PRIMARY KEY,
        HISTORY LONG VARCHAR
    )
    ```

2. HISTORY 칼럼 부분에 길이가 긴 문자열을 값으로 입력

    concat은 그냥 알아보기 좋게 하려고 사용함

    ```sql
    insert into MEMBER_HISTORY values ( 'madvirus',
        concat(
           '2015 스프링4 프로그래밍 입문<br>',
           '2014 Spring4.0 프로그래밍<br>',
           '2013 객체지향과 디자인 패턴<br>',
           '2012 JSP 2.2 웹프로그래밍<br>',
        )

    )
    ```

3. LONG VARCHAR타입의 값을 읽어오는 코드

    ```sql
    String data = null // 스트림으로 읽어온 데이터를 저장할 변수
    java.io.Reader reader = null // LONG VARCHAR 데이터를 읽어올 스트림

    try{
        //1. ResultSet의 getCharacterstream()으로 Reader 구함
        reader = rs.getCharacterStream("FIELD") //스트림 읽어옴

        if(reader!= null){
            //2. 스트림에서 읽어온 데이터를 저장할 버퍼를 생성
            StringBuilder buff = new StringBuilder();
            char[] ch = new char[512];
            int len = -1;

            //3. 스트림에서 데이터를 읽어와 버퍼에 저장
            while((len = reader.read(ch)) != -1) {
                buff.append(ch, 0, len);
            }

            //4. 버퍼에 저장한 내용을 String으로 변환
            data =  buff.toString();
        } catch(IOException e){
            //5. IO관련 처리 도중 문제가 있으면 IOException이 발생
            //익셉션 발생 
        } finally{
            if(reader!=null) try{ reader.close() } catch (IOException){}
        }
    }

    ...
    ```

### PreparedStatement를 사용한 쿼리 실행 

Statement와 동일한 기능을 제공함

차이점 : PreparedStatement은 SQL 쿼리의 틀을 미리 생성해 놓고 값을 나중에 지정함

1. Connection.prepareStatment() 메서드를 사용해 PreparedStatement 생성

    ```sql
    PreparedStatement pstmt = null;
    ...
    
    pstmt = conn.prepareStatement("insert into MEMBER values(?,?,?)");
    ```

2. PreparedStatement의 set 메서드를 사용해 필요한 값 지정

    인덱스는 1, 이후 물음표의 인덱스는 나오는 순서대로 인덱스값이 1씩 증가
    
    ```sql
    pstmt.setString(1, "aaa"); //첫번째 물음표 값 지정
    pstmt.setString(2, "bbb"); //두번째 물음표 값 지정
    ```

PreparedStatement클래스가 제공하는 set메서드
{: .label .label-red .mt-2}

| 메서드 | 설명 |
|:-------|:-----|
| setString(int index, String x) | 지정한 인덱스의 파라미터 값을 x로 지정 | 
| setCharacterStream(int index, Reader reader, int length) | 지정한 인덱스의 파라미터 값을 LONG VARCHAR타입의 값으로 지정한다 |
| setInt(int index, String x) | 지정한 인덱스의 파라미터 값을 int의 값 x로 지정한다 |
| setLong(int index, String x) | 지정한 인덱스의 파라미터 값을 long의 값 x로 지정한다 |
| setDouble(int index, String x) | 지정한 인덱스의 파라미터 값을 의 double값 x로 지정한다 |
| setFloat(int index, String x) | 지정한 인덱스의 파라미터 값을 의 float값 x로 지정한다 |
| setTimestamp(int index, String x) | 지정한 인덱스의 값을 SQL TIMESTAMP 타입을 나타내는 java.sql.Timestamp 타입으로 지정한다 |
| setDate(int index, String x) | 지정한 인덱스의 값을 SQL DATE타입을 나타내는 java.sql.Date 타입으로 지정한다 |
| setTime(int index, String x) | 지정한 인덱스의 값을 SQL TIME타입을 나타내는 java.sql.Time 타입으로 지정한다 |

3. PreparedStatement의 executeQuery() 나 executeUpdate()를 사용해 쿼리를 실행
    
    PreparedStatement를 생성할 때 실행할 쿼리를 지정하기 때문에 이 메서드는 쿼리를 인자로 입력받지 않음 

    * ResultSet executeQuery(String query) : SELECT 쿼리를 실행, 결과값을 java.sql.ResultSet 객체에 저장해서 리턴

    * int executeUpdate(String query) : INSERT, UPDATE, DELETE 쿼리를 실행, 변경한 레코드의 개수를 리턴

4. finally 블록에서 사용한 PreparedStatement를 닫음(close() 실행)

#### PreparedStatement에서 LONG VARCHAR 타입 값 지정하기

**setCharacterStream(int index, Reader reader, int length) 메서드를 사용해서 지정함**

&#9656; reader로부터 length 글자 수만큼 데이터를 읽어와 저장

&#9656; reader에는 두가지가 있음

1. String 타입의 값을 저장하고 싶을 때

    ```jsp
    PreparedStatement pstmt = null;

    try{
        String value = "..." //Long VARCHAR에 넣을 값
        pstmt = conn.preparedStatement(...);
        java.io.StringReader reader = new java.io.StringReader(value);
        pstmt.setCharacterStream(1, reader, value.length());
        ...
    }catch (SQLException ex){
        ...
    }finally{
        ...
        if(pstmt != null) try{ pstmt.close(); } catch(SQLException e){}
    }
    ```

2. 텍스트 파일로부터 데이터를 읽어와 저장하고 싶을 때

    ```jsp
    PreparedStatement pstmt = null;
    FileReader reader = null;

    try{
        pstmt = conn.preparedStatement(...);
        reader = java.io.FileReader(파일경로);
        pstmt.setCharacterStream(1, reader);
        ...
    } catch(SQLException ex){
    } finally {
        if(pstmt != null) try{ pstmt.close(); } catch(SQLException e){}
        if(reader != null) try{ pstmt.close(); } catch(SQLException e){}
    }
    ```

### PreparedStatement 쿼리를 사용하는 이유

1. 값 변환을 자동으로 하기 위해

2. 간결한 코드를 위해

검색 조건과 같이 값을 지정해야 하는 쿼리를 실행 할 때는 PreparedStatement를 선호함

---

## 웹 어플리케이션 구동 시 JDBC 드라이버 로딩하기

## JDBC에서 트랜잭션 처리

## Connection Pool

### What is Connection Pool?

### DBCP를 이용해서 커넥션 풀 사용하기 

<span class="fs-2">
[Apache Commons DBCP » 2.8.0](https://mvnrepository.com/artifact/org.apache.commons/commons-dbcp2/2.8.0){: .btn .btn-outline .mt-2}
</span>

<span class="fs-2">
[Apache Commons Pool » 2.9.0](https://mvnrepository.com/artifact/org.apache.commons/commons-pool2/2.9.0){: .btn .btn-outline .mt-2}
</span>

<span class="fs-2">
[Apache Commons Logging](https://mvnrepository.com/artifact/commons-logging/commons-logging/1.2){: .btn .btn-outline .mt-2}
</span>

### 커넥션 풀 초기화 서블릿 클래스 

### 커넥션 풀 초기화 서블릿 설정

### 커넥션 풀로부터 커넥션 사용하기

### 커넥션 풀 속성 설명

GenericObjectPoolConfig 클래스의 커넥션 개수와 대기 관련 설정 메서드
{: .label .label-red .mt-2}

| 메서드 | 설명 | 기본값 |
|:-------|:-----|:-------|
| setMaxTotal(int) | 풀이 관리하는 커넥션의 최대 개수를 설정. 음수면 제한 X | 8 |
| setMaxIdle(int) | 커넥션풀이 보관할 수 있는 최대 유휴 개수를 지정. 음수면 제한 X | 8 | 
| setMinldle(int) | 커넥션풀이 유지할 최소 유휴 커넥션 개수를 지정. 이 값이 maxIdle보다 크면 maxIdle을 minIdle값으로 사용 | 0 |
| setBlockWhenExhausted(boolean) | 풀이 관리하는 커넥션이 모두 사용중인 상태에서 커넥션을 요청할 떄 풀에 커넥션이 반환될 때 까지 대기할지 여부를 지정. ture: 대기 / false: NoSuchElementException 발생 | true |
| setMaxWaitMillis(long) | bolckWhenExhausted가 true일 때, 최대 대기 시간을 설정. 음수면 풀에서 커넥션을 구할 수 있을 때 까지 대기. 단위는 밀리초 | -1L |
 
 커넥션 풀은 사용되지 않은 유휴 커넥션을 제거하는 기능을 제공함 
 
 이 기능을 사용하면 주기적으로 커넥션을 검사하기 때문에 DBMS에서 연결을 끊기 전에 먼저 커넥션을 풀에서 제거할 수 있음 
 
GenericObjectPoolConfig 클래스의 유휴 커넥션 제거 및 검사 관련 설정 메서드
{: .label .label-red .mt-2}

| 메서드 | 설명 | 기본값 |
|:-------|:-----|:-------|
| setTimeBetweenEvictionRunsMillis(long) | 풀에 있는 유휴 커넥션 검사 주기를 설정. 양수가 아니면 검사하지 않음, 단위는 밀리초 | -1L |
| setNumTestsPerEvictionRun(int) | 각 주기 때마다 검사할 커넥션의 개수를 설정. 음수면 유휴 커넥션 개수를 검사 개수의 절대값으로 나눈 값을 사용 | 3 |
| setMinEvictableIdleTimeMillies(long) | 풀에 머물 수 있는 최소 유휴시간. 이 시간을 초과한 커넥션이 제거대상, 단위는 밀리초 | 1800000L(30분) |
| setTestWhileIdle(boolean) | ture면 유휴 커넥션이 유효한지 검사 | false |
| setTestOnBorrow(boolean) | true면 커넥션 풀에서 커넥션을 가져올 때 유효한지 검사 | false |
| setTestOnReturn(boolean) | true면 커넥션 풀을 반환할 때 유효한지 검사 | false |
 
커넥션 풀에 있는 커넥션 중 오랜 시간동안 사용되지 않는 커넥션은 DBMS와 연결이 끊길 가능성이 높음
 
연결이 끊긴 커넥션을 사용하면 프로그램 실행 도중 오류가 발생하기 때문에 주기적으로 커넥션 풀에 있는 커넥션을 검사해서 사전에 제거해 주는게 좋음
 
DBCP는 다음의 두가지 기준으로 풀에 있는 커넥션을 검사함
 
1. 커넥션이 최소 유휴 시간보다 오래 풀에 있는 경우(minEvictableIdleTimeMillis)
 
2. 커넥션이 유효한지 여부 확인(testWhileIdle)
 
    true면 PoolableConnectionFactory의 커넥션 검사 기능을 사용
    
두 속성은 기본적으로 검사 주기가 양수일 때 적용됨
 
&#8594; 양수가 아니면 유휴 커넥션 제거 처리 자체를 하지 않기 때문에 검사 주기 값을 설정해야 유효 커넥션을 제거함 
 
PoolableConnectionFactory클래스의 커넥션 검사 기능과 관련된 설정 메서드
{: .label .label-red .mt-2}

| 메서드 | 설명 | 기본값 |
|:-------|:-----|:-------|
| setMaxConnLifeTimeMillis(long) | 커넥션의 최대 사용 시간을 설정. 단위는 밀리초 | -1L |
| setValidationQuery(String) | 커넥션을 검사할 때 사용할 쿼리를 설정 |

GerenicObjectPoolConfig 클래스에서 설정하는 풀의 속성
{: .label .label-red .mt-2}

1. maxTotal : 사이트의 최대 커넥션 사용량을 기준으로 지정. 이 값이 불필요하게 커질 경우 커넥션 개수가 비대하게 늘어나 DBMS가 수용할 수 있는 수준을 넘어서면 오히려 전체 성능에 좋지 않은 영향을 끼칠 수 있음

2. minIdle : 사용되지 않는 커넥션의 최소 개수를 0으로 지저하면 풀에 저장된 커넥션 개수가 0이 될 수 있음. 이 경우 커넥션이 필요할 때 다시 커넥션을 생성하게 됨. 따라서 커넥션의 최소 개수는 시스템 사용이 가장 적은 시간을 기준으로 설정

3. timeBetweenEvctionRunsMillis : 이 값을 설정해서 주기적으로 유휴 커넥션을 풀에서 제거해야 함. 커넥션의 동시 사용량은 보통 새벽에 최저이고 낮 시간대에 최대에 이름. 이 두시간대에 필요한 커넥션 개수의 차이는 수십에서 수백개. 이때 최대 상태에 접어들었다가 최소 상태로 가게되면 풀에서 사용되지 않는 커넥션의 개수가 점차 증가. 따라서 DB와의 연결이 끊기기 전에 유휴 커넥션을 미리 풀에서 제거해주는게 좋음. 보통 10분에서 30분 단위로 검사하는게 좋음

4. testWhileIdle : 유휴 커넥션을 검사할 떄 유효하지 않은 커넥션도 검사해서 연결이 끊긴 커넥션을 사전에 제거하는게 좋음

5. maxWaitMillis : 커넥션 풀에 커넥션이 없으면 일정 시간 대기 후 익셉션을 발생시키는게 좋음. 커넥션을 대기하느라 수십 초 이상 대기하면 사용자는 응답이 없으므로 브라우저의 새로고침을 누르거나 DB를 사용하는 다른 페이지로 이동해서 다시 풀에서 가져오기 위해 대기하게 됨. 사용자가 아무 응답없이 대기하는 것 보다 1초 미만의 길지 않은 시간 안에 커넥션을 구하지 못하면 익셉션을 발생시켜서 알맞은 안내 화면을 보여주는게 더 좋음
