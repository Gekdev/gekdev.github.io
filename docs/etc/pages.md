---
layout: default
title: Tools
parent: ect
nav_order: 3
---

# 프로그래밍 사이트 모음
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Visual Studio Code(VSCode) 

### 단축키 및 팁 정리

! 자주 사용하는 중요한 단축키 리스트

** 검색 및 찾기 **

- 일치하는 텍스트 찾기   Ctrl +  F 

- 일치하는 텍스트 바꾸기   Ctrl +  R 

- 파일 찾기   Ctrl +  P 


** 줄 또는 블럭 이동하기 **

- 라인 또는 멀티라인 삭제하기   Ctrl +  Shift +  K 

- 라인 위 또는 아래로 이동하기   Alt +  방향키 


** 주석 관련 **

- 한 줄(Line)  주석 토글하기  Ctrl +  / 

   : 한 줄에도 적용가능하지만 여러 줄에도 사용이 가능합니다. (블록이 아닌 한줄 주석이 여러 줄에 적용됨)

- 멀티라인 주석 토글하기   Shift +  Alt +  A 

- 현재 줄 선택하기   Ctrl +  I   또는   Shift +  방향키 


** 탭 관련 **

- 탭 이동하기   Tab 

- 탭 반대 방향으로 이동하기   Shift +  Tab 

- 현재 탭 닫기  Ctrl +  W  

- 들여쓰기(Indent) 이동하기   Ctrl +  [   or   ] 

- 선택영역 접기 또는 펼치기   Ctrl +  Shift +  [   or   ] 

- 자동 줄바꿈(Word Wrap) 사용하기(토글)   Alt +  Z 

- 수정했던 라인으로 바로 이동하기   Alt +  좌우 방향키 

                  ; 수정된 상태는 그대로 두고 라인만 이동할 때 사용합니다

- 좌측 또는 우측 화면으로 포커스(Focus) 하기   Ctrl +  1   or   2 

                  ; 화면을 분할해서 사용하는 경우 매우 유용하며 좌우로 즉시 이동할 수 있습니다

- 선택 라인으로 이동하기   Ctrl +  G 

                  ; 100번째 줄로 이동할 경우 100을 입력합니다

- 설정 화면 열기   Ctrl  +  , 

​

​

​

1. Show All Commands (Ctrl + Shift + P)

VSCode에서 사용할 수 있는 모든 명령어를 입력할 수 있습니다.  


​

2. Keymaps Extensions 설치

VSCode에서는 keymaps Extension을 설치하여 본인이 기존에 사용하던 편집기의 단축키를 그대로 사용하거나 커스터마이징 할 수 있습니다.  



​

3. Process Explorer

VSCode를 사용하다보면 가끔 느려질 때가 있습니다. 원인을 모르고 한 없이 멈춰있는 VSCode를 보면 답답할 때가 있는데요. 이 때 사용할 수 있는 것이 바로 Process Explorer 입니다. 윈도우의 Task manager 처럼 어떤 프로세스가 메모리를 먹고 있는지 확인하고 kill할 수 있습니다. 


Process Explorer는 Ctrl + Shift + P > process explorer 를 입력하여 실행하면 됩니다. 단축키는 따로 정의되어 있지 않은데 자주 사용한다면 keyboard shortcuts를 설정(Ctrl + K 후 Ctrl + S)해서 사용하면 되겠죠?

 


​

4. Add Cursor Above / Below (Ctrl + Alt + 위/아래 화살표)

위아래로 커서를 늘려서 동시에 여러줄을 수정할 수 있도록 하는 기능입니다.  


 

5. Show running extensions

Ctrl + Shift + P > Show running extensions 를 입력하면 현재 VSCode에서 사용하고 있는 extension을 빠르게 확인해볼 수 있습니다. 


 

6. Quick Open (Ctrl + P or E)

파일명을 찾을 때 일일이 폴더를 열면서 찾으면 한 세월입니다. 파일명을 알고 있다면 Quick Open을 통해 파일을 바로 열 수 있습니다. 


 

7. Re Open (Ctrl + Shift + T)

방금 전에 닫은 파일을 다시 열고 싶을 때 사용하는 단축키입니다. 특히 파일이 많은 프로젝트를 개발할 때 실수로 파일을 닫았다가 다시 찾으려면 시간이 걸릴 때가 있습니다. 이 때 유용하게 쓸 수 있는 단축키 입니다. 의외로 이 단축키가 상당히 시간을 많이 세이브해줍니다.

 

이상 비주얼 스튜디오에서 자주 사용하는 단축키와 몇가지 팁을 정리해봤습니다. 제가 생각나는데로 항목을 추가하기 때문에 문단 순서가 다소 두서없이 나열되어 있는데요. 양해부탁드리며.. 앞으로도 계속 유용하다 싶은 기능이 있으면 이 포스트에 계속 추가해볼까 합니다. 마지막으로 Visual Studio Code 단축키 설정에 대한 자세한 내용은 VSCode 공식 문서를 참고해 보시길 바랍니다.

    