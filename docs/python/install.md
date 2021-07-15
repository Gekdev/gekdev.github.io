---
layout: default
title: Install
parent: Basic
grand_parent: Python
nav_order: 1
---

# Python Install
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Python Install

### Download 

1.  **아나콘다**


    &#9656; 오리지널 python 프로그램은 www.python.org에서 다운로드 할 수 있지만 오리지널 프로그램은 필요한 라이브러리를 일일이 사용자가 설치를 해야 함

    &#9656; 하지만 Anaconda를 설치하면 기본적으로 python.exe.와 자주 사용하는 유용한 패키지들을 자동으로 설치해 줌

    **phython v3.8버전 다운로드**

    <span class="fs-2">
    [download](http://www.anaconda.com/download){: .btn .btn-outline .mt-2}
    </span>
    
2. **설치 경로 : C:Anaconda3**

---

## Environment Setting

### Path setting

1. **window key + r : sysdm.cpl > (tab) 고급 > (b)환경변수설정**

2. **(system 리스트박스) path에 경로설정**

    1) C:\Anaconda3
    
    2) C:\Anaconda3\Scripts
    
    3) C:\Anaconda3\Library\bin

3. **설치확인**

    1) cmd 창에서 c:\python --version
    
    2) python 3.x.x 가 출력되면 정상적으로 설치완료
  
### Update

1. **anaconda prompt 를 관리자 권한으로 실행**

2. **conda update --all 또는 conda update conda**을 실행

3. **proceed Y 하기**

### Jupyter Notebook 

**홈폴더(root)를 설정**

1. **C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Anaconda3 (64-bit)의 'Jupyter Notebook (Anaconda3)'을 바탕화면에 복사**

2. **복사된 아이콘 속성 열기 (마우스 우클릭)**

3. **속성의 대상** : ~~ "%USERPROFILE%"의 %~%부분을 여러분의 작업폴더로 수정 
    
    &#9656; 예) ~~ "D:\lec\06.python"

---

## Jupyter Notebook 기본사용법

### Create New File

* 새 파일 생성 

    *  홈탭에서 오른쪽 상단의 New버튼을 클릭하면 Python3, TextFile, Floder, Terminal등의 옵션에서 Python3를 클릭하면 새파일이 생성됨

    *  현재탭에서 File>New Notebook>Python3 를 선택

* 이름 변경 : 생성된 파일의 이름을 변경하려면 제목라인의 제목을 클릭 한 후에 이름을 변경

