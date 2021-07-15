
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

### 데이터 베이스 생성

1. mariaDB에 board 데이터베이스 생성

    ```sql
    create database board;
    ```

### 예제 이클립스 프로젝트 생성

Dynamic Project : board

Context root : board

1. 커넥션 풀

    * commons-dbcp2-2.8.0.jar

    * commons-logging-1.2.jar

    * commons-pool2-2.9.0.jar

2. DB 커넥터

    * mariadb-java-client-2.7.3.jar

3. JSTL

    * jstl-1.2.jar

4. 파일업로드

    * cos.jar

### 커넥션 관련 코드

1. 커넥션풀을 초기화 하기 위한 코드

    DBCPInitListener.java
    {: .label .label-purple .mt-2}
    ```java
    package board.db;

    import java.io.IOException;
    import java.io.StringReader;
    import java.sql.DriverManager;
    import java.util.Properties;

    import javax.servlet.ServletContextEvent;
    import javax.servlet.ServletContextListener;

    import org.apache.commons.dbcp2.ConnectionFactory;
    import org.apache.commons.dbcp2.DriverManagerConnectionFactory;
    import org.apache.commons.dbcp2.PoolableConnection;
    import org.apache.commons.dbcp2.PoolableConnectionFactory;
    import org.apache.commons.dbcp2.PoolingDriver;
    import org.apache.commons.pool2.impl.GenericObjectPool;
    import org.apache.commons.pool2.impl.GenericObjectPoolConfig;

    public class DBCPInitListener implements ServletContextListener{

        @Override
        public void contextInitialized(ServletContextEvent sce) {

            String poolConfig = sce.getServletContext().getInitParameter("poolConfig");
            Properties prop = new Properties();

            try {
                prop.load(new StringReader(poolConfig));
            } catch (IOException e) {
                System.out.println("prop.load 실패" + e.getMessage());
            }

            loadJDBCDriver(prop);
            initConnectionPool(prop);

        }

        private void loadJDBCDriver(Properties prop) {

            //[web.xml] driverClass = org.mariadb.jdbc.Driver
            String driverClass = prop.getProperty("jdbcdriver");

            try {
                Class.forName(driverClass);
            } catch (ClassNotFoundException e) {
                throw new RuntimeException("Fail to load JDBC Driver", e);
            }

        }

        private void initConnectionPool(Properties prop) {

            try {
                String jdbcUrl = prop.getProperty("jdbcUrl");	//[web.xml] jdbcUrl = jdbc:mariadb://localhost:3306/board
                String username = prop.getProperty("dbUser");	//[web.xml] username = root
                String pw = prop.getProperty("dbPass");			//[web.xml] pw = 12345

                ConnectionFactory connFactory = new DriverManagerConnectionFactory(jdbcUrl, username, pw);

                PoolableConnectionFactory poolableConnFactory = new PoolableConnectionFactory(connFactory, null);

                //커넥션풀의 커넥션 검사 쿼리
                //[web.xml] validationQuery = select 1
                String validationQuery = prop.getProperty("validationQuery");

                //validationQuery가 빈값이 아니라면
                if(validationQuery != null && !validationQuery.isEmpty()) {
                    poolableConnFactory.setValidationQuery(validationQuery);
                }

                GenericObjectPoolConfig poolConfig = new GenericObjectPoolConfig();

                poolConfig.setTimeBetweenEvictionRunsMillis(1000L * 60L * 5L);
                poolConfig.setTestWhileIdle(true);

                //최소 유휴 커넥션을 프로퍼티로 설정
                int minIdle = getIntProperty(prop, "minIdle", 5);
                poolConfig.setMinIdle(minIdle);
                //최대 유휴 커넥션을 프로퍼티로 설정
                int maxTotal = getIntProperty(prop, "maxTotal", 50);
                poolConfig.setMaxTotal(maxTotal);

                GenericObjectPool<PoolableConnection> connectionPool = new GenericObjectPool<PoolableConnection>(poolableConnFactory, poolConfig);
                poolableConnFactory.setPool(connectionPool);

                Class.forName("org.apache.commons.dbcp2.PoolingDriver");
                PoolingDriver driver = (PoolingDriver) DriverManager.getDriver("jdbc:apache:commons:dbcp:") ;
                //[web.xml] poolName = board
                String poolName = prop.getProperty("poolName");
                driver.registerPool(poolName, connectionPool);

            } catch (Exception e) {
                throw new RuntimeException(e);
            }
        }

        private int getIntProperty(Properties prop, String propName, int defaultValue) {
            String value = prop.getProperty(propName);
            if(value == null) return defaultValue;
            return Integer.parseInt(value);
        }

        @Override
        public void contextDestroyed(ServletContextEvent sce) {
        }

    }
    ```

