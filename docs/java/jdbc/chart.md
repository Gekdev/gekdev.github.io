---
layout: default
title: Chart
parent: JDBC
grand_parent: Java
nav_order: 2
---

# JDBC Chart
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Chart Application

**Board를 바탕으로 복습하면서 내가 생성한 sql 테이블로 프로그램 짜기**

### Chart table

```sql
create table scott.chart (
	CHT_NUMBER	number          not null primary key
  , EMP_NUMBER	number    		default  0
  , DIG_NUMBER	number   		default  0
  , DOC_NUMBER	number         	not null  
  , PAT_NUMBER	number         	not null
  , CHT_LOC     varchar2(256)
);

create sequence scott.chart_chtnum_s;
```

### jdbc.properties 

```properties
jdbc.drv=oracle.jdbc.OracleDriver
jdbc.url=jdbc:oracle:thin:@localhost:1521:XE
jdbc.usr=scott
jdbc.pwd=tiger

insert=insert into chart(CHT_NUMBER, DOC_NUMBER, PAT_NUMBER, CHT_LOC) values(scott.chart_chtnum_s.nextval,?,?,?)
select=select * from chart
update=update chart set DOC_NUMBER=?, PAT_NUMBER=?, CHT_LOC=? where CHT_NUMBER=?
delete=delete from chart where CHT_NUMBER=?

mysql.drv=com.mysql.jdbc.Driver
mysql.url=jdbc:mysql://localhost:3306/chart
mysql.usr=root
mysql.pwd=12345

mariadb.drv=
mariadb.url=
mariadb.usr=
mariadb.pwd=
```

### Chart Program

#### ChartVO 

```java
package project;

public class ChartVO {

	private int cht_num;
	private int emp_num;
	private int dig_num;
	private int doc_num;
	private int pat_num;
	private String cht_loc;
	
	public ChartVO() {
		this.cht_num = 0;
		this.emp_num = 0;
		this.dig_num = 0;
		this.doc_num = 0;
		this.pat_num = 0;
		this.cht_loc = null;
	}

	public int getCht_num() {
		return cht_num;
	}

	public void setCht_num(int cht_num) {
		this.cht_num = cht_num;
	}

	public int getEmp_num() {
		return emp_num;
	}

	public void setEmp_num(int emp_num) {
		this.emp_num = emp_num;
	}

	public int getDig_num() {
		return dig_num;
	}

	public void setDig_num(int dig_num) {
		this.dig_num = dig_num;
	}

	public int getDoc_num() {
		return doc_num;
	}

	public void setDoc_num(int doc_num) {
		this.doc_num = doc_num;
	}

	public int getPat_num() {
		return pat_num;
	}

	public void setPat_num(int pat_num) {
		this.pat_num = pat_num;
	}

	public String getCht_loc() {
		return cht_loc;
	}

	public void setCht_loc(String cht_loc) {
		this.cht_loc = cht_loc;
	}

	@Override
	public String toString() {
		return cht_num + "\t\t" + doc_num + "\t\t" + pat_num + "\t\t" + cht_loc;
	}
	
}
```

#### ConnectionFactory 

**꼭@@@ ojdbc8-21.1.0.0.jar 를 가져와야함 그래야 Class.forName(DRV);할 수 있음**

