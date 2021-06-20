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

### Board 테이블 생성 

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

### jdbc.properties 생성

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

### Board 프로그램

#### BoardVO : 게시판 Model 클래스

**게시판 내용들을 생성, 초기화 그리고 get,set할 메소드를 가진 클래스**

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

```java
package com.lec.ex02_board;

import java.io.FileReader;
import java.io.UnsupportedEncodingException;
import java.net.URLDecoder;
import java.sql.Connection;
import java.sql.DriverManager;
import java.util.Properties;

public class ConnectionFactory {

	// Path의 경로를 가져오기 : 자기클래스명.class.getResource("파일이름").getPath()
    // 해석 : ConnectionFactory와 같은 패키지의 클래스의 "jdbc.properties" 파일의 경로를 가져오세요
	private String path = ConnectionFactory.class.getResource("jdbc.properties").getPath();
	
	private String DRV = null;
	private String URL = null;
	private String USR = null;
	private String PWD = null;

	private String insert = null;
	private String select = null;
	private String update = null;
	private String delete = null;
	
    //생성시 setUp() 메소드 바로 시작
	public ConnectionFactory() {
		try {
			setUp();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
	
    //생성자가 부르는 setUp()
	private void setUp() throws Exception {
		
		//Properties 객체 생성
		Properties p = new Properties();
		
		try {
			path = URLDecoder.decode(path, "utf-8"); 	// 한글깨짐 방지
			p.load(new FileReader(path));				// path의 경로 가져오기
		} catch (Exception e) {
			e.printStackTrace();
		}
	
        //Properties 객체의 정보 가져오기
		//a. Properties의 DB접속정보
		DRV = p.getProperty("jdbc.drv");
		URL = p.getProperty("jdbc.url");
		USR = p.getProperty("jdbc.usr");
		PWD = p.getProperty("jdbc.pwd");
		
		//b. Properties의 SQL 정보
		insert = p.getProperty("insert");
		select = p.getProperty("select");
		update = p.getProperty("update");
		delete = p.getProperty("delete");

		/* 나오는지 확인
		System.out.println(DRV);
		System.out.println(URL);
		System.out.println(USR);
		System.out.println(PWD);
		
		System.out.println(insert);
		System.out.println(select);
		System.out.println(update);
		System.out.println(delete);
		*/
		
        // JDBC 드라이버 로딩 - Oracle JDBC 드라이버의 Driver Class 로딩
		Class.forName(DRV);
	}
	
	//DB접속 메서드
    //객체 생성 후 접속을 위해 사용할 메소드임
	public Connection getConnection() {
		try {
			System.out.println("DB접속성공");
			return DriverManager.getConnection(URL, USR, PWD);
		} catch (Exception e) {
			System.out.println("DB접속실패");
			e.printStackTrace();
			return null;			
		}
	}

    //Properties 파일의 명령문 가져오는 메소드
	public String getInsert() {
		return insert;
	}

	public String getSelect() {
		return select;
	}

	public String getUpdate() {
		return update;
	}

	public String getDelete() {
		return delete;
	}

	
}

```

#### BoardDAOService : 게시판 인터페이스

```java
package com.lec.ex02_board;

import java.util.ArrayList;

public interface BoardDAOService {

	void createBoard();         // 글쓰기
	BoardVO viewBoard(int bno); // 내용조회
	void updateBoard(int bno);  // 글수정
	void deleteBoard(int bno);  // 글삭제
	
	ArrayList<BoardVO> listBoard(); // 전체글목록조회
	ArrayList<BoardVO> findBySubjectBoard(String subject); // 제목별조회
	ArrayList<BoardVO> findByWriterBoard(String writer); // 작성자조회
}

```

#### BoardDAOImpl : 게시판 구현 클래스

BoardDAOService를 구현함