![](https://gekdev.github.io/docs/python/images/00.파이썬설치 및 설정_01_새파일생성.PNG)

### Edit / Command Mode

* 편집모드 : 셀의 내용을 편집가능 (셀의 테두리가 초록색)

* 명령모드 : 편집중이 아닌 상태 또는 셀 자체를 조작하는 상태 (셀의 테두리가 파란색)

2. 명령모드에서 편집모드로 변경하려면 `Enter키 or 더블클릭`을, 반대의 경우 `Esc`키를 누른다.

#### Cell Type

* Code타입 : 파이썬의 코드를 실행할 수 있는 셀 
    
    기본적을 셀을 생성하면 Code타입으로 생성됨 
    
* Markdown타입 : 주석으로 셀의 내용을 작성할 수 있고 이 셀은 수식도 작성할 수 있음

![](https://gekdev.github.io/docs/python/images/00.파이썬설치 및 설정_02_셀타입.PNG)

### Run Cell

1. 실행하고자 하는 셀에 커서를 위치

2. `shift + enter` or `ctrl + enter` or `alt + enter`키를 누름
    
    * `shift + enter` :  마지막인 셀에서 실행할 경우는 실행후에 셀을 자동으로 추가
    
    * `ctrl + enter` :  실행만 함
    
    * `alt + enter` : 마지막 셀의 여부와 상관 없이 실행 후 셀을 자동으로 추가
     
3. 실행한 후에 셀 아래쪽에 실행결과가 출력

    &#9656; `In [ ]`과 `Out [ ]`에 몇 번째로 실행되었는지를 나타내는 숫자가 표시됨
    
    &#9656; 여러번 실행했을 경우에는 계속해서 자동으로 숫자가 증가됨

### Force Stop / Restart

![](https://gekdev.github.io/docs/python/images/00.파이썬설치 및 설정_03_강제중단.PNG)

**kernel 메뉴 : iPython(Jupyter Notebook의 옛날 이름) 대화창 아래에서 백그라운드와 비슷하게 실행되는 일종의 운영체제**

&#9656; kernel의 모든 메뉴는 기존에 작성된 코드를 삭제하지는 않음

* Interrupt : 실행중인 코드를 갈제로 중지. 에러메시지가 발생되면서 실행이 중지가 됨

* Restart : 실행중인 코드가 중지가 되며 재시작된다. 코드나 실행결과는 삭제가 되지 않음

* Restart & Clear All : 코드가 중지가 되며 실행결과는 삭제

* Restart & Run All : 재시작후에 모든 셀의 코드를 맨 처음부터 순차적으로 실행

* Reconnect : 인터넷 연결이 끊어졌을 경우 연결을 재시도함

* Shutdown : 커널을 종료 

    &#9656; 이 메뉴는 실행 결과는 삭제되지 않지만 완전 종료가 되는 상태로서 메모리에서 해제가 됨
 
    &#9656; Shutdown이 되었거나 인터넷 연결이 끊어 졌거나 기타 문제가 있다면 탬에 알림표시가 나타난다.

<img src="./images/00.파이썬설치 및 설정_04_Shutdown.png" width="600" height="500">

현재 실행중인 커널이 있는지 여부를 확인하는 방법
{: .label .mt-2}
<div class="code-example" markdown="1">
1. Home > Files 탭에서 `~.ipynb`파일의 아이콘이 초록색이면 실행중 회색이면 중단 또는 시작되지 않은 상태

2. Home > Running 탭에서 현재 실행중인 iPython과 터미널의 목록을 확인할 수 있음
</div>

### Create text file

1. Home > Files > New버튼

2. `Text File`을 생성

    `~.txt` or `~.py`파일 등을 만들 수 있음
    
&#9656; 이 파일들은 iPython에서 실행되지 않고 Terminal에서 실행시켜야 됨. 

&#9656; 하지만 파일을 읽는 것은 Jupyter Notebook에서 가능

### Terminal

1. Home > Files > New버튼

2. `Terminal`을 클릭 : 새로운 터미널

    윈도우의 `cmd창`과 같음
    
&#9656;  `~.py`파일을 실행시킬 수 있고 파일의 목록조회나 파일삭제등의 명령을 실행할 수 있음
 
&#9656; 이 터미널의 중지는 Running탭에서 중지시킬수 있음

### Rename or Delete File

![](https://gekdev.github.io/docs/python/images/00.파이썬설치 및 설정_05_파일이름변경 삭제.PNG)

<img src="./" width="600" height="300" />

### Jupyter Notebook Shortcut keys

단축키정보는 `(menu)Help > Keyboard Shortcuts` or `명령모드에서 H`를 눌러서 표시할 수 있음

메뉴에서 keyboard 아이콘을 클릭하면 단축키를 볼 수가 있음

1. 셀나누기   : `ctrl + shift + -`

2. 셀실행하기 : `ctrl + enter`, `shift + enter`,`alt + enter`

3. 불럭주석   : `ctrl + /`

![](https://gekdev.github.io/docs/python/images/00.파이썬설치 및 설정_06_단축키(1).PNG)

![](https://gekdev.github.io/docs/python/images/00.파이썬설치 및 설정_06_단축키(2).PNG)

---

## Representative Site

### Information

* [아나콘다(Anaconda) 설치 및 환경변수 설정](https://machine-geon.tistory.com/42)