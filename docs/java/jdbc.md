---
layout: default
title: JDBC
parent: Java
nav_order: 22
has_children: true
---
# Java JDBC
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Java & DB Connection

## Connection Basic

JDBC를 이용한 Java와 DB의 연동

Java와 DB를 연동하기 위해서는 각 DBMS의 버전에 맞는 JRE 실행환경 라이브러리(커텍터 드라이버)를 Java프로젝트에 추가해야 함

MSSQL, MySQL, Maria 등 각각 DB버전에 맞는 실행환경 드라이버를 추가해야 함

**즉 이번에 설치 할 Oracle DB는 DB버전(11gR2)에 맞는 자바프로젝트(ojbdc8.jar)를 추가해야 함**

<span class="fs-2">
[Download Library](https://mvnrepository.com/artifact/com.oracle.database.jdbc/ojdbc8/21.1.0.0){: .btn .btn-outline .mt-2}
</span>

### Add Library

라이브러리(드라이버)를 추가하는 방법

1. **java프로젝트를 우클릭**

2. **Build Path > Configure Build Path**

![](jar.jpg)

3. **(tab)Libraries -> (b)Add Jars(Add Ex...) -> (b)Apply & Close**

![](jar2.jpg)

### JDBC Program Creation Steps

**JDBC 프로그램 작성 단계**

1. JDBC드라이버 로드(DB버전에 따라 드라이버가 다를 수 있음)

    1. Oracle : `Class.forName("oracle.jdbc.OracleDriver");`
    
        ![](jar3.jpg)
    
    2. MySQL : `Class.forName("com.mysql.jdbc.driver");`
    
    3. [MariaDB](http://www.gisdeveloper.co.kr/?p=4858) : `Class.forName("org.mariadb.jdbc.Driver");`
    
2. Connection 객체를 생성

    Connection객체에 연결하는 것으로 DriverManager에 등록된 각 드라이버들을 getConnection()메서드를 사용해서 식별
    
    **getConnection() : 매개값은 DB의 url주소, 사용자ID, password를 전달함**
    
    연결할 때 url식별자정보를 이용해서 mapping하고 찾지 못할 경우(연결되지 않을 경우)에는 "no suitable error"가 발생
    
    찾았을 경우에는 getConnection(String url)의 수행결과가 Connection객체에 리턴됨
    
    1. Oracle
    
        ```java
        conn = DriverManager.gerConnetion("jdbc:oracle:thin:@localhost:1521:xe", "scott", "tiger");
        ```
    
    2. MySQL
    
        ```java
        conn = DriverManager.gerConnetion("jdbc:mysql://localhost:3306:db이름", "root", "12345");
        ```
    
    3. MariaDB
    
        ```java
        conn = DriverManager.getConnection( "jdbc:mariadb://100.100.100.7:3306/dbname", "userId", "password");
        ```

3. Statement(Statement / PreparedStatement / CallableStatement)객체를 생성

    SQL을 생성 및 실행하며 반환된 결과를 저장할 작업영역을 제공하는 객체
    
    Statement객체는 Connection 객체의 createStatement() 메서드를 사용하여 생성함
    
    이 단계부터는 JDBC 드라이버에 제한을 받지 않음
    
    즉 DB와 상관없이 동일한 SQL 명령을 사용할 수 있음
    
    단 SQL표준을 준수할 경우 동일한 명령이지만 DB마다 고유한 SQL명령이라면 각 DB에 알맞는 SQL문법에 맞게 작성되어야 함
    
    ```java
    Statement stmt = conn.createStatement();
    
    PreparedStatement pstmt = conn.createStatement();
    ```

4. SQL실행

    Statement 객체가 생성이 되면 Statement 객체의 executeQuery(), executeUpdate() 메서드를 사용하여 처리함
    
    ```java
    ResultSet rs = stmt.executeQuery("select * from emp")
    ```

5. ResultSet객체로 처리결과를 리턴

    executeQuery()메서드는 SQL 실행결과를 ResultSet으로 리턴
    
    이 ResultSet으로부터 읽은 데이터를 추출하는 과정이 ResultSet처리과정
    
    데이터를 추출하는 방법은 ResultSet에서 한행(row)씩 이동하면서 getXXX()메서드를 이용하여 추출하는데
    
    이때 사용하는 방법은 2가지가 있음
    
    1. 컬럼 순서
    
    `String str = rs.getString(1)`
    
    2. 컬럼명
    
    `String str = rs.setString("컬럼이름")`

---

## Objects used by JDBC

**JDBC에서 사용되는 객체**

### DriverManager Class

1. 역할 

    **데이터원본에 JDBC 드라이버를 통해 커넥션을 만듦**

2. 생성

    **Class.forName()를 통해 생성,  이 메서드는 인터페이스 드라이버를 구현하는 작업**

    &#9656; Class.forName()처럼 특정 클래스를 로드하면 자동으로 객체가 생성되고 DriverManager에 등록됨

    &#9656; 드라이버를 찾지 못했을 경우에는 forName() 메서드는 ClassNotFound Exception예외를 발생시켜서 반드시 예외처리를 해야함

3. 특징 

    &#9656; 일반적으로 드라이버 클래스들은 로드될 때 **자신의 인터페이스를 자동으로 DriverManager클래스의 메서드를 호출하여 그 인스턴스를 등록함**

    &#9656; 모든 메서드는 static이기 때문에 객체를 생성할 필요가 없음

4. 다른객체 생성
    
    DriverManager 클래스는 Connection 인터페이스의 구현객체를 생성하는데 **getConnection()을 이용해 생성**

### Connection Interface

1. 역할

    &#9656; **Connection 인터페이스가 구현된 클래스의 객체 : 특정 데이터원본에 대한 커넥션**

    &#9656; 특정한 SQL문장을 정의하고 실행시킬 수 있는 Statement 객체를 생성할 때도 Connection객체를 사용

    &#9656; 데이터베이스에 대한 데이터인 메터데이터베이스에 관한 정보를 데이터 원본에 질의하는데 사용

    &#8594; 이때에는 사용가능한 테이블이름, 특정테이블의 컬럼등의 정보가 제공

### Statement Interface

1. 역할

    **Connection객체에 의해 프로그램에 리턴되는 객체에 의해 구현되는 일종의 메서드 집합을 정의**
    
    **특정한 SQL문장을 정의하고 실행**
    
2. 생성

    Statement인터페이스를 구현한 객체로서 항상 매개값이 없는 Connection.createStatment()를 호출

3. 

Statement객체를 생성하면 Statement.executeQuery()를 호출해서 SQL질의를 실행

메서드의 인자로 SQL문장을 담은 String객체를 전달

4. 특징

    Statement객체는 단순 질의문을 사용하는 것이 좋음

### PreparedStatement Interface

1. 역할

    **PreparedStatement 인터페이스 : 각각의 인수에 위치홀더(placeholder, ?)를 사용하여 SQL문장을 정의할 수 있게 해줌**
    
    위치 홀더
    {: .label .label-red .mt-2}
    <div class="code-example" markdown="1">
    &#9656; ?으로 표현

    &#9656; 위치홀더는 SQL문장에 나타나는 토큰(token)인데 이것은 SQL문장이 실행되기 전에 실제값으로 대체됨

    &#9656; 이런 방법을 이용하면 특정값으로 문자열을 연결하는 방법보다 훨씬 쉽게 SQl문장을 만들 수 있음 
    </div>
    
2. 생성 

    **PreparedStatement 인터페이스는 Conneciton객체의 preparedStatement()를 사용해서 객체를 생성**

3. Statement객체와의 차이점

    PreparedStatement객체는 SQL문장이 사전에 컴파일되어 실행시간동안 파라미터값을 위한 공간을 확보한다는 점에서 Statement 객체와 구별됨

    Statement객체의 SQL은 실행될 때 마다 DB서버에서 분석되어야 하지만 PreparedStatement객체는 한번 분석되면 재사용이 용이

4. 메서드

    setXXX(): 각각의 SQL타입을 처리

    여기서 XXX는 해당 테이블의 필드데이터타입과 관련이 있음 

    해당 필드의 데이터타입이 문자열이면 setSTring()이 되고, 숫자값이면 setInt()가 된다

    setXXX(num, value)메서드는 2개의 매개값을 가지고 잇는데 num은 placeholder의 위치와 대응됨


PreparedStatement객체가 제공하는 메서드는 setString, setInt, setLong, setDouble, setFloat, setTimestamp, setDate, setObject가 있음

PreparedStatement객체를 사용하는 것이 statement객체를 사용하는 것보다 좋음

4. 장점

    1. 동일한 질의문을 특정값만 변경해서 여러번 실행해야 할 때, 많은 데이터를 다룰 경우 질의문을 정리해야 할 필요가 있을 때, 파라미터가 많아서 질의문을 정리해야 할 필요가 있을 때 좋음
    
    2. 사전에 컴파일되기 때문에 쿼리실행속도가 Statement객체에 비해 빠름
    
    3. Statement객체는 쿼리 실행시 작은 따옴표가 있으면 작은 따옴표를 2개로 표시해야 하지만 PreparedStatement 객체는 작은 따옴표의 문제를 쿼리 실행시에 자동으로 처리하기 때문에 신경 쓸 필요가 없음

### CallableStatement Interface

1. 역할

    CallableStatement 객체는 주로 StoredProcedure(function of procedure)를 사용하기 위해 사용

2. 생성

    CallableStatement 인터페이스는 Connection객체의 preparedCall() 메서드를 사용해서 객체를 생성
    
    ```java
    CallableStatement cstmt = conn.preparedCall("{ call storedprocedure명 }");
    ```

3. 처리 

    데이터베이스에 저장된 procedure나 function을 단지 호출하는 것 만으로도 처리가 가능
    
4. 호출방법

    1. 단순호출 : { call procedure이름[?,?,...] }

    2. 호출 결과값 리턴 : { ? = call procedure이름[?,?,...] }
    
    3. 파라미터가 없는 프로시져 호출 : { call procedure이름 }

### ResultSet Interface

SQL문중에서 select문을 사용한 질의가 성공했을 경우에 결과로서 ResultSet을 반환

1. 역할 

    **ResultSet은 SQL질의에 의해 생성된 정보를 저장**

2. 커서
    
    ResultSet 객체는 커서(cursor)라고 불리는 것을 가지고 있는데 그것으로 ResultSet에서 특정행에 참조하는 데이터를 조작할 수 있음

    커서는 초기에 첫번째 행의 바로 앞을 가리키도록 되어 있는데 ResultSet객체의 next() 메서드를 사용하면 다음행으로 이동할 수 있음

    ResultSet 커서 메서드
    {: .label .label-red .mt-2}

    | 메서드 | 설명 |
    |:------|:----|
    | first() | 커서를 첫 번째 행으로 이동 | 
    | last() | 커서를 마지막 행으로 이동 |
    | beforefirst() | 커서를 첫 번째 이전으로 이동 | 
    | afterlast() |  커서를 마지막 행 다음으로 이동| 
    | next() | 커서를 다음행으로 이동| 
    | previous() | 커서를 이전행으로 이동| 

    ResultSet에서 행을 처리하는데 반복을 사용하며 next()메서드가 유효한 행이 있으면 true, 없으면 false를 리턴하는것으로 while문을 제어할 수 잇음

    ResultSet객체에서 값을 가져올 경우에는 getXXX()메서드를 사용

### JDBC transaction

1. 정의 
    
    **트렌젝션(Transaction)은 여러 단계의 작업을 하나로 처리하는 것**
    
2. 역할

    하나로 인신된 작업이 모두 성공적으로 끝나면 commit이 되고 하나라도 문제가 있다면 rollback되어서 작업을 수행전으로 되돌림
    
    이렇기 때문에 Transaction은 프로그램의 신뢰도를 보장하게 됨

3. 메서드

    JDBC에서도 Transaction처리에 대한 메서드를 제공

    1. commit()
    
    2. rollback()
    
    기본적으로 Connection객체에 setAutoCommit(boolean autoCommit)이라는 메서드가 있는데 기본값이 true로 되어있기 때문에
    JDBC는 Auto Commit이 자동수행됨
    
    자동수행되는것을 막으려면 conn.setAutoCommit(false)로 지정해야 함

---

## 




