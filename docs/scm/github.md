---
layout: default
title: Github basic
parent: SCM
nav_order: 1
---
 
# Github
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Basic of Git

### What is Github?

Git이란 소스코드를 효과적으로 관리하기 위해 개발된 '분산형 버전 관리 시스템'입니다. 원래는 Linux 소스코드를 관리할 목적으로 개발 되었습니다.

Git에서는 소스 코드가 변경된 이력을 쉽게 확인할 수 있고, 특정 시점에 저장된 버전과 비교하거나 특정 시점으로 되돌아갈 수도 있습니다.

### Terms of Github

* Git repository

  1. Remote Repository : 함께 저장소 전용 서버에서 관리 
  2. Local Repository : 혼자 쓰는 개인 전용 저장소

* Commit

    변경을 기록하는 명령어, 최근 커밋부터 거슬러 올라가면 과거 변경 이력과 내용을 알 수 있다.

    버그 수정, 기능 추가 등 특별한 의미가 있는 업데이트를 작업 별로 구분해서 각각 커밋하면, 나중에 이력을 보고 특정 변경 내용을 찾기 쉽다.

    git에서 권장하는 메시지 형식 ...

    ```
    1번째 줄 : 커밋 내의 변경 내용을 요약
    2번째 줄 : 빈 칸
    3번째 줄 : 변경한 이유
    ```