```java
package com.lec.ex02_board;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.util.ArrayList;
import java.util.Scanner;

public class BoardDAOImpl implements BoardDAOService {

	// 글입력메서드 (새로생성)
	BoardVO inputBoard() {
        //게시판 Model 객체 생성
		BoardVO bd = new BoardVO();
        //Scanner로 값 입력받기
		Scanner sc = new Scanner(System.in);
		
        //입력받은 값으로 제목, 작성자, 글내용 입력받기
		System.out.println("글제목을 입력하세요 ==> ");
		bd.setSubject(sc.nextLine());
		
		System.out.println("작성자 입력하세요 ==> ");
		bd.setWriter(sc.nextLine());
		
		System.out.println("글내용을 입력하세요 ==> ");
		bd.setContent(sc.nextLine());
		
		return bd;
	}
	
	//추.클 구현하기
	@Override
	public void createBoard() {
		BoardVO bd = inputBoard();
		// System.out.println("insert into emp values(" + bd.getSubject());
		
		Connection conn = null;
		PreparedStatement pstmt = null;

		ConnectionFactory cf = new ConnectionFactory();
		conn = cf.getConnection(); //연결
		String sql = cf.getInsert(); // insert문 가져오기
		
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, bd.getSubject());
			pstmt.setString(2, bd.getWriter());
			pstmt.setString(3, bd.getContent());
			int row = pstmt.executeUpdate();
			System.out.println(row + " 건이 추가되었습니다!");
		} catch (Exception e) {
			System.out.println("게시판 추가 실패!!");
		} finally {
			try {
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}	
		}		
	}
	
	@Override
	public ArrayList<BoardVO> listBoard() {
		
		ArrayList<BoardVO> boardList = new ArrayList<BoardVO>();
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getSelect() 
					      + " where rownum between 1 and 10 "
					      + " order by bno desc";
//		 	System.out.println(sql);
			pstmt = conn.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			while(rs.next()) {
				BoardVO bd = new BoardVO();
				bd.setBno(rs.getInt(1));
				bd.setSubject(rs.getString("subject"));
				bd.setWriter(rs.getString("writer"));
				bd.setContent(rs.getString("content"));
				boardList.add(bd);
			}
		} catch (Exception e) {
			System.out.println("게시판 목록 조회 실패!!");
		} finally {
			try {
				if(rs!=null) rs.close();
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}			
		}
		return boardList;
	}
	
	@Override
	public void updateBoard(int bno) {
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getUpdate();
			// System.out.println(sql);
			
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, "[수정]제목");
			pstmt.setString(2, "[수정]내용");
			pstmt.setInt(3, bno);
			pstmt.executeUpdate();
			System.out.println("게시판 수정 성공!!");
		} catch (Exception e) {
			System.out.println("게시판 수정 실패!!");
		} finally {
			try {
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}			
		}		
	}
	
	@Override
	public void deleteBoard(int bno) {
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getDelete();
			
			pstmt = conn.prepareStatement(sql);
			pstmt.setInt(1, bno);
			pstmt.executeUpdate();
			System.out.println("게시판 삭제 성공!!");
		} catch (Exception e) {
			System.out.println("게시판 삭제 실패!!");
		} finally {
			try {
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}			
		}		
	}

	@Override
	public BoardVO viewBoard(int bno) {
		
		BoardVO bd = new BoardVO();
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getSelect()
					        + " where bno = " + bno;
			// System.out.println(sql);
			
			pstmt = conn.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			if(rs.next()) {
				bd.setSubject(rs.getString("subject"));
				bd.setWriter(rs.getString("writer"));
				bd.setContent(rs.getString("content"));
			} else {
				System.out.println("조회된 게시글이 없습니다!");
			}
		} catch (Exception e) {
			System.out.println("게시판 조회 실패!!");
			// e.printStackTrace();
		} finally {
			try {
				if(rs!=null) rs.close();
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}			
		}		
		return bd;
	}

	@Override
	public ArrayList<BoardVO> findBySubjectBoard(String subject) {
		
		ArrayList<BoardVO> boardList = new ArrayList<BoardVO>();
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getSelect() 
					      + " where subject like '%" + subject + "%' "
					      + " order by bno desc";
//		 	System.out.println(sql);
			pstmt = conn.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			while(rs.next()) {
				BoardVO bd = new BoardVO();
				bd.setBno(rs.getInt(1));
				bd.setSubject(rs.getString("subject"));
				bd.setWriter(rs.getString("writer"));
				bd.setContent(rs.getString("content"));
				boardList.add(bd);
			}
		} catch (Exception e) {
			System.out.println("게시판 목록 조회 실패!!");
		} finally {
			try {
				if(rs!=null) rs.close();
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}			
		}
		return boardList;
	}

	@Override
	public ArrayList<BoardVO> findByWriterBoard(String writer) {
		
		ArrayList<BoardVO> boardList = new ArrayList<BoardVO>();
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getSelect() 
					      + " where writer like '%" + writer + "%' "
					      + " order by bno desc";
//		 	System.out.println(sql);
			pstmt = conn.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			while(rs.next()) {
				BoardVO bd = new BoardVO();
				bd.setBno(rs.getInt(1));
				bd.setSubject(rs.getString("subject"));
				bd.setWriter(rs.getString("writer"));
				bd.setContent(rs.getString("content"));
				boardList.add(bd);
			}
		} catch (Exception e) {
			System.out.println("게시판 목록 조회 실패!!");
		} finally {
			try {
				if(rs!=null) rs.close();
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}			
		}
		return boardList;
	}

}
```