```java
package project;

import java.io.FileReader;
import java.net.URLDecoder;
import java.sql.Connection;
import java.sql.DriverManager;
import java.util.Properties;

public class ConnectionFactory {

	private String path = ConnectionFactory.class.getResource("jdbc.properties").getPath();
	
	private String DRV = null;
	private String URL = null;
	private String USR = null;
	private String PWD = null;

	private String insert = null;
	private String select = null;
	private String update = null;
	private String delete = null;
	
	public ConnectionFactory(){
		try {
			setUp();
		} catch (Exception e) {
			System.out.println("setUp() 함수 호출이 중단되었습니다");
			//e.printStackTrace();
		}
	}

	private void setUp() throws Exception{
		
		Properties p = new Properties();
		path = URLDecoder.decode(path, "utf-8");
		p.load(new FileReader(path));

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
		
		/* 출력 확인 OK 
		System.out.println(DRV);
		System.out.println(URL);
		System.out.println(USR);
		System.out.println(PWD);
		
		System.out.println(insert);
		System.out.println(select);
		System.out.println(update);
		System.out.println(delete);
		*/
		
		Class.forName(DRV);
		
	}
	
	//DB접속 메서드 (객체 생성 후 접속을 위해 사용할 메소드)
	public Connection getConnection() {
		try {
			return DriverManager.getConnection(URL,USR,PWD);
		} catch (Exception e) {
			System.out.println("DB접속실패");
			//e.printStackTrace();
			return null;
		}
	}

	//명령문 GETTER
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

#### ChartDAOService

```java
package project;

import java.util.ArrayList;

public interface ChartDAOService {

	// ⓐ 글쓰기
	void createChart();
	// ⓑ 글 수정
	void updateChart(int cht_num);
	// ⓒ 글 삭제
	void deleteChart(int cht_num);
	// ⓓ 내용 조회
	ChartVO viewChart(int cht_num);
	
	// ⓔ 전체 글 목록 조회
	ArrayList<ChartVO> listChart();
	// ⓕ 의사번호로 조회하기
	ArrayList<ChartVO> findByDocNumChart(int doc_num);	
	// ⓖ 환자번호로 조회하기
	ArrayList<ChartVO> findByPatNumChart(int pat_num);	
	
}
```

#### ChartDAOImpl

```java
package project;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.Scanner;

public class ChartDAOImpl implements ChartDAOService{

	// ★ 새로 생성된 글 입력 메서드
	ChartVO inputChart() {
		
		//차트 Model 객체 생성
		ChartVO ct = new ChartVO();
        //Scanner로 값 입력받기
		Scanner sc = new Scanner(System.in);
		
        //입력받은 값으로 제목, 작성자, 글내용 입력받기		
		System.out.println("차트내용을 입력하세요 ==> ");
		ct.setCht_loc(sc.nextLine());
		
		System.out.println("의사번호를 입력하세요 ==> ");
		ct.setDoc_num(sc.nextInt());
		
		System.out.println("환자번호를 입력하세요 ==> ");
		ct.setPat_num(sc.nextInt());
		
		return ct;
	}
	