2. 서블릿 컨텍스트 리스너 등록

    &#9656; DBCPInitListener는 서블릿 컨텍스트 리스너 이므로 web.xml에 등록해야 함
    
    web.xml
    {: .label .label-purple .mt-2}
    ```xml
    <listener>
        <listener-class>board.db.DBCPInitListener</listener-class>
    </listener>
  
    <context-param>
        <param-name>poolConfig</param-name>
        <param-value>
            jdbcdriver=org.mariadb.jdbc.Driver
            jdbcUrl=jdbc:mariadb://localhost:3306/board
            dbUser=root
            dbPass=12345
            validationQuery=select 1
            minIdle=3
            maxTotal=30
            poolName=board
        </param-value>
    </context-param>
    ```
    
3. 커넥션을 구할 때 사용할 코드 

    &#9656; jdbc:apache:commons:dbcp:board는 web.xml에서 지정한 poolName값인 board를 풀 이름으로 사용
    
    ConnectionProvider
    {: .label .label-purple .mt-2}
    ```java
    package board.db;

    import java.sql.Connection;
    import java.sql.DriverManager;
    import java.sql.SQLException;

    public class ConnectionProvider {

        public static Connection getConnection() throws SQLException{
            return DriverManager.getConnection("jdbc:apache:commons:dbcp:board");
        }

    }
    ```
    
4. 커넥션 관련 코드 작성을 편리하게 하는 코드

    &#9656; jdbcUtility 클래스 생성

    JDBCUtility
    {: .label .label-purple .mt-2}
    ```java
    package board.db;

    import java.sql.Connection;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;

    import javax.naming.Context;
    import javax.naming.InitialContext;
    import javax.naming.NamingException;
    import javax.sql.DataSource;

    public class JDBCUtility {

        public static void close(Connection conn) {
            try {
                if(conn != null) conn.close();
            }catch (Exception e) {
                e.printStackTrace();
            }
        }

        public static void close(Statement stmt) {
            try {
                if(stmt != null) stmt.close();
            }catch (Exception e) {
                e.printStackTrace();
            }
        }

        public static void close(Connection conn, Statement stmt) {
            try {
                if(stmt != null) stmt.close();
                if(conn != null) conn.close();
            }catch (Exception e) {
                e.printStackTrace();
            } 
        }

        public static void close(Statement stmt,  ResultSet rs) {
            try {
                if(rs != null) rs.close();
                if(stmt != null) stmt.close();
            } catch (Exception e) {
                e.printStackTrace();
            }
        }

        public static void close(Connection conn, Statement stmt, ResultSet rs) {
            try {
                if(rs != null) rs.close();
                if(stmt != null) stmt.close();
                if(conn != null) conn.close();
            }catch (Exception e) {
                e.printStackTrace();
            }
        }

        public static void commit(Connection conn) {
            try {
                conn.commit();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }

        public static void rollback(Connection conn) {
            try {
                conn.rollback();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
    ```

### 캐릭터 인코딩 필터 설정