* 저장되는 방식

    ![](https://gekdev.github.io/assets/images/git_route.png)


* Watch : 저장소에 변화가 있을때 알림
* Star : 좋아요
* Fork : 저장소 내 저장소에 가져오기
* Code : 현재 저장된 코드
* Issues : 다른 사람이 저장소에 있는 코드를 쓸때 문제가 생길경우 문제 제기
* Pull request(PR) : 남들이 코드를 직접 수정해서 올리는 곳
* Projects, Wiki, Pulse, Graph 등..

---

### Git Command

#### Setting Folder
{: .no_toc .fw_700}

* git remote

    원격 저장소를 관리할 수 있는 명령어, 주소를 등록한다. 

    git remote add origin _remote repository url_ <br>
    : 첫 커밋을 할 때만 사용하는 명령어이며 이후에는 사용하지 않아도 됨 

    ```markdown
    fatal: remote origin already exists. 의 오류발생 시
    git remote remove origin후 다시 생성
    git remote -v // 연결상태를 확인한다.
    ```

    ```markdown
    cd WorkingDirectory 주소 //파일 위치 이동
    ```

* git config

    닉네임과 이메일을 등록하기

    ```markdown
    git config --global user.name "닉네임"
    git config --global user.email "이메일"
    ```

* git init

> 원하는 폴더에서 시작하는 깃 초기화 커맨드.<br> 

이 커맨드를 치고나면 .git 라는 이름의 숨김 폴더가 하나 생긴다. 이것을 저장소라고 하는데 깃은 이 폴더의 모든 변경 내용을 여기에 저장한다. 이 파일을 지우면 더 이상 깃으로 폴더의 변경사항을 추적할 수 없다.

* git status 

> 파일들의 상태를 볼 수 있음

* git add

> 변경사항 중에서 “저장하고 싶은 부분만 선택해 임시로 저장”하는 개념, 스테이징(=인덱스에 올리는) 시키는 명령어 

#### 추적하고 싶은 파일을 스테이지에 넣는 2가지 방법
{: .no_toc }

```markdown
1. git add file.txt
  // 변경된 파일 직접선택

2. git add .
  // 폴더의 전체 변경 사항을 지정
```

* git commit

> 깃이 폴더의 변경 내용을 저장하는 단위(스테이지 상태에 두어야만 커밋가능) - 버전을 만드는것

```markdown
1. git commit
  // 기본 에디터로 변경 내용을 기록할 수 있음

2. git commit -m "여기에 커밋메세지를 입력합니다."
  // 에디터 없이 기록가능
  
3. git commit -am "스태이징과 커밋을 한번에!"
  // 한번이라도 커밋한 적이 있는 파일을 다시 커밋할때 사용

4. git commit --amend
  // 커밋을 만들지 않고 이전 커밋에 변경사항을 추가할 경우(에디터)
```

- git push -u origin master
git push -u origin master 명령어는 첫 커밋을 할때만 사용하는 명령어이며 이후에는 git push 명령어만 사용하면 됩니다.

* git log

> 스테이징을 거쳐 커밋한 결과 보기

커밋 해쉬값, 작성자, 작성일자, 메세지순으로 확인가능

* git show 
변경 내용이 반영되었는지 보기<br>
삭제한 라인은 앞에 -를, 추가한 라인은 +로 표시한다.

* git branch
브랜치 목록 확인
깃은 기본적으로 master라는 이름의 브랜치를 하나 가지고 있음<br>

새로운 브랜치 생성 : git branch 생성할브랜치명 기존브랜치명<br>
현재 브랜치는 앞에 별표(*)가 있는 master 브랜치, 이동은 git checkout 이동할브랜치명<br>
둘다 동시에(브랜치 만들면서 변경): git checkout -b 뉴브랜치명 <br>

브랜치 병합하기: 기준이 되는 master브랜치로 이동한 뒤, 머지
```markdown
git checkout master
git merge feature
```

- head
위치를 좀 더 정확하게 보여주는 정보, 여러 개 가지로 뻗어있는 브랜치와 커밋 목록에서 현재 위치를 나타냄
체크아웃 하면서 브랜치를 이동할 때 마다 헤드는 수시로 변경
```markdown
git log 

commit 23427f8fb1baa80a5f0c9f974ba16dd0212edd69 (HEAD -> master)  //현재 작업 위치
commit d4b18ac8dc8f1e29a6082163b9329ffabd5bca96 (feature)
commit 18383c3d504208864ec73e7845d126a4824a43d6
```



---

- git clone
git clone으로 원격 저장소에 있는 모든 파일들을 자신의 Working Directory로 가져오는 것<br> 
git clone은 git init의 효과 까지 있다

- git pull
git pull은 다른 사람이 PR을 통해서 코드를 업데이트했거나, 아니면 Github를 통해서 commit했을 때 그 내용을 클라이언트로 내려받는 명령어.<br> 
충돌이(conflict) 일어나는 경우에는 충돌이 일어난 위치를 찾아서 해결(resolve)하고 다시 git pull로 가져오면 됨<br>
git pull origin master 하면 origin의 내용이 master로 복사됨.<br> 

- git config --global credential.helper 'store --file 경로'
git pull을 할 때는 깃허브의 유저이름과 비밀번호를 쳐야하는 경우가 많은데 매번 비밀번호를 치기 귀찮을때 사용<br> 
해당 경로에 비밀번호가 저장된 파일이 생성됨. 단, 파일로 저장되는만큼 보안에 취약하기 때문에 주의.
```markdown
1. git config credential.helper store 
  // git directory에선 반영구적으로 인증 절차가 생략됩니다.(저장된 credential 정보를 이용해 인증 처리)
  
2. git config credential.helper cache
  // cash 사용 15분 동안 인증 절차를 요구하지 않음, git config credential.helper 'cache --timeout=3600'와같이 시간지정도 가능
  
3. git config credential.helper store --global
  // 모든 프로젝트에 적용

```

### 상황별 팁!
https://jeonghwan-kim.github.io/dev/2020/02/10/git-usage.html#%EC%83%81%ED%99%A9%EB%B3%84-%ED%8C%81

### reference
https://opentutorials.org/module/4636 <br>
https://www.hahwul.com/2018/08/git-credential-helper.html<br>
<br>
https://medium.com/webeveloper/%EA%B9%83%ED%97%88%EB%B8%8C-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95-github-tutorials-4a63f31bb6a5