	// ⓐ 글쓰기
	@Override
	public void createChart() {
		
		ChartVO ct = inputChart();
		
		/*입,출력 확인 ok 
		System.out.println("insert into"+ ct.getCht_num());
		
		//Chart에서 실행 ->
		//	ChartDAOImpl dao = new ChartDAOImpl();
		//	dao.createChart();
		*/
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		
		ConnectionFactory cf = new ConnectionFactory();
		conn = cf.getConnection();
		String sql = cf.getInsert();
		
		/* 출력 확인 ok 
		System.out.println(sql);
		//insert into chart(CHT_NUMBER, DOC_NUMBER, PAT_NUMBER, CHT_LOC) values(scott.chart_chtnum_s.nextval,?,?,?)
		*/
		
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setInt(1, ct.getDoc_num());	
			pstmt.setInt(2, ct.getPat_num());
			pstmt.setString(3, ct.getCht_loc());
			int row = pstmt.executeUpdate();
			System.out.println(row + "건이 추가되었습니다");
		} catch (Exception e) {
			System.out.println("차트 Insert 실패");
		}finally {
			try {
				if(pstmt!=null) pstmt.close();
				if(conn!=null) pstmt.close();
			} catch (SQLException e) {
				System.out.println("Connection이 제대로 닫히지 않았습니다");
			}
		}
	}
	
	// ★ 새로 생성된 글 수정 메서드
	ChartVO changeChart() {
		
		//차트 Model 객체 생성
		ChartVO ct = new ChartVO();
        //Scanner로 값 입력받기
		Scanner sc = new Scanner(System.in);
		
        //입력받은 값으로 제목, 작성자, 글내용 입력받기		
		System.out.println("수정할 차트내용을 입력하세요 ==> ");
		ct.setCht_loc(sc.nextLine());
		
		System.out.println("수정할 의사번호를 입력하세요 ==> ");
		ct.setDoc_num(sc.nextInt());
		
		System.out.println("수정할 환자번호를 입력하세요 ==> ");
		ct.setPat_num(sc.nextInt());
		
		return ct;
	}
	
	// ⓑ 글 수정
	@Override
	public void updateChart(int cht_num) {
		
		ChartVO ct = changeChart();
		Connection conn = null;
		PreparedStatement pstmt = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getUpdate();
			
			/* 출력 확인 ok 
			System.out.println(sql);
			//update chart set DOC_NUMBER=?, PAT_NUMBER=?, CHT_LOC=? where CHT_NUMBER=?
			*/
			
			pstmt = conn.prepareStatement(sql);
			pstmt.setInt(1, ct.getDoc_num());	
			pstmt.setInt(2, ct.getPat_num());
			pstmt.setString(3, ct.getCht_loc());
			pstmt.setInt(4, cht_num);
			pstmt.executeUpdate();
			System.out.println("게시판이 수정되었습니다");
		} catch (Exception e) {
			System.out.println("게시판이 수정되지 않았습니다");
		} finally {
			try {
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e) {
				System.out.println("Connection이 제대로 닫히지 않았습니다");
			}
		}	
		
	}

	// ⓒ 글 삭제
	@Override
	public void deleteChart(int cht_num) {
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getDelete();
			
			/* 출력 확인 ok 
			System.out.println(sql);
			//delete from chart where CHT_NUMBER=?
			*/
			
			pstmt = conn.prepareStatement(sql);
			pstmt.setInt(1, cht_num);
			pstmt.executeUpdate();
			System.out.println("게시판이 삭제되었습니다");
		} catch (Exception e) {
			System.out.println("게시판이 삭제되지 않았습니다");
		} finally {
			try {
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e) {
				System.out.println("Connection이 제대로 닫히지 않았습니다");
			}
		}
		
	}

	// ⓓ 내용 조회
	@Override
	public ChartVO viewChart(int cht_num) {
		
		ChartVO ct = new ChartVO();
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getSelect() + " where CHT_NUMBER = " + cht_num;

			/* 출력 확인 ok 
			System.out.println(sql);
			//select * from chart where CHT_NUMBER = 3
			*/
			
			pstmt = conn.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			if(rs.next()) {
				ct.setDoc_num(rs.getInt("DOC_NUMBER"));
				ct.setPat_num(rs.getInt("PAT_NUMBER"));
				ct.setCht_loc(rs.getString("CHT_LOC"));
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
		
		return ct;
	}

	// ⓔ 전체 글 목록 조회
	@Override
	public ArrayList<ChartVO> listChart() {
		
		ArrayList<ChartVO> chartList = new ArrayList<ChartVO>();
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getSelect() 
					      + " where rownum between 1 and 10 "
					      + " order by CHT_NUMBER desc";
			
			/* 출력 확인 ok 
			System.out.println(sql);
			//select * from chart where rownum between 1 and 10  order by CHT_NUMBER desc
			*/
			
			pstmt = conn.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			while(rs.next()) {
				ChartVO ct = new ChartVO();
				ct.setCht_num(rs.getInt(1));
				ct.setDoc_num(rs.getInt("DOC_NUMBER"));
				ct.setPat_num(rs.getInt("PAT_NUMBER"));
				ct.setCht_loc(rs.getString("CHT_LOC"));
				chartList.add(ct);
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
		
		return chartList;
	}

	// ⓕ 의사번호로 조회하기
	@Override
	public ArrayList<ChartVO> findByDocNumChart(int doc_num) {
		
		ArrayList<ChartVO> chartList = new ArrayList<ChartVO>();
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getSelect() + " where DOC_NUMBER like '%" + doc_num + "%'"
				      					+ " order by CHT_NUMBER desc";

			/* 출력 확인 ok 
			System.out.println(sql);
			//select * from chart where DOC_NUMBER like '%1%' order by CHT_NUMBER desc
			*/
			
			pstmt = conn.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			while(rs.next()) {
				ChartVO ct = new ChartVO();
				ct.setCht_num(rs.getInt(1));
				ct.setDoc_num(rs.getInt("DOC_NUMBER"));
				ct.setPat_num(rs.getInt("PAT_NUMBER"));
				ct.setCht_loc(rs.getString("CHT_LOC"));
				chartList.add(ct);
			}
			
		} catch (Exception e) {
			System.out.println("의사번호로 게시판 조회 실패!!");
		}finally {
			try {
				if(rs!=null) rs.close();
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}	
		}
		
		return chartList;
	}

	// ⓖ 환자번호로 조회하기
	@Override
	public ArrayList<ChartVO> findByPatNumChart(int pat_num) {
				
		ArrayList<ChartVO> chartList = new ArrayList<ChartVO>();
		
		Connection conn = null;
		PreparedStatement pstmt = null;
		ResultSet rs = null;
		
		try {
			ConnectionFactory cf = new ConnectionFactory();
			conn = cf.getConnection();
			String sql = cf.getSelect() + " where PAT_NUMBER like '%" + pat_num + "%'"
				      					+ " order by CHT_NUMBER desc";

			/* 출력 확인 ok 
			System.out.println(sql);
			//select * from chart where PAT_NUMBER like '%1%' order by CHT_NUMBER desc
			*/
			
			pstmt = conn.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			while(rs.next()) {
				ChartVO ct = new ChartVO();
				ct.setCht_num(rs.getInt(1));
				ct.setDoc_num(rs.getInt("DOC_NUMBER"));
				ct.setPat_num(rs.getInt("PAT_NUMBER"));
				ct.setCht_loc(rs.getString("CHT_LOC"));
				chartList.add(ct);
			}
			
		} catch (Exception e) {
			System.out.println("환자번호로 게시판 조회 실패!!");
		}finally {
			try {
				if(rs!=null) rs.close();
				if(pstmt!=null) pstmt.close();
				if(conn!=null) conn.close();
			} catch (Exception e2) {
				// dummy
			}	
		}
		
		return chartList;
	}

}
```

#### ChartFactory 

```java
package project;

