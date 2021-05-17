---
layout: default
title: Oracle
parent: Database
nav_order: 5
has_children: true
---

# Oracle
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Oracle Installation

### Oracle Express Edition Download & Install

1. [다운로드](https://www.oracle.com/database/technologies/xe-prior-releases.html) : Oracle Database 11gR2 Express Edition for Windows x64

2. 압축 풀고 setup.exe 를 실행

### Navicat Install

1. Navicat Premium 15.zip 압축풀기

2. navicat150_premium_en_x64.exe 실행후 설치

3. RegPrivateKey.pem 실행 후 설정 마친 후 Key Generate

    (Error Message 무시 후 close)
    
4. Navicat에 Key 붙여넣기 

5. Navicat에서 생성된 코드 RegPrivateKey.pem Request Code에 붙여넣기

6. RegPrivateKey.pem에서 Activation Code 다시 Navicat에 붙여넣기

7. 모두 마친 후 Navicat 재시작 

### Oracle DB Connecting 

**제대로 설치 되었는지 commanline으로 연결 확인**

1. Window Menu > Run SQL Command Line 실행

2. Command Line

    ```sql
    -- 1. DB 접속
    SQL> conn sys/12345 as sysdba
        -- Connected 확인 : 접속성공
        
    -- 2. 현재 사용자 확인 
    SQL> show user 
        -- USER is "SYS"
        
    -- 3. 다른 사용자접속
    SQL> conn hr/hr
        -- hr 사용자는 기본적으로 lock 되어있음
         
    SQL> exit
    ```
    
3. Navicat 실행

    a. File > New Connection > Oracle
    
    b. New Connection
         ... Connection Name : sys
         ... Host            : localhost
         ... Service Name    : XE
         ... User Name       : sys
         ... password        : 12345
      c. (tab) Advanced
         ... Role            : SYSDBA
      d. (button) Test Connection
         ... Connection Successful
      e. (button)OK
      f. (menu) Tools > Options > Enviroment 
         ... OCI Environment 
         ... c:Progrman Files/premium soft/..../instanceclient_10_?/oci.dll 
         ... (button) 열기
      g. 좌측 Tree Menu : sys를 더블클릭
         ... 접속확인
         
&#8594; 여기까지 실행 잘 되면 제대로 설치된것!

---

## Oracle DB Environment Setting

### Search Oracle DB Current Environment

1. Run SQL Command Line 실행

    ```sql
    -- 1. DB 접속
    SQL> conn sys/12345 as sysdba
        -- Connected 확인 : 접속성공
        
    -- 2. 현재 사용자 확인 
    SQL> show user 
        -- USER is "SYS"
        
    -- 3. 다른 사용자접속
    SQL> conn hr/hr
        -- hr 사용자는 기본적으로 lock 되어있음
    
         conn scott
         -- scott 사용자는 없음
    ```
    
    &#8594; hr사용자는 lock해제해야 하고 scott사용자는 새로 생성해야함
    
2. Navicat 실행

    SYS table에서 `SQL > select * from v$nls_parameters;` 검색
    
    (위 SQL Command Line에서도 볼 수 있지만, 테이블 형식은 보기 힘들어서 navicat에서 실행 후 확인)
    
    ![](https://gekdev.github.io/docs/database/oracle/example/search_table.JPG)
    

### Change Oracle DB Environment Setting

b. 날짜형식 변경하기

 SQL> alter session set nls_date_format = 'YYYY-MM-DD';
      ... NLS_DATE_FORMAT=DD-MON-RR 을 YYYY-MM-DD'로 변경
 SQL> alter session set NLS_TIMESTAMP_FORMAT = 'YYYY-MM-DD HH:MI:SS';

c. 변경정보를 영구적으로 변경

 명령) alter [session/system]
 a) session : 현재 접속한 session에서만 변경되고 접속을 끊은후 다시 접속하면 
              변경전 환경으로 복귀된다.
 b) system  : database의 정보를 영구적으로 변경
    ... 옵션 scope=[both/spfile]
        --> both : 바로 적용 or 재시작(오류가 날 가능성이 많다.)
        --> spfile : db를 종료후 재시작

 c) 변경하기

