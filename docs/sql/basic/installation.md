---
layout: default
title: Installation
parent: Basic
grand_parent: SQL / Oracle
nav_order: 1
---

# Basic Installation
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Oracle Installation

### Oracle Express Edition Download & Install

1. Oracle Database 11gR2 Express Edition for Windows x64

    <span class="fs-2">
    [다운로드](https://www.oracle.com/database/technologies/xe-prior-releases.html){: .btn .btn-outline .mt-2}
    </span>

2. 압축 풀고 setup.exe 를 실행

3. 비밀번호 12345

4. 완료

![](https://gekdev.github.io/docs/sql/basic/example/or_ins_finish.JPG)

### Navicat Install

0. window defender, 보안프로그램 off

1. Navicat Premium 15.zip 압축풀기

2. navicat150_premium_en_x64.exe 실행

    &#8594; 설치한거 실행하면 안됨!

3. Navicat_Keygen_Patch_v6.1_By_DFoX.exe 실행
    
    설정(lang: English) > Patch > Key Generate

    (Error Message 무시 후 close)
    
4. Navicat에 Key 붙여넣기 

5. Navicat에서 생성된 코드 DFoX.exe의 Request Code에 붙여넣기

6. Activation Code > Own RSA Key 클릭

7. Generate에서 ddl 파일 클릭

8. 생성된 Activation Code를 다시 Navicat에 붙여넣기

9. 완료

<span class="fs-2">
[자세히 확인하기](https://gekdev.github.io/docs/sql/basic/example/navicatpatch순서.txt){: .btn .btn-outline .mt-2}
</span>

### Oracle DB Connection Checking

**제대로 설치 되었는지 SQL Command Line으로 연결 확인하는 것**

1. Window Menu > Run SQL Command Line

2. DB 접속

    ```sql
    SQL> conn sys/12345 as sysdba
        -- Connected 확인 : 접속성공
    ```
3. 현재 사용자 확인 

    ```sql
    SQL> show user 
        -- USER is "SYS"
    ```

4. 다른 사용자 접속 확인

    ```sql
    SQL> conn hr/hr
        -- hr 사용자는 기본적으로 lock 되어있음
    ```

5. 종료

    ```sql
    SQL> exit
    ```

오라클에서 제공되는 사용자 계정
{: .label .mt2}
<div class="code-example" markdown="1">
* SYS : 오라클 SUPER 사용자계정, 데이터베이스에서 발생하는 모든 문제들을 처리할 수 있는 권한을 가지고 있음

* SYSTEM : 오라클 데이터베이스를 유지보수 관리할 떄 사용하는 사용자 계정이며, SYS 사용자와의 차이점은 데이터베이스를 생성할 수 있는 권한이 없으면 불완전 복구를 할 수 없음

* HR : 처음 오라클을 사용하는 사용자의 실습을 위해 만들어놓은 교육용 계정
</div>
```html
sys와 system계정은 dba권한을 가짐 → 사용자를 생성하거나 삭제, 변경 등의 시스템 권한을 가지고 있음

오라클을 처음 설치하자마자 디폴트로 생성되고 활성화 되어있는 사용자 계정
```

---

## Navicat DB Connection

### New Database Connection

연결하는데에는 아래처럼 두가지 방법이 있음

1. **File &#8594; New Connection**

    ![](https://gekdev.github.io/docs/sql/basic/example/newconnection.jpg)

2. 왼쪽 끝에 있는 **Connection 아이콘**

    ![](https://gekdev.github.io/docs/sql/basic/example/connection_icon.jpg)

### New Connection Setting

1. General

    1. **Connection Name : sys** (서버이름, 아래 예제는 잘못 생성)

    2. **Hose : localhost**

    3. **Service Name : XE** 

    4. **User Name : sys** (최고 관리자)

    5. **Password : 12345**

    ![](https://gekdev.github.io/docs/sql/basic/example/newcon_oracle.JPG)

2. Advanced

    1. **Role : SYSDBA**

    2. **Test Connections &#8594; Connection Successful**

    ![](https://gekdev.github.io/docs/sql/basic/example/newcon_oracle2.JPG)

3. Databases

    **원하는 데이터 베이스를 체크해서 보고싶은 데이터베이스만 볼 수 있음**

    1. **Test Connections &#8594; Connection Successful**이 완료 되어야지 열림
    
    2. **HR, SYS 데이터베이스 선택** (나중에 SCOTT 계정 추가할 예정)

    ![](https://gekdev.github.io/docs/sql/basic/example/custom_dbase.JPG)

&#8594; 1,2,3 모두 다 설정 후 OK

### OCI Environment

1. **Tools &#8594; Options &#8594; Enviroment &#8594; OCI Environment &#8594; OCI Library** 열기

2. 파일을 c:Progrman Files/premium soft/..../instanceclient_10_?/oci.dll로 변경

![](https://gekdev.github.io/docs/sql/basic/example/dllfile.JPG)

### Setting Fonts

**d2 coding 폰트로 변경**

![](https://gekdev.github.io/docs/sql/basic/example/setting_font.JPG)

### Connected Database

**Connection되면 빨갛게 불이 들어옴**

![](https://gekdev.github.io/docs/sql/basic/example/connected.JPG)

#### Delete Connection

**마우스 오른쪽 눌러서 Close Connection**

![](https://gekdev.github.io/docs/sql/basic/example/connection_close.jpg)

---

## Change Oracle DB Environment

### Checking Environment Variables

1. Navicat 실행

2. SYS 관리자 선택 &#8594; New Query 생성

    ```sql
    select * from v$nls_parameters;
    ```

    &#8594; SQL Command Line에서도 볼 수 있지만, 테이블 형식은 보기 힘들어서 navicat에서 실행 후 확인

★ **NLS_DATE_FORMAT, NLS_TIMESTAMP_FORMAT을 변경할 예정**

**↓ 변경전 모습**

![](https://gekdev.github.io/docs/sql/basic/example/before_change.jpg)

### Session and System 

환경을 변경하는데에는 두가지 방법이 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**alter [session/system] ...**

* **session** : 현재 접속한 session에서만 변경되고 접속을 끊은 후 다시 접속하면 **변경전 환경으로 복귀됨**

* **system**  : database의 정보를 **영구적으로 변경**
    
    옵션 : **scope=[both/spfile]**

   &#9656; both : 바로 적용 or 재시작(오류가 날 가능성이 많음)

   &#9656; spfile : db를 종료후 재시작
</div>
```sql
-- session changing
SQL> alter session set nls_date_format = 'YYYY-MM-DD';
  -- ... NLS_DATE_FORMAT=DD-MON-RR 을 YYYY-MM-DD'로 변경
SQL> alter session set NLS_TIMESTAMP_FORMAT = 'YYYY-MM-DD HH:MI:SS';
SQL> exit

-- system changing
SQL> alter system set nls_date_format = 'YYYY-MM-DD' scope=spfile;
SQL> alter system set NLS_TIMESTAMP_FORMAT = 'YYYY-MM-DD HH:MI:SS' scope=spfile;
SQL> exit
```

### Changing Date Format

**영구적으로 변경해야 하니 system 변경 명령어로 사용해야 함**

1. SQL Command Line 실행

2. 데이터베이스 연결

    ```sql
    SQL> conn sys/12345 as sysdba
    ```

3. 변경 명령어 작성    

    ```sql
    SQL> alter system set nls_date_format = 'YYYY-MM-DD' scope=spfile;

    SQL> alter system set NLS_TIMESTAMP_FORMAT = 'YYYY-MM-DD HH:MI:SS' scope=spfile;
    ```

4. 종료

    ```sql
    SQL> exit
    ```

![](https://gekdev.github.io/docs/sql/basic/example/change_format.JPG)

### Restart Database

**데이터 포멧을 변경한 후에는 꼭 데이터베이스를 재시작 해줘야 함**

1. Stop database(app) 실행

2. Start database(app) 실행

**↓ 변경후 모습**

![](https://gekdev.github.io/docs/sql/basic/example/search_table.JPG)

---

## Checking and Changing HR 

### Check and Change HR Setting

**HR, SCOTT사용자 확인하기**

1. Window Menu > Run SQL Command Line

2. DB 접속

    **dn connection명령 : conn 사용자/비밀번호 as 사용자권한**
    
    &#8594; 오라클 명령어이기 때문에 navicat 에서는 사용불가
    
    ```sql
    SQL> conn sys/12345 as sysdba
        -- Connected 확인 : 접속성공
    ```

3. 현재 사용자 확인 

    &#9656; 시스템 권한을 가지고 있는 사용자 계정으로 접속해 있어야 함
    
    ```sql
    SQL> show user 
        -- USER is "SYS"
    ```

4. 다른 사용자접속

    ```sql
    SQL> conn hr/hr
        -- hr 사용자는 기본적으로 lock 되어있음
    SQL> conn scott
        -- scott 사용자는 없음
    ```

5. HR 잠금해제

    ```sql
    SQL> alter user hr account unlock;
    ```

6. HR 패스워드 지정

    ```sql
    alter user hr identified by 1234
    ```
    
### Create HR Connection in Navicat 

0. sys에서 hr 활성화

    ![](https://gekdev.github.io/docs/sql/basic/example/activate_hr.JPG)

1. General

    1. **Connection Name : hr** 

    2. **Host : localhost**

    3. **Service Name : XE** 

    4. **User Name : hr** 

    5. **Password : hr**

    ![](https://gekdev.github.io/docs/sql/basic/example/default_hr.jpg)

2. Advanced

    1. **Role : Default**

    2. **왼쪽 아래 text connections &#8594; Connection Successful**

    3. **OK**

    ![](https://gekdev.github.io/docs/sql/basic/example/newcon_oracle2.JPG)

3. Databases

    HR 데이터베이스만 보기
    
    ![](https://gekdev.github.io/docs/sql/basic/example/custom_onlyhr.JPG)

5. locked

    접속하려면 기본값으로 hr은 잠겨있음
    
    &#8594; 만약 위에서 잠금을 풀어줬다면 아래 HR권한만들기 하지 않아도 됨

    ![](https://gekdev.github.io/docs/sql/basic/example/locked.JPG)

    ★ **SYS에서 관리자 권한으로 풀어줘야 함**

### Checking HR By Navicat

1. oracle 사용자 조회, 환경 변수 변경 조회

    ```sql
    select * from dba_users; 
        -- dba_users 테이블에서 * 전체칼럼 가져오기
    select username from dba_users;
        -- 이렇게 칼럼을 선택해서 가져올 수 있음
    select username, ACCOUNT_STATUS, LOCK_DATE from dba_users;
        -- 여러칼럼 ,로 사용가능, 칼럼은 대소문자 구분하지 않음
    ```

    ![](https://gekdev.github.io/docs/sql/basic/example/check_set.jpg)
    
2. 사용자 권한 조회

    ```sql 
    select * from DBA_SYS_PRIVS; --전체 사용자의 권한을 조회
    select * from DBA_SYS_PRIVS where grantee = 'SYS' 
        -- sys 사용자만 권한 조회, 대소문자 구분함, row 값 검색해서 테이블에서 추출
    select * from DBA_ROLE_PRIVS where grantee = 'HR';
        -- HR 사용자 권한 조회
    ```

    **↓ SYS의 ADMIN_OPTION YES권한조회**
    ![](https://gekdev.github.io/docs/sql/basic/example/sys_yes.jpg)

    **↓ HR의 ADMIN_OPTION YES권한조회**
    ![](https://gekdev.github.io/docs/sql/basic/example/hr_yes.jpg)
    

3. HR 권한 만들기

    ```sql
    alter user hr account unlock; -- 사용자 잠금을 헤제하는 명령
    select username, ACCOUNT_STATUS, LOCK_DATE from dba_users where username = 'HR';
    alter user hr identified by hr; -- hr사용자의 비번을 hr로 변경하기
    select * from dba_users where username = 'HR';
    ```

    **↓ HR의 ACCOUNT_STATUS YES권한조회**
    ![](https://gekdev.github.io/docs/sql/basic/example/hr_role.jpg)
    
4. 사용자 소유의 table 목록 조회

    ```sql
    select * from tabs; -- 현재 접속한 session 즉, 사용자의 테이블 목록 조회
    ```

---

## Checking and Changing SCOTT 

### Checking Users By SQL Command Line

HR사용자 확인하면서 SCOTT 계정은 없는걸 확인했음

### Create SCOTT

1. SYS 권한으로 SCOTT 생성

    **identified = 비밀번호**
    
    ```sql
    select * from dba_users where username = 'SCOTT'; -- 존재하지 않음
    create user scott identified by tiger; -- scott 유저 생성하고 비번 tiger
    ```
    
    ![](https://gekdev.github.io/docs/sql/basic/example/hr_yes.jpg)
    
2. SCOTT에 권한 부여하기

    ```sql
    select * from dba_sys_privs where grantee ='SCOOT' -- 아무것도 나오지 않음
    select * from dba_role_privs where grantee = 'SCOOT' ;
    grant connect, resource to scott; -- 권한부여
    ```
    
3. 작업장소 지정하기

    ```sql
    alter user scott default tablespace users; -- users라는 작업장소
    alter user scott temporary tabblespace temp; -- temp라는 작업장소
    ```

    ![](https://gekdev.github.io/docs/sql/basic/example/scott.JPG)

4. 실습용 테이블 생성하기

    &#9656; 사용자를 scott으로 변경 후 작업 - 안나오면 scott에서 new query 하기

    &#9656; dept, emp, bonus, salgradeI (아래 명령들)

    ```sql
    CREATE TABLE DEPT
       (DEPTNO NUMBER(2) CONSTRAINT PK_DEPT PRIMARY KEY,
        DNAME VARCHAR2(14) ,
        LOC VARCHAR2(13) ) ;

    CREATE TABLE EMP  
       (EMPNO NUMBER(4) CONSTRAINT PK_EMP PRIMARY KEY,  
        ENAME VARCHAR2(10),  
        JOB VARCHAR2(9),  
        MGR NUMBER(4),  
        HIREDATE DATE,  
        SAL NUMBER(7,2),  
        COMM NUMBER(7,2),  
        DEPTNO NUMBER(2) CONSTRAINT FK_DEPTNO REFERENCES DEPT);

    INSERT INTO DEPT VALUES (10,'ACCOUNTING','NEW YORK');
    INSERT INTO DEPT VALUES (20,'RESEARCH','DALLAS');   
    INSERT INTO DEPT VALUES (30,'SALES','CHICAGO');  
    INSERT INTO DEPT VALUES (40,'OPERATIONS','BOSTON');

    INSERT INTO EMP VALUES
    (7369,'SMITH','CLERK',7902,to_date('17-12-1980','dd-mm-yyyy'),800,NULL,20);
    INSERT INTO EMP VALUES
    (7499,'ALLEN','SALESMAN',7698,to_date('20-2-1981','dd-mm-yyyy'),1600,300,30);
    INSERT INTO EMP VALUES
    (7521,'WARD','SALESMAN',7698,to_date('22-2-1981','dd-mm-yyyy'),1250,500,30);
    INSERT INTO EMP VALUES
    (7566,'JONES','MANAGER',7839,to_date('2-4-1981','dd-mm-yyyy'),2975,NULL,20);
    INSERT INTO EMP VALUES
    (7654,'MARTIN','SALESMAN',7698,to_date('28-9-1981','dd-mm-yyyy'),1250,1400,30);
    INSERT INTO EMP VALUES
    (7698,'BLAKE','MANAGER',7839,to_date('1-5-1981','dd-mm-yyyy'),2850,NULL,30);
    INSERT INTO EMP VALUES
    (7782,'CLARK','MANAGER',7839,to_date('9-6-1981','dd-mm-yyyy'),2450,NULL,10);
    INSERT INTO EMP VALUES
    (7788,'SCOTT','ANALYST',7566,to_date('13-7-1987','dd-mm-yyyy')-85,3000,NULL,20);
    INSERT INTO EMP VALUES
    (7839,'KING','PRESIDENT',NULL,to_date('17-11-1981','dd-mm-yyyy'),5000,NULL,10);
    INSERT INTO EMP VALUES
    (7844,'TURNER','SALESMAN',7698,to_date('8-9-1981','dd-mm-yyyy'),1500,0,30);
    INSERT INTO EMP VALUES
    (7876,'ADAMS','CLERK',7788,to_date('13-7-1987','dd-mm-yyyy')-51,1100,NULL,20);
    INSERT INTO EMP VALUES
    (7900,'JAMES','CLERK',7698,to_date('3-12-1981','dd-mm-yyyy'),950,NULL,30);
    INSERT INTO EMP VALUES
    (7902,'FORD','ANALYST',7566,to_date('3-12-1981','dd-mm-yyyy'),3000,NULL,20);
    INSERT INTO EMP VALUES
    (7934,'MILLER','CLERK',7782,to_date('23-1-1982','dd-mm-yyyy'),1300,NULL,10);

    CREATE TABLE BONUS
        (
        ENAME VARCHAR2(10)  ,
        JOB VARCHAR2(9)  ,
        SAL NUMBER,
        COMM NUMBER
        ) ;

    CREATE TABLE SALGRADE
          ( GRADE NUMBER,
        LOSAL NUMBER,
        HISAL NUMBER );

    INSERT INTO SALGRADE VALUES (1,700,1200);
    INSERT INTO SALGRADE VALUES (2,1201,1400);
    INSERT INTO SALGRADE VALUES (3,1401,2000);
    INSERT INTO SALGRADE VALUES (4,2001,3000);
    INSERT INTO SALGRADE VALUES (5,3001,9999);
    ```