1. 요청 파라미터의 캐릭터 인코딩 코드 작성

    CharacterEncodingFilter
    {: .label .label-purple .mt-2}
    ```java
    package board.filter;

    import java.io.IOException;

    import javax.servlet.Filter;
    import javax.servlet.FilterChain;
    import javax.servlet.FilterConfig;
    import javax.servlet.ServletException;
    import javax.servlet.ServletRequest;
    import javax.servlet.ServletResponse;

    public class CharacterEncodingFilter implements Filter{

        private String encoding;

        @Override
        public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain)
                throws IOException, ServletException {
            //setCharacterEncoding() 메서드로 요청 캐릭터 인코딩을 설정
            req.setCharacterEncoding(encoding);
            chain.doFilter(req, res);
        }

        @Override
        public void init(FilterConfig config) throws ServletException {
            encoding = config.getInitParameter("encoding");
            if(encoding == null) {
                encoding = "UTF-8";
            }
        }

        @Override
        public void destroy() {	}

    }
    ```
    
2. 사용할 인코딩을 지정하고, url 패턴 지정

    web.xml
    {: .label .label-purple .mt-2}    
    ```xml
    
    //위 DBCPInitListener... 코드
    
    <filter>
        <filter-name>encodingFilter</filter-name>
        <filter-class>board.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>utf-8</param-value>
        </init-param>
    </filter>

    <filter-mapping>
        <filter-name>encodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
    ```

### MVC 컨트롤러 코드

1. board.handler.CommandHandler

    ```java
    package board.handler;

    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;

    //CommandHandler 인터페이스를 정의
    public interface CommandHandler {

        //모든 명령어 핸들러가 공통으로 구현해야 하는 메서드를 선언
        //process() 메서드를 이용해서 알맞은 로직 코드를 구현하고 결과를 보여줄 JSP의 URI를 리턴
        public String process(HttpServletRequest req, HttpServletResponse res) throws Exception;

    }
    ```

2. board.handler.NullHandler

    ```java
    package board.handler;

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

3. board.handler.ControllerUsingURI

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

### 회원 가입 기능 구현

회원 가입 기능의 명세는 다음과 같음

1. 회원 가입 요청을 하면 입력을 위한 폼을 보여줌

2. 입력 폼에 아이디, 이름, 암호, 암호 확인을 입력하고 전송하면 가입에 성공

3. 동일한 아이디를 가진 회원이 존재하면 에러 메시지와 함께 다시 폼을 보여줌

4. 입력한 암호와 암호 확인이 일치하지 않으면 에러 메시지와 함께 다시 폼을 보여줌

![](joinhandler.png)

* JoinHandler : 사용자의 요청을 받음

    사용자가 폼을 요청한 경우 폼을 보여주고, 폼데이터를 전송한경우 JoinService를 통해 회원가입을 처리함
    
    - joinForm : 회원 가입 폼을 보여줌
    
    - joinSuccess : 회원 가입 처리에 성공한 경우 결과를 보여줌

* JoinService : 회원 가입 기능을 구현

    - JoinRequest 회원가입할 때 필요한 데이터를 담음
    
    폼에 입력한 값을 이 객체에 담아 JoinService에 전달
    
* MemberDao : member테이블과 관련된 쿼리를 실행

* Member : member 테이블과 관련된 클래스로서 회원 데이터를 담음

#### Member

board 데이터베이스에 member 테이블 생성

```sql
create table member (
	memberid varchar(50) primary key,
	name varchar(50) not null,
	password varchar(10) not null,
	regdate datetime not null
)
```

member 테이블의 데이터를 담을 때 사용할 Member 클래스

matchPassword는 암호 변경 기능을 구현할 떄 사용

```java
package member.model;

import java.util.Date;

public class Member {
	
	private String id;
	private String name;
	private String password;
	private Date regDate;
	
	public Member(String id, String name, String password, Date regDate) {
		super();
		this.id = id;
		this.name = name;
		this.password = password;
		this.regDate = regDate;
	}

	public String getId() {
		return id;
	}

	public String getName() {
		return name;
	}

	public String getPassword() {
		return password;
	}

	public Date getRegDate() {
		return regDate;
	}
	
	//암호 변경 기능을 구현할 떄 사용
	public boolean matchPassword(String pwd) {
		return password.equals(pwd);
	}
}
```

#### MemberDao 구현



