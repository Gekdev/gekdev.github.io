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

### 초기화 (git init)
원하는 폴더에서 시작하는 깃 초기화 커맨드<br>
.git 라는 이름의 숨김 폴더가 하나 생긴다. 이것을 저장소라고 하는데 깃은 이 폴더의 모든 변경 내용을 여기에 저장한다. 이 파일을 지우면 더 이상 깃으로 폴더의 변경사항을 추적할 수 없다.

### 스테이징(git status)
변경사항 중에서 “저장하고 싶은 부분만 선택해 임시로 저장”하는 개념<br>

추적하고 싶은 파일을 스테이지에 넣기
<div class="code-example" markdown="1">
1. git add file.ext
  : 변경된 파일 직접선택

2. git add .
  : 폴더의 전체 변경 사항을 지정
</div>

스테이징 된 파일을 커밋 직전 상태로 변경
<div class="code-example" markdown="1">
git status

Changes to be committed:
  new file: file.txt
</div>

### 커밋(git commit)
깃이 폴더의 변경 내용을 저장하는 단위(스테이지 상태에 두어야만 커밋가능)
<div class="code-example" markdown="1">
1. git commit
  : 기본 에디터로 변경 내용을 기록할 수 있음

2. git commit -m "여기에 커밋메세지를 입력합니다."
  : 에디터 없이 기록가능
  
3. git commit -am "스태이징과 커밋을 한번에!"

4. git commit --amend
  : 커밋을 만들지 않고 이전 커밋에 변경사항을 추가할 경우(에디터)
</div>

### 로그(git log)
스테이징을 거쳐 커밋한 결과 보기

- 변경 내용이 반영되었는지 보려면 git show <br>
삭제한 라인은 앞에 -를 추가한 라인은 +로 표시한다.

### branch
지금하고 있는 작업과 성격이 다른 작업을 할 때 브랜치를 만든다

깃은 기본적으로 master라는 이름의 브랜치를 하나 가지고 있음<br>
브랜치 목록 확인 : git branch <br>

새로운 브랜치 생성 : git branch 생성할브랜치명 기존브랜치명<br>
현재 브랜치는 앞에 별표(*)가 있는 master 브랜치, 이동은 git checkout 이동할브랜치명<br>
둘다 동시에(브랜치 만들면서 변경): git checkout -b 뉴브랜치명 <br>

브랜치 병합하기: 기준이 되는 master브랜치로 이동한 뒤, 머지
<div class="code-example" markdown="1">
git checkout master
git merge feature
</div>




## reference
https://opentutorials.org/module/4636 <br>