public class ChartFactory {

	private static ChartDAOImpl ctdao = null;
	
	private ChartFactory() {}
	
	public static ChartDAOImpl getInstance() {
		if(ctdao == null) ctdao = new ChartDAOImpl();
		return ctdao;
	}
}
```

#### ChartUI 

```java
package project;

import java.util.ArrayList;

import javax.swing.JOptionPane;

public class ChartUI {

	private double ver;
	
	public ChartUI(double ver) {
		this.ver = ver;
	}
	
	public void mainChartMenu() {
		
		ChartDAOImpl ctdao = ChartFactory.getInstance();
		//System.out.println(ctdao);
		
		while(true) {
			
			//메뉴창 실행
			int menuNo = displayBoardMenu();
			
			//실행해서 받은 값에 따라 함수 실행
			switch(menuNo) {
				case 0: System.out.println("프로그램종료"); System.exit(0); break;
				case 1: makeChart(ctdao); break;
				case 2: listChart(ctdao); break;
				case 3: updateChart(ctdao); break;
				case 4: deleteChart(ctdao); break;
				case 5: contentView(ctdao); break;
				case 6: findByDocNum(ctdao); break;
				case 7: findByPatNum(ctdao);
			}
			
		}
		
	}
	
	private int displayBoardMenu() {
		
		String menuNo = JOptionPane.showInputDialog(
			"***** 게시판프로그램 V 1.0 *****\n\n" +
			    "1. 새로운 차트 쓰기\n" +
				"2. 전체차트 목록 조회\n" +
				"3. 차트 수정\n" +
				"4. 차트 삭제\n" +
				"5. 차트 보기\n" +
				"6. 의사번호로 차트 조회\n" +
				"7. 환자번호로 차트 조회\n" +
				"0. 종료\n\n" +
				"처리할 작업번호를 입력하세요\n");
		
		if(menuNo == null) return 0;        
		if(menuNo.equals("")) return 0;       
		else return Integer.parseInt(menuNo); 
		
	}
	