SQL> alter system set nls_date_format = 'YYYY-MM-DD' scope=spfile;
SQL> alter system set NLS_TIMESTAMP_FORMAT = 'YYYY-MM-DD HH:MI:SS' scope=spfile;
SQL> exit

d. DB재시작 : 

Window Mene > Oracle XE.....
a) stop database
b) start database


### 연결하고자 하는 데이터 베이스 Connection

connection Name = 서버 이름

1. **File &#8594; New Connection**

    ![](https://gekdev.github.io/docs/database/oracle/example/newconnection.jpg)

2. 왼쪽 끝에 있는 **Connection 아이콘**

    ![](https://gekdev.github.io/docs/database/oracle/example/connection_icon.jpg)

### 오라클 데이터베이스에 new Connection

![](https://gekdev.github.io/docs/database/oracle/example/newcon_oracle.JPG)

&#9656; Connection Name : sys

&#9656; Hose : localhost

&#9656; Service Name : XE로 해야지 오류가 나지않음

&#9656; User Name : sys => 최고 관리자

&#9656; password : 12345

![](https://gekdev.github.io/docs/database/oracle/example/newcon_oracle2.JPG)

&#9656; Advanced / Role : SYSDBA

&#9656; 왼쪽 아래 text connections 버튼 확인 후 Connection Successful 나오면 ok

![](https://gekdev.github.io/docs/database/oracle/example/dllfile.JPG)

Tools > Options > Enviroment > OCI Environment > OCI Library

c:Progrman Files/premium soft/..../instanceclient_10_?/oci.dll 

### Custom Database

![](https://gekdev.github.io/docs/database/oracle/example/custom_dbase.JPG)

원하는 데이터 베이스를 체크해서 보고싶은 데이터베이스만 볼 수 있음

### Connection된 Database

![](https://gekdev.github.io/docs/database/oracle/example/connected.JPG)

connection되면 빨갛게 불이 들어옴

![](https://gekdev.github.io/docs/database/oracle/example/connection_close.jpg)


### Open External File

다른 sql 파일들을 가져올 수 있음

![](https://gekdev.github.io/docs/database/oracle/example/open_file.png)

---

### 

여러개 동시에 선택하면 아래 창에 여러개 값이 한꺼번에 나와서 비교 가능함

![](https://gekdev.github.io/docs/database/oracle/example/drag.JPG)


## Connection Create

### SYS

SYS 테이블 중 dba_users가 있음


![](https://gekdev.github.io/docs/database/oracle/example/change_format.JPG)

SQL Command Line에서 

`conn sys/12345 as sysdba`로 SYS와 connection 후

nls_date_format테이블의 형식을 바꿈

![](https://gekdev.github.io/docs/database/oracle/example/reformed.JPG)

바꾼 후 모습 

### HR 

![](https://gekdev.github.io/docs/database/oracle/example/hr.JPG)

&#9656; Hose => localhost

&#9656; Service Name => XE로 해야지 오류가 나지않음

&#9656; User Name : hr

![](https://gekdev.github.io/docs/database/oracle/example/custom_onlyhr.JPG)

hr 데이터베이스만 보게 하기

![](https://gekdev.github.io/docs/database/oracle/example/locked.JPG)

**접속하려면 기본값으로 hr은 잠겨있음**

&#8594; SYS에서 관리자 권한으로 풀어줘야 함

### SCOTT

![](https://gekdev.github.io/docs/database/oracle/example/scott.JPG)

1. SYS 권한으로 SCOTT 생성

    `create user scott identified by tiger`

    identified = 비밀번호
    
2. SCOTT 에 권한 부여하기

3. 작업장소 지정하기

---

### Setting Fonts

![](https://gekdev.github.io/docs/database/oracle/example/setting_font.JPG)

----

## Example


