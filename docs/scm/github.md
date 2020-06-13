---
layout: default
title: Github
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

Git이란 소스코드를 효과적으로 관리하기 위해 개발된 **분산형 버전 관리 시스템** 입니다. 원래는 Linux 소스코드를 관리할 목적으로 개발 되었습니다.

Git에서는 소스 코드가 변경된 이력을 쉽게 확인할 수 있고, 특정 시점에 저장된 버전과 비교하거나 특정 시점으로 되돌아갈 수도 있습니다.

### Basic Terms of Github

* Git Repository

    **프로젝트가 거주(live)할 수 있는 디렉토리나 저장 공간**

    1. Remote Repository : 함께 저장소 전용 서버에서 관리 
    2. Local Repository : 혼자 쓰는 개인 전용 저장소

* Commit 
    
    **변경을 기록하는 명령어**

    &#9656; 최근 커밋부터 거슬러 올라가면 과거 변경 이력과 내용을 알 수 있다.

    &#9656; 버그 수정, 기능 추가 등 특별한 의미가 있는 업데이트를 작업 별로 구분해서 각각 커밋하면, 나중에 이력을 보고 특정 변경 내용을 찾기 쉽다.


    &#42; git에서 권장하는 메시지 형식
    {: .label .label-green .mt-3 }

    ```
    1번째 줄 : 커밋 내의 변경 내용을 요약
    2번째 줄 : 빈 칸
    3번째 줄 : 변경한 이유
    ```
