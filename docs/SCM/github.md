---
layout: default
title: Github
parent: SCM
nav_order: 1
---

# Github

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## What is Github?

## Command

cd WorkingDirectory 주소 //파일 위치 이동
2. git config
git config --global user.name "닉네임"
git config --global user.email "이메일"
위 두 개의 명령어를 통해서 닉네임과 이메일을 등록해줍니다.



1. git init

원하는 폴더에서 시작하는 깃 초기화 커맨드.<br> 
이 커맨드를 치고나면 .git 라는 이름의 숨김 폴더가 하나 생긴다. 이것을 저장소라고 하는데 깃은 이 폴더의 모든 변경 내용을 여기에 저장한다. 이 파일을 지우면 더 이상 깃으로 폴더의 변경사항을 추적할 수 없다.

2. git status

변경사항 중에서 “저장하고 싶은 부분만 선택해 임시로 저장”하는 개념<br>
추적하고 싶은 파일을 스테이지에 넣는 2가지 방법

```markdown
1. git add file.txt
  // 변경된 파일 직접선택

2. git add .
  // 폴더의 전체 변경 사항을 지정
```

3. git commit

깃이 폴더의 변경 내용을 저장하는 단위(스테이지 상태에 두어야만 커밋가능)

```markdown
1. git commit
  // 기본 에디터로 변경 내용을 기록할 수 있음

2. git commit -m "여기에 커밋메세지를 입력합니다."
  // 에디터 없이 기록가능
  
3. git commit -am "스태이징과 커밋을 한번에!"

4. git commit --amend
  // 커밋을 만들지 않고 이전 커밋에 변경사항을 추가할 경우(에디터)
```

4.git log

스테이징을 거쳐 커밋한 결과 보기
커밋 해쉬값, 작성자, 작성일자, 메세지순으로 확인가능

5. git show 

변경 내용이 반영되었는지 보기
삭제한 라인은 앞에 -를, 추가한 라인은 +로 표시한다.

6. git branch

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

7. head

위치를 좀 더 정확하게 보여주는 정보, 여러 개 가지로 뻗어있는 브랜치와 커밋 목록에서 현재 위치를 나타냄
체크아웃 하면서 브랜치를 이동할 때 마다 헤드는 수시로 변경

```markdown
git log 

commit 23427f8fb1baa80a5f0c9f974ba16dd0212edd69 (HEAD -> master)  //현재 작업 위치
commit d4b18ac8dc8f1e29a6082163b9329ffabd5bca96 (feature)
commit 18383c3d504208864ec73e7845d126a4824a43d6
```
6. git remote add origin “remote repository url”
git remote add origin “remote repository url” 명령어는 첫 커밋을 할 때만 사용하는 명령어이며 이후에는 사용하지 않아도 됩니다.

//fatal: remote origin already exists. 의 오류발생 시
git remote rm origin후 다시 생성

git remote -v // 연결상태를 확인한다.

7. git push -u origin master

git push -u origin master 명령어는 첫 커밋을 할때만 사용하는 명령어이며 이후에는 git push 명령어만 사용하면 됩니다.

1. git clone
가장 먼저 해야할 일은 git clone으로 원격 저장소에 있는 모든 파일들을 자신의 Working Directory로 가져오는 것입니다. git clone은 git init의 효과 까지 있습니다.

2. git pull
git pull은 다른 사람이 PR을 통해서 코드를 업데이트했거나, 아니면 Github를 통해서 commit했을 때(Github를 통해서도 간단한 commit을 할 수 있습니다) 그 내용을 클라이언트로 내려받는 명령어입니다. git pull origin master 하면 origin의 내용이 master로 복사됩니다.

git pull을 할 때는 깃허브의 유저이름과 비밀번호를 쳐야하는 경우가 많습니다. 매번 비밀번호를 치기 귀찮다면 git config --global credential.helper 'store --file 경로'하면 됩니다. 해당 경로에 비밀번호가 저장된 파일이 생성됩니다. 단, 파일로 저장되는만큼 보안에 취약하기 때문에 주의해야 합니다.

원격 저장소에서 팀원이 merge한 파일가져오기
원격 저장소에서 팀원이 merge한 파일을 가져올 때에는 git pull 명령어를 통해서 간단하게 가져올 수 있습니다. 충돌이(conflict) 일어나는 경우에는 충돌이 일어난 위치를 찾아서 해결(resolve)하고 다시 git pull로 가져오면 됩니다.

## 상황별 팁
https://jeonghwan-kim.github.io/dev/2020/02/10/git-usage.html#%EC%83%81%ED%99%A9%EB%B3%84-%ED%8C%81

## reference
https://opentutorials.org/module/4636 <br>
https://medium.com/webeveloper/%EA%B9%83%ED%97%88%EB%B8%8C-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95-github-tutorials-4a63f31bb6a5
