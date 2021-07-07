---
layout: default
title: Board
parent: Application EX
grand_parent : JSP
nav_order: 2
---

# Application Board
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 게시판 폴더 만들고 설정

1. 새로운 프로젝트 생성

    jso08_member

2. 라이브러리 모두 가져오기

    * commons-dbcp2-2.8.0.jar
    
    * commons-logging-1.2.jar
    
    * commons-pool2-2.9.0.jar
    
    * jstl-1.2.jar
    
    * mariadb-java-client-2.7.3.jar
    
3.

## 데이터베이스 생성

1. board_member 테이블 생성

```sql
create table board_member(
	member_id 		varchar(15),
	member_pw 		varchar(13),
	member_name 	varchar(20),
	member_age 		int,
	member_gender	varchar(5),
	member_email	varchar(30),
	primary key(member_id)	
);
```

2. board 테이블 생성

```sql
create table board(
	board_num 			int,
	board_name 			varchar(20) not null,
	board_pass 			varchar(15) not null,
	board_subject		varchar(50) not null,
	board_content		varchar(2000) not null,
	board_file 			varchar(50),
	board_re_ref 	    int not null,
	board_re_lev 	    int not null,
	board_re_seq 	    int not null,
	board_readcount	    int default 0,
	board_date 			date,
	primary key(board_num)
);
```

유저를 localhost로 만드는 방법

mysql
```sql
create user 'scott'@'localhost' identified by 12345;  //내부망에서 접근하는 유져
create user 'scott'@'%' identified by 12345;          //외부망에서 접근하는 유져
```

권한주기

mysql
```sql
grant all privileges on *.* to 'scott'@'localhost';
grant all privileges on *.* to 'scott'@'%';
```

```sql
create table board(
	board_num 			int,
	board_name 			varchar(20) not null,
	board_pass 			varchar(15) not null,
	board_subject		varchar(50) not null,
	board_content		varchar(2000) not null,
	board_file 			varchar(50) not null,
	board_re_ref 	    int not null,
	board_re_lev 	    int not null,
	board_re_seq 	    int not null,
	board_readcount	    int default 0,
	board_date 			date,
	primary key(board_num)
);

select * from board;

update board set board_readcount = board_readcount + 1 where board_num = 1;

select max(board_num) from board;

delete from board;

 delimiter //
 begin not atomic 
     declare i int default 1;
     while(i <= 1001) do
         insert into board(board_num, board_name, board_pass, board_subject, board_content, 
				 board_file, board_re_ref, board_re_lev, board_re_seq, board_readcount, board_date)
             values(i, concat('작성자_',i), '1', concat('메시지제목_', i), concat('메시지내용_', i), '', i, 0, 0, 0, curdate());
             set i = i + 1;
     end while;
 end;
 ```