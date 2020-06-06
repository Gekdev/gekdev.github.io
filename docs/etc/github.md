---
layout: default
title: Github
parent: ect
nav_order: 1
---

# Github

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Software Configuration Management(SCM)
더 범위가 큰 구성 관리(CM)의 학문간 분야의 일부인, 소프트웨어의 변경사항을 추적하고 통제하는 작업 <br>
(“구성”은 일반적으로 시스템 관리자가 취한 변경사항을 커버하는 것으로 이해된다.)

CM은 시스템이나 제품의 성능과 기능 및 물리적 특성들을 요구사항(requirements), 설계(design), 기능적인 정보(operational information) 등과 함께 전 생애에서 지속적으로 관리하고 수립하는 것에 초점을 맞추고 있다. 관리 분야에서 제품의 성능이나 기능 및 물리적인 속성들을 요구사항, 설계, 운영 정보 등을 통하여 시스템의 일관성을 수립하고 유지하는 것이다.

### purpose of SCM
SCM은 Revision Control이나 Source control 및 Version Control과 같이 소프트웨어의 변경을 관리하고 작업을 추적하는 것이다. SCM은 버전관리(Revision Control)와 베이스라인 수립(establishment of baselines)를 포함하여 실행하는 것이다. SCM은 복잡한 시스템이 개발되면서 발생하는 다양한 변경사항들을 처리할 수 있도록 구성되어 있다. 이에 따라 최근 형상관리를 넘어 SCM이 각광받고 있으며, 기존의 Revision Control 등과 구분된다. 대표적인 SCM의 개념을 지원 툴은 JIRA 등이 있지만, 보통 SCM은 다양한 툴을 종합하여 구현한다.

### References
https://jangsunjin.tistory.com/236
https://en.wikipedia.org/wiki/Software_configuration_management
https://blog.naver.com/agapeuni/221057032543 (더 자세하게 알고싶다면)

## What is Github?

https://backlog.com/git-tutorial/kr/intro/intro1_2.html<br>
https://www.zerocho.com/category/Git
https://opentutorials.org/module/4636
https://nolboo.kim/blog/2013/10/06/github-for-beginner/



### Command

```markdown
cd WorkingDirectory 주소 //파일 위치 이동
```

- git config
```markdown
git config --global user.name "닉네임"
git config --global user.email "이메일"
```
위 두 개의 명령어를 통해서 닉네임과 이메일을 등록해줍니다.

- git init
원하는 폴더에서 시작하는 깃 초기화 커맨드.<br> 
이 커맨드를 치고나면 .git 라는 이름의 숨김 폴더가 하나 생긴다. 이것을 저장소라고 하는데 깃은 이 폴더의 모든 변경 내용을 여기에 저장한다. 이 파일을 지우면 더 이상 깃으로 폴더의 변경사항을 추적할 수 없다.

- git status
변경사항 중에서 “저장하고 싶은 부분만 선택해 임시로 저장”하는 개념<br>
추적하고 싶은 파일을 스테이지에 넣는 2가지 방법
```markdown
1. git add file.txt
  // 변경된 파일 직접선택

2. git add .
  // 폴더의 전체 변경 사항을 지정
```

- git commit
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

- git log
스테이징을 거쳐 커밋한 결과 보기<br>
커밋 해쉬값, 작성자, 작성일자, 메세지순으로 확인가능

- git show 
변경 내용이 반영되었는지 보기<br>
삭제한 라인은 앞에 -를, 추가한 라인은 +로 표시한다.

- git branch
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
- git remote add origin “remote repository url”
첫 커밋을 할 때만 사용하는 명령어이며 이후에는 사용하지 않아도 됨 <br>
```markdown
fatal: remote origin already exists. 의 오류발생 시
git remote rm origin후 다시 생성
git remote -v // 연결상태를 확인한다.
```

- git push -u origin master
git push -u origin master 명령어는 첫 커밋을 할때만 사용하는 명령어이며 이후에는 git push 명령어만 사용하면 됩니다.

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

## Github blog
아래 블로그들을 참고해서 구축했습니다.

https://devmjun.github.io/archive/CreatGithubBlog <br>
https://honbabzone.com/jekyll/start-gitHubBlog/
