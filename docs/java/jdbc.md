---
layout: default
title: JDBC
parent: Java
nav_order: 22
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

3. Statement(Statement / PreparedStatement / CallableStatement)객체를 생성

4. SQL실행

5. ResultSet객체로 처리결과를 리턴


### Objects used by JDBC

JDBC에서 사용되는 객체

1. DriverManager 클래스

2. Connection 인터페이스

3. Statement 인터페이스

4. PreparedStatement 인터페이스

5. CallableStatement 인터페이스

6. ResultSet 인터페이스

7. JDBC 트렌젝션

---

## 

1. JDBC드라이버 로드

    &#9656; 드라이버 클래스를 어디서나 사용할 수 있게 상수로 만들어 줌
    
    &#9656; Class.forName() 함수는 Exception처리를 해줘야 함

    ```java
    public class JDBCConnection {

    // 어디서나 사용할 수 있게 상수로 만들어 줌
    final static String DRV = "oracle.jdbc.OracleDriver";

    public static void main(String[] args) {

        // Class.forName() 함수는 Exception처리를 해줘야 함
        try {
            Class.forName(DRV);
        } catch (Exception e) {
            e.printStackTrace();
        }

    }
    }
    ```