	// Case 1
	private void makeChart(ChartDAOImpl ctdao) {
		// ⓐ 글쓰기
		ctdao.createChart();
	}

	// Case 2
	private void listChart(ChartDAOImpl ctdao) {
		
		// ⓔ 전체 글 목록 조회
		ArrayList<ChartVO> cts = ctdao.listChart();
		
		System.out.println("==================================================================");
		System.out.println("차트번호\t의사번호\t환자번호\t차트내용");
		System.out.println("==================================================================");
		
		for(ChartVO ct:cts) {
			System.out.println(ct.toString()); 
		}
		
		System.out.println("==================================================================\n\n\n");

	}

	// Case 3
	private void updateChart(ChartDAOImpl ctdao) {
		
		String cht_num = JOptionPane.showInputDialog("수정할 글 번호를 입력하세요!");
		
		if(cht_num == null) return;
		if(cht_num.equals("")) return;
		else {
			// ⓑ 글 수정
			ctdao.updateChart(Integer.parseInt(cht_num));
		}
		
	}
	
	// Case 4
	private void deleteChart(ChartDAOImpl ctdao) {
		
		String cht_num = JOptionPane.showInputDialog("삭제할 글 번호를 입력하세요!");
		
		if(cht_num == null) return;
		if(cht_num.equals("")) return;
		else {
			// ⓒ 글 삭제
			ctdao.deleteChart(Integer.parseInt(cht_num));
		}
		
	}

	// Case 5
	private void contentView(ChartDAOImpl ctdao) {
		
		String cht_num = JOptionPane.showInputDialog("조회할 글 번호를 입력하세요!");
		
		if(cht_num == null) return;
		if(cht_num.equals("")) return;
		else {
			// ⓓ 내용 조회
			ChartVO ct = ctdao.viewChart(Integer.parseInt(cht_num));
			System.out.println("의사번호: " + ct.getDoc_num());
			System.out.println("환자번호: " + ct.getPat_num());
			System.out.println("진료번호: " + ct.getDig_num());
			System.out.println("차트내용: " + ct.getCht_loc());
		}
		
	}

	// Case 6
	private void findByDocNum(ChartDAOImpl ctdao) {
		
		String doc_num = JOptionPane.showInputDialog("의사 번호를 입력하세요 \n");
		
		if(doc_num == null) return;
		if(doc_num.equals("")) return;

		// ⓕ 의사번호로 조회하기
		ArrayList<ChartVO> cts = ctdao.findByDocNumChart(Integer.parseInt(doc_num));
				
		System.out.println("==================================================================");
		System.out.println("차트번호\t의사번호\t환자번호\t차트내용");
		System.out.println("==================================================================");
		
		for(ChartVO ct:cts) {
			System.out.println(ct.toString()); 
		}
		
		System.out.println("==================================================================\n\n\n");
			
	}

	// Case 7
	private void findByPatNum(ChartDAOImpl ctdao) {
		
		String doc_num = JOptionPane.showInputDialog("환자 번호를 입력하세요 \n");
				
		if(doc_num == null) return;
		if(doc_num.equals("")) return;

		// ⓖ 환자번호로 조회하기
		ArrayList<ChartVO> cts = ctdao.findByPatNumChart(Integer.parseInt(doc_num));
				
		System.out.println("==================================================================");
		System.out.println("차트번호\t의사번호\t환자번호\t차트내용");
		System.out.println("==================================================================");
		
		for(ChartVO ct:cts) {
			System.out.println(ct.toString()); 
		}
		
		System.out.println("==================================================================\n\n\n");

	}
}
```

#### Chart 

```java
package project;

public class Chart {
public static void main(String[] args) {
	
	ChartUI ui = new ChartUI(1.0);
	ui.mainChartMenu();
	
}
}
```