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

0. window defender off

1. Navicat Premium 15.zip 압축풀기

2. navicat150_premium_en_x64.exe 실행후 설치

3. RegPrivateKey.pem 실행 후 설정 마친 후 Key Generate

    (Error Message 무시 후 close)
    
4. Navicat에 Key 붙여넣기 

5. Navicat에서 생성된 코드 RegPrivateKey.pem Request Code에 붙여넣기

6. RegPrivateKey.pem에서 Activation Code 다시 Navicat에 붙여넣기

7. 모두 마친 후 Navicat 재시작

<span class="fs-2">
[자세히 확인하기](/navicatpatch순서.txt){: .btn .btn-outline .mt-2}
</span>

### Oracle DB Connecting 

**제대로 설치 되었는지 commanline으로 연결 확인**

1. Window Menu > Run SQL Command Line 실행

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
    
2. [Navicat 실행]()
         
&#8594; 여기까지 실행 잘 되면 제대로 설치된것!

---

## Oracle DB Environment Setting

### Search Current Oracle DB Environment

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
    
    &#8594; [hr사용자는 lock해제해야 하고 scott사용자는 새로 생성해야함]()
    
2. Navicat 실행

    SYS table에서 `SQL > select * from v$nls_parameters;` 검색
    
    (위 SQL Command Line에서도 볼 수 있지만, 테이블 형식은 보기 힘들어서 navicat에서 실행 후 확인)
    
    &#8594; [NLS_DATE_FORMAT, NLS_TIMESTAMP_FORMAT을 변경할 예정]()
    
    ![](https://gekdev.github.io/docs/database/oracle/example/search_table.JPG)
    

### Change Oracle DB Environment Setting

#### Change Date Format

 **영구적으로 변경해야 하니 system 변경 명령어로 사용해야 함**

![](https://gekdev.github.io/docs/database/oracle/example/change_format.JPG)

 syntax
 {: .label .mt-2}
 <div class="code-example" markdown="1">
 명령문 : alter [session/system] ...

 * session : **현재 접속한 session에서만 변경**되고 접속을 끊은 후 다시 접속하면 **변경전 환경으로 복귀됨**

 * system  : **database의 정보를 영구적으로 변경**

     옵션 : **scope=[both/spfile]**

     &#9656; both : 바로 적용 or 재시작(오류가 날 가능성이 많음)

     &#9656; spfile : db를 종료후 재시작
 </div>
 ```sql
 -- Session changing
 SQL> alter session set nls_date_format = 'YYYY-MM-DD';
      -- ... NLS_DATE_FORMAT=DD-MON-RR 을 YYYY-MM-DD'로 변경
 SQL> alter session set NLS_TIMESTAMP_FORMAT = 'YYYY-MM-DD HH:MI:SS';

 -- System changing
 SQL> alter system set nls_date_format = 'YYYY-MM-DD' scope=spfile;
 SQL> alter system set NLS_TIMESTAMP_FORMAT = 'YYYY-MM-DD HH:MI:SS' scope=spfile;
 SQL> exit
 ```

![](https://gekdev.github.io/docs/database/oracle/example/reformed.JPG)

&#8594; 변경 후 모습

#### Restart Database

**데이터 포멧을 변경한 후에는 꼭 데이터베이스를 재시작 해줘야 함**

&#9656; Stop database(app) 실행 후 Start database(app) 실행

---

## Oracle DB Creating & Connecting

### New Database Connection

connection Name = 서버 이름

1. **File &#8594; New Connection**

    ![](https://gekdev.github.io/docs/database/oracle/example/newconnection.jpg)

2. 왼쪽 끝에 있는 **Connection 아이콘**

    ![](https://gekdev.github.io/docs/database/oracle/example/connection_icon.jpg)

### New Connection Setting

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

&#9656; Tools > Options > Enviroment > OCI Environment > OCI Library

&#9656; 경로를 c:Progrman Files/premium soft/..../instanceclient_10_?/oci.dll 

### Custom Database

![](https://gekdev.github.io/docs/database/oracle/example/custom_dbase.JPG)

&#9656; 원하는 데이터 베이스를 체크해서 보고싶은 데이터베이스만 볼 수 있음

### Connection된 Database

![](https://gekdev.github.io/docs/database/oracle/example/connected.JPG)

&#9656; connection되면 빨갛게 불이 들어옴

![](https://gekdev.github.io/docs/database/oracle/example/connection_close.jpg)

&#9656; 마우스 오른쪽 눌러서 connection 종료

---

## Open External File

다른 sql 파일들을 가져올 수 있음

![](https://gekdev.github.io/docs/database/oracle/example/open_file.png)

---

### 

여러개 동시에 선택하면 아래 창에 여러개 값이 한꺼번에 나와서 비교 가능함

![](https://gekdev.github.io/docs/database/oracle/example/drag.JPG)


---

## Connection Create

### [SYS]()

가장 큰 관리자 권한 (위에서 했음!)

### HR 

![](https://gekdev.github.io/docs/database/oracle/example/hr.JPG)

&#9656; Hose => localhost

&#9656; Service Name => XE로 해야지 오류가 나지않음

&#9656; User Name : hr

![](https://gekdev.github.io/docs/database/oracle/example/custom_onlyhr.JPG)

&#9656; hr 데이터베이스만 보게 하기

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

## Navicat Settings 

### Setting Fonts

![](https://gekdev.github.io/docs/database/oracle/example/setting_font.JPG)

---

## Reference Site

### Information

* [Practical Oracle SQL](https://www.apress.com/kr/book/9781484256169)

    &#9656; [github](https://github.com/Apress/practical-oracle-sql)