* Watch : 저장소에 변화가 있을때 알림
* Star : 좋아요
* Fork : 저장소 내 저장소에 가져오기
* Code : 현재 저장된 코드
* Issues : 다른 사람이 저장소에 있는 코드를 쓸때 문제가 생길경우 문제 제기
* Pull request(PR) : 남들이 코드를 직접 수정해서 올리는 곳
* Data Transport

    ![](https://gekdev.github.io/assets/images/git_route.png)

---

## Git Basic Command

### Setting Folder

* git remote
    
    **원격 저장소를 관리할 수 있는 명령어, 주소를 등록한다.**

    ```markdown
    git remote add origin _remote repository url_
      // 첫 커밋을 할 때만 사용하는 명령어이며 이후에는 사용하지 않아도 됨 
    ```
    
    !오류 fatal: remote origin already exists.
    {: .label .label-red .mt-3 }
    
    ```markdown
    git remote remove origin후 다시 생성
    git remote -v // 연결상태를 확인한다.
    ```

* git config

    **닉네임과 이메일을 등록하기**
    
    ```markdown
    git config --global user.name "닉네임"
    git config --global user.email "이메일"
    ```

* git init

    **원하는 폴더에서 시작하는 깃 초기화 커맨드**

    이 커맨드를 치고나면 .git 라는 이름의 숨김 폴더가 하나 생긴다. 이것을 저장소라고 하는데 깃은 이 폴더의 모든 변경 내용을 여기에 저장한다. 이 파일을 지우면 더 이상 깃으로 폴더의 변경사항을 추적할 수 없다.

### Upload, download

* git status

    **파일들의 상태를 보기**

* git add
    
    **스테이징 시키는(=인덱스에 올리는) 명령어**
    
    변경사항 중에서 “저장하고 싶은 부분만 선택해 임시로 저장”하는 개념

    ```markdown    
    1. git add file.txt
      // 변경된 파일 직접선택
 
    2. git add .
      // 폴더의 전체 변경 사항을 지정
    ```

* git commit

    **깃이 폴더의 변경 내용을 저장하는 단위** 
    
    &#9656; 스테이지 상태에 두어야만 커밋가능
    
    &#9656; 버전을 만드는 단위 따라서 최대한 잘게 commit 하는게 좋다

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

* git push

    **원격 저장소에 commit을 저장**

    ```markdown
    git push -u origin master
      // 첫 커밋을 할때만 사용하는 명령어 이후에는 그냥 git push만 사용 
    ```

* git pull

    **다른 사람이 PR을 통해서 코드를 업데이트했거나, 아니면 Github를 통해서 commit했을 때 그 내용을 클라이언트로 내려받는것**
    
    ```markdown
    git pull origin master
      // origin의 내용이 master로 복사
    ```
    
    비밀번호를 계속 치기 귀찮을 때
    {: .label .mt-3 }
    
    ```markdown
    1. git config --global credential.helper 'store --file 경로
    
    2. git config credential.helper store 
      // git directory에선 반영구적으로 인증 절차가 생략됩니다.(저장된 credential 정보를 이용해 인증 처리)

    3. git config credential.helper cache
      // cash 사용 15분 동안 인증 절차를 요구하지 않음, 
      // git config credential.helper 'cache --timeout=3600'와같이 시간 지정도 가능

    4. git config credential.helper store --global
      // 모든 프로젝트에 적용
    ```
    
    충돌이(conflict) 일어나는 경우
    {: .label .label-red .mt-3 }
    <div class="code-example" markdown="1">
    충돌이 일어난 위치를 찾아서 해결(resolve)하고 다시 git pull로 가져오면 됨
    </div>    

* git clone

    **git clone으로 원격 저장소에 있는 모든 파일들을 자신의 Working Directory로 가져오는 것**
    
    git clone은 git init의 효과 까지 있다
    
    ```markdown
    git clone 저장소주소
    ```

### Checking

* git diff

    **수정된 파일에서 어떤 부분이 달라졌는지 확인**
    
    &#9656; 보기 불편해서 Git GUI나 Git을 지원하는 IDE를 사용
    
    &#9656; 나가기 q
    
    한글 파일이 깨진경우
    {: .label .label-red .mt-3 }
    <div class="code-example" markdown="1">
    파일을 메모장으로 열어(혹은 다른 에디터를 열어) 다른 이름으로 저장을 누르고 
    ANSI나 EUC-KR 대신 UTF-8 인코딩으로 저장
    </div>    
    
* Untracked와 Tracked의 3단계
    ![](https://gekdev.github.io/assets/images/tracked.png)

* git checkout
    
    **Modified 상태의 파일을 Unmodified로 되돌리기** 
    
    대부분 수정을 잘못해서 파일을 원상태로 되돌리고 싶을 때 사용
    
    ```markdown
    git checkout git.html(파일명)
    ```
    
    &#9656; git2.23버젼부터 `git restore`도 가능!

* git reset
    1. add해서 Staged된 상태의 파일을 Modified 상태로 만들기 (이전 commit으로 직접 되돌아가기)
    
        ```markdown
         git reset git.html(파일명)
        ```
    
    2. commit한후 되돌리기 (3가지 옵션)

        ```markdown
        1. --soft
          // commit 후의 Unmodifed에서 commit 직전의 Staged 상태로

        2. --mixed
          // Unmodified에서 commit 전의 Modified 상태로 (default)

        3. --hard
          // Unmodified에서 commit 전의 Unmodified (다 날리기)
          
        ---
        git reset HEAD~1
          // HEAD가 현재 commit의 위치, ~1은 commit 1개 전으로 되돌아가라는 뜻
        ```

* git revert
    
    **이전 commit 내용을 새 commit으로 만들어서 저장**
    
    git revert는 commit을 이미 push해서 서버에 저장해버린 경우 자주 사용
    
    ```markdown
    git revert HEAD 
      // 현재 HEAD를 취소하고 이전 HEAD로 돌아간다는 뜻
      // 화면이 바뀌고 commit 메세지를 바꿀 수 있음, 바꾸고 :wq
    ```

* git log

    **스테이징을 거쳐 커밋한 결과 보기**

    &#9656; 커밋 해쉬값, 작성자, 작성일자, 메세지순으로 확인가능
    
    &#9656; 나가기 q
    
    ```markdown
    git log 

    commit 23427f8fb1baa80a5f0c9f974ba16dd0212edd69 (HEAD -> master)  //현재 작업 위치
    commit d4b18ac8dc8f1e29a6082163b9329ffabd5bca96 (feature)
    commit 18383c3d504208864ec73e7845d126a4824a43d6
    ```

* git show

    **변경 내용이 반영되었는지 보기**
    
    &#9656; 삭제한 라인은 앞에 -를, 추가한 라인은 +로 표시한다.

---

## Git Branch

### What is Branch?

**여러 개발자들이 동시에 다양한 작업을 할 수 있게 만들어 주는 기능**

또 실제 환경에선 **master 브랜치에 배포 준비가 된 commit들만 남기는 경우**가 많기 때문에 사용한다 

### Branch Command

* git branch

    **브랜치 목록 확인과 생성**
    
    &#9656; 깃은 기본적으로 master라는 이름의 브랜치를 하나 가지고 있음
    
    &#9656; 현재 브랜치는 앞에 별표(*)가 있는 master 브랜치

    ```markdown
    git branch 생성할브랜치명 기존브랜치명
      // 새로운 브랜치 생성
    ```
    
* git checkout 
    
    **브랜치 옮기기**
    
    ```markdown
    git checkout 이동할브랜치명
    
    git checkout -b 뉴브랜치명
      // 브랜치 만들면서 변경
    ```
    
    &#9656; git2.23버젼부터 `git switch`도 가능!
    
* git merge

    **브랜치 병합하기 1** 
    
    기준이 되는 **master브랜치로 이동**한 뒤, 머지해야함
    {: .text-red-300}
    
    &#8594; git branch 명령어로 head가 어디있는지 항상 확인!
    
    ```markdown
    git checkout master
    git merge 브랜치명(feature)
    ```
    &#8594; merge 결과에 Fast-forward 라고 적혀있으면 OK!

    오류! conflict 발생시
    {: .label .label-red .mt-3 }
    <div class="code-example" markdown="1">
    1. 일단 충돌이 되는 파일을 해결
    2. git add .로 staged 상태로 만듦 
    3. 그 후에 commit을 하면 됨
    </div>
    
* git rebase

    **브랜치 병합하기 2**
    
    기준이 되는 **master브랜치로 이동**한 뒤, 리베이스 해야함
    {: .text-red-300}
    
    ```markdown
     git rebase 브랜치명
    ```
    오류! conflict 발생시
    {: .label .label-red .mt-3 }
    <div class="code-example" markdown="1">
    1. 일단 충돌이 되는 파일을 해결
    2. git add .로 staged 상태로 만듦 
    3. 그 후에 git rebase --continue로 중단된 rebase를 이어감
    </div>
    
    merge와 rebase는 취향에 따라 사용하시면 됩니다. 깔끔한 log를 원하면 rebase를 하고, 직관적으로 간단하게 하고 싶으면 merge를 하면 됩니다.
    

## 상황별 팁

### 기타 명령어

* cherry-pick

체리는 commit을 의미
다른 브랜치의 commit 중 하나를 쏙 골라서 현재 브랜치에 넣는 겁니다. 
merge나 rebase는 다른 브랜치를 통째로 가져오는 데 비해, 다른 브랜치의 원하는 commit 한 개만 가져올 수 있습니다.

기존 master 브랜치에 새로 바꾼 CSS 작업만 가져오고 싶습니다.

```markdown
git cherry-pick [commit명] 
  // commit명은 Git 자체에서 붙여주는 고유값
```

* git tag

**commit에 태그를 붙이는 기능**

&#8594; 태그란 꼬리표로 commit에게 별명을 지어주는 것(commit명이 너무 길기때문에)

&#9656; 주로 새로운 버전이 나왔거나 특정 기능을 가진 commit에 tag를 붙여줍니다. 

```markdown
git tag -a v1.0.0 
  // 태그생성, 나중에 git cherry-pick v1.0.0으로 선택가능
  
git tag -d 태그명
  // 태그 삭제
```

* git fetch 

**서버의 변경점을 별개의 브랜치로 만드는 것** 

&#9656; git fetch 명령어만 실행하면 merge하지 않고 FETCH_HEAD라는 별개의 브랜치에서 변경점을 확인할 수 있다

&#9656; git pull은 git fetch와 git merge를 동시에 실행 시키는것임

* git shortlog

**git log에서 commit 메시지만 추려서 보여줌**

~하지만 최고의 방법은 GUI를 사용하는 것~

* git stash, git unstash

**현재 변경점을 저장**

&#9656; commit과는 다른 의미의 저장

&#9656; 한 브랜치에서 작업을 하다가 잠깐 다른 브랜치에서 작업할 일이 생겼을 때에 주로 사용

&#9656; 현재까지의 변경사항을 저장하고 다른 브랜치로 넘어갔다가, 다시 돌아왔을 때 복구할 수 있다

git stash 명령어를 사용하면 현재 변경사항들이 저장되고, git status 내역이 비워집니다. stash한 것들은 git stash list하면 확인할 수 있습니다.

이제 다른 작업을 하고 돌아와서 저장했던 stash를 복구해보겠습니다. 간단히 git stash apply하면 최근에 저장한 stash가 복구됩니다.

https://jeonghwan-kim.github.io/dev/2020/02/10/git-usage.html#%EC%83%81%ED%99%A9%EB%B3%84-%ED%8C%81

## Reference
[](https://opentutorials.org/module/4636) <br>
https://www.hahwul.com/2018/08/git-credential-helper.html<br>
<br>
https://medium.com/webeveloper/%EA%B9%83%ED%97%88%EB%B8%8C-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95-github-tutorials-4a63f31bb6a5