#### BoardFactory : 게시판 생성 클래스 (Singleton)

```java
package com.lec.ex02_board;

//＠ BoardDAOImpl을 싱글톤으로 만드는 클래스
public class BoardFactory {

	private static BoardDAOImpl bddao = null;
	
	// 외부에생성금지
	private BoardFactory() {}
	
	// Singletone
	public static BoardDAOImpl getInstance() {
		if(bddao == null) bddao = new BoardDAOImpl();
		return bddao;
	}
}

```

#### BoardUI : 게시판 처리 프로그램의 화면구성(메뉴)을 담당하는 클래스 

```java
package com.lec.ex02_board;

import java.util.ArrayList;

import javax.swing.JOptionPane;

public class BoardUI {

	private double ver;
	
    //생성자 호출 후 필드에 대입
	public BoardUI(double ver) {
		this.ver = ver;
	}

    // ★ 호출된 메소드
	public void mainBoardMenu() {
		
        // 게시판 인터페이스를 싱글톤 객체로 생성 ＠
		BoardDAOImpl bddao = BoardFactory.getInstance();
		
        // 바로 실행
		while(true) {
			
            // displayBoardMenu의 리턴값을 menuNo로 받음 ＆
			int menuNo = displayBoardMenu();
                     
			//받은 리턴값에 따라 실행되어야 하는 메소드들을 switch문으로 나눠줌
			switch(menuNo) {
			case 0: System.out.println("프로그램종료"); System.exit(0); break;
			case 1: makeBoard(bddao); break;
			case 2: listBoard(bddao); break;
			case 3: contentView(bddao); break;
			case 4: updateBoard(bddao); break;
			case 5: deleteBoard(bddao); break;
			case 6: findBySubject(bddao); break;
			case 7: findByWriter(bddao);
			}
		}
	}

   // ＆ showInputDialog로 내용을 출력하고 값을 받음
   private int displayBoardMenu() {
		String menuNo = JOptionPane.showInputDialog(
			"***** 게시판프로그램 V 1.0 *****\n\n" +
		    "1. 새로운 글쓰기\n" +
			"2. 전체글 목록 조회\n" +
			"3. 본문글 보기\n" +
			"4. 본문글 수정\n" +
			"5. 본문글 삭제\n" +
			"6. 제목으로 글 조회\n" +
			"7. 작성자로 글 조회\n" +
			"0. 종료\n\n" +
			"처리할 작업번호를 입력하세요\n");
		
		if(menuNo == null) return 0;          //값이 없거나
		if(menuNo.equals("")) return 0;       //null이면 0을 리턴하고
		else return Integer.parseInt(menuNo); //받은 나머지 값을 menuNo에 받음
	}
    
    // case 7                   
	private void findByWriter(BoardDAOImpl bddao) {
		
		String writer = JOptionPane.showInputDialog("작성자를 입력하세요!!\n");
		if(writer == null) return;
		if(writer.equals("")) return;
		
                         // BoardDAOImpl객체의 findByWriterBoard(bno)메서드 실행
		ArrayList<BoardVO> bds = bddao.findByWriterBoard(writer);
		
		System.out.println("==================================================================");
		System.out.println("번호\t\t제목\t\t작성자\t\t내용");
		System.out.println("==================================================================");
		
		for(BoardVO bd:bds) {
			System.out.println(bd.toString());
		}
		System.out.println("----------- 출력종료 ---------------\n\n\n");
	}

    // case 6 
	private void findBySubject(BoardDAOImpl bddao) {
		
		String subject = JOptionPane.showInputDialog("제목을 입력하세요!!\n");
		if(subject == null) return;
		if(subject.equals("")) return;
		
                            // BoardDAOImpl객체의 findBySubjectBoard(bno)메서드 실행
		ArrayList<BoardVO> bds = bddao.findBySubjectBoard(subject);
		
		System.out.println("==================================================================");
		System.out.println("번호\t\t제목\t\t작성자\t\t내용");
		System.out.println("==================================================================");
		
		for(BoardVO bd:bds) {
			System.out.println(bd.toString());
		}
		System.out.println("----------- 출력종료 ---------------\n\n\n");
	}

    // case 5      
	private void deleteBoard(BoardDAOImpl bddao) {

		String bno = JOptionPane.showInputDialog("삭제할 글 번호를 입력하세요!");
		
		if(bno == null) return;
		if(bno.equals("")) return;
		else {
            // BoardDAOImpl객체의 deleteBoard(bno)메서드 실행
			bddao.deleteBoard(Integer.parseInt(bno));
		}
	}

    // case 4     
	private void updateBoard(BoardDAOImpl bddao) {

		String bno = JOptionPane.showInputDialog("수정할 글 번호를 입력하세요!");
		
		if(bno == null) return;
		if(bno.equals("")) return;
		else {
            // BoardDAOImpl객체의 parseInt(bno)메서드 실행
			bddao.updateBoard(Integer.parseInt(bno));
		}
	}

    // case 3      
	private void contentView(BoardDAOImpl bddao) {
		
		String bno = JOptionPane.showInputDialog("조회할 글 번호를 입력하세요!");
		
		if(bno == null) return;
		if(bno.equals("")) return;
		else {
            // BoardDAOImpl객체의 viewBoard(Integer.parseInt(bno))메서드 실행
			BoardVO bd = bddao.viewBoard(Integer.parseInt(bno));
			System.out.println("글제목 : " + bd.getSubject());
			System.out.println("작성자 : " + bd.getWriter());
			System.out.println("글내용 : " + bd.getContent());
		}
	}

    // case 2
	private void listBoard(BoardDAOImpl bddao) {
    
        // BoardDAOImpl객체의 listBoard()메서드 실행
		ArrayList<BoardVO> bds = bddao.listBoard();
		
		System.out.println("==================================================================");
		System.out.println("번호\t\t제목\t\t작성자\t\t내용");
		System.out.println("==================================================================");
		
		for(BoardVO bd:bds) {
			System.out.println(bd.toString()); 
		}
		System.out.println("----------- 출력종료 ---------------\n\n\n");
	}
	
    // case 1
	private void makeBoard(BoardDAOImpl bddao) {
		bddao.createBoard(); // BoardDAOImpl객체의 createBoard()메서드 실행
	}
}
```

#### Board : 메인클래스

```java
package com.lec.ex02_board;

import java.util.ArrayList;

public class Board {
public static void main(String[] args) {
    
	//게시판 처리 프로그램의 화면구성(메뉴)을 담당하는 클래스를 버전 1.0으로 인스턴스생성
	BoardUI bui = new BoardUI(1.0);    
	//인스턴스의 mainBoardMenu()호출 ★
    bui.mainBoardMenu();
}
}
```