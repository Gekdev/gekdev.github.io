---
layout: default
title: IT Terms
parent: ect
nav_order: 1
---

# IT Terms 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

[hopeless](https://brunch.co.kr/@hopeless/8)에서 가져왔습니다. 

## IT영단어 정리
{: .no_toc}

### 명명법
클래스명은 명사, 메서드는 동사, 기능은 명사 + 동사

### 표기법
&#9656; **CamelCase**

    문자의 표현을 낙타 등 처럼 했다고 해서 정해진 이름

    주로 객체지향 프로그램에서 사용함

&#9656; **snake_case**

    언더라인(_) 으로 단어를 구분하는 명명법

    C, SQL등에서 사용

&#9656; **헝가리안표기법**

    변수에 정보를 추가해서 명명하는 방법

    g_ / m_ / s_

    글로벌 / 멤버 / 스태틱

### 반대되는 단어
* **add / remove**

    추가, 삭제

    리스트 등에 값을 추가, 삭제할 때 사용.

    꼬리에 추가시에는 append, 선두에 추가시에는 prepend를 사용

* **top / last**

    선두, 말미

* **head / tail**

    머리, 꼬리

    자료구조 등에서 자료의 첫번째, 마지막 의미로 사용

* **or under / and over**

    이하, 이상

    greater then, not less than

* **foreground / background**

    전경, 배경

    앞 단, 뒷 단

* **push / pop**

    스택 등에 넣고, 뺄 때

* **push / pull**

    git 에서 넣고, 뺄 때

* **enqueue / dequeue**

    큐에 넣고, 뺄 때

* **parent / child / children / self**

    부모, 자식, 자식들, 자신

* **open / close**

    파일이나 소켓을 열다, 닫다

* **input / output**

    입력, 출력

    기기의 입출력

* **import / export**

    설정 등을 가져오기, 내보내기

* **set / unset**

    설정, 해제

* **suspend / resume**

    쉬다, 재개

* **enable / disable**

    유효하게 함, 무효하게 함

* **activate / deactivate**

    활성화, 비활성화

* **show / hide**

    표시, 숨김

* **valid / invalid**

    유효, 무효

* **host / guest**

    손님을 받는 쪽이 호스트

    손님은 게스트

* **server / client **

    서비스를 제공하는 쪽이 서버

    의뢰하는 쪽이 클라이언트

* **provider / user**

    제공자, 사용자

* **resume / pause**

    재개, 일시정지

* **create / destroy**

    생성, 파괴

### 비슷한 의미의 단어, 뉘앙스
* **config / setting / preference**

    구성, 설정, 환경설정

* **initialize / init / setup**

    초기화, 셋업

* **stop / end / finish**

    재시작할 가능성이 있으면 stop

    재시작할 가능성이 없으면 end

    완료 했다는 의미는 finish

* **stop / suspend / pause**

    움직이는 것을 멈추는 것이 stop

    일시정지는 suspend

    일단 움직임을 멈추는 것을 pause, 언제든 다시 재개할 수 있음

* **stop / quit / exit**

    현재 상태에서 탈출하는 것이 quit

    출구로 나가는 것이 exit

* **changed / modified / revised**

    전면적인 변경이 changed

    수정이나 개선 modified

    개정 revised

* **find / search**

    찾아질 것을 기대하는 것이 find

    찾아보는 것이 search

* **toXXX / parseXXX / convertXXX**

    XXX로 변환

* **tryParseXXX**

    XXX로 변환을 시도

* **fromXXX**

    XXX로 부터 변환

    메서드명은 동사가 원칙이나 to나 from은 예외

* **clear / delete**

    예를 들어 파일의 내용만 지우는 것이 clear

    파일을 통째로 지우는 것을 delete

* **create / make / generate**

    창조하는 것이 create

    무언가를 보고 만들어 내는 것이 make

    무언가를 변환하여 생성하는 것이 generate

    인스턴스를 생성할 때에는 create가 일반적

* **parameter / argument**

    메서드에 정의되어 있는 것이 parameter

    메서드에 전달된 값이 argument

    인수, 매개변수라고도 한다

* **property / attribute**

    둘 다 속성이란 뜻

    단, 분야나 제품에 따라 사용이 나눠지기도 함

    객체 지향의 클래스의 성질을 나타내는 것이 property

    HTML의 태그의 속성은 attribute

* **number / numeric**

    숫자, 번호를 나타내는 것이 number

    숫자 중 10진수를 numeric

    numeric이 좀 더 수학적인 느낌

* **sum / total**

    금액의 합계, 모두 더한 것이 sum

    합계, 전체의, 모두가 total

* **limits / bounds / range**

    경계, 제한범위, 제한구역이 limits. 제한.

    한계 내, 한계선이 bounds. 좀더 수학적인 느낌. 경계.

    값이 변경하는 폭, 상한과 하한이 결정되는 범위가 range, 범위.

* **top / peak / spike**

    최상, 선두가 top.

    쌓여진 것 중에서 가장 위가 peak.

    꺾인선 그래프 등의 뾰족한 것이 spike.

    헤깔리면 그냥 top 사용하면 됨

* **exclude / ignore**

    배제하다, 빼내다, 고려하지 않는다가 exclude.

    무시하다, 신경쓰이지 않는 느낌이 ignore

* **state / status**

    상태 그 자체의 의미. state

    게임 캐릭터의 status, 독에 걸린 state

* **letter / character**

    a나 b와 같은 문자 자체 letter.

    알파벳 전체, 문자 전체를 가리키는 경우 character

* **title / caption**

    책이나 기사의 제목, 표제가 title.

    짧은 설명문, 페이지의 제목이 caption.

* **issue / problem**

    문제, 논점, 쟁점, 논해야 하는 것이 issue

    곤란해 질 만한 문제로, 해결이 필요한 것이 problem

* **individual / personal / private**

    많은 사람들에 대해 개인일 경우 individual. 개별.

    사람 수에 관계없이, 다른 누구도 아닌, 개인을 나타낼 때 personal. 개인적인.

    public(공적)에 반대인 private(사적).

    종업원 한명한명을 가리키는 개인은 individual을 사용하면 됨

* **just / only**

    무언가를 기준으로 딱, 그것을 가리킬 때 just

    절대적인 의미로, 유일한 것을 가리킬 때 only.

* **within**

    시간, 거리, 범위를 의미하는 이내.

    within 3 sec = 3초 이내.

* **fix**

    수정, 수리, 고정, 결정.

* **apply**

    설정 등을 적용하다

* **flush**

    쌓인 데이터나 로그를 클리어한다.

    밀어 내보낸다. 모든것을 토해낸다.

* **validate / verify**

    요구를 만족하는가, 올바른가 확인하는 것이 validate

    공정의 일부로 포함 된 체크가 verify

    CD/DVD를 굽고 나면 verify를 함.

### 자주 나오는 단어
* **syntax / statement / expression / operator / signature**

    syntax는 구문.

    statement는 문장. if문, for문, 함수 호출문 등.

    expression은 평가식

    operator는 연사자

    signature는 메서드명, 파라미터, 리턴값의 타입을 표현하는 것.

* **inheritance**

    상속

* **delimiter / separator**

    구분자 문자

* **log**

    기록, 로그를 얻다.

    명사와 동사가 같음

* **stack**

    쌓기, 쌓다.

    명사와 동사가 같음

* **token**

    토큰, 표시, 증거.

    분해되지 않는 최소 단위.

    네트워크의 경우에는 송신권을 주고 받는 데이터 등.

* **optimize**

    최적화하다

* **normalize**

    정규화하다

* **cheatsheet**

    사용법을 1페이지로 정리한 것

* **usage**

    사용방법

* **unknown**

    미지의, 정체불명의

* **misc / miscellaneous**

    다양한, 다방면의

* **brief**

    개요, 요약하다

* **features**

    특징, 기능.

    대체로 복수형으로 사용

* **via**

    ~에 의해, ~를 경유하여

* **required**

    필수의

### 값 관련
* **initial value / initialized value**

    초기치, 초기값

* **default value**

    기본 값

* **original value**

    원래의 값, 변경전의 값

* **current value**

    현재 값

* **parameter / argument**

    인수

* **return value / returned value**

    리턴 값

* **variable / var**

    변수  

* **literal**

    리터럴. 직접 기술한 값.

    변수의 반대의 의미.

    int x = 10;

    String str = "abc";

    10을 정수 리터럴, "abc"를 문자열 리터럴

* **constant / const**

    상수

* **primitive data type**

    프리미티브 타입. 기본형

    int, double, long 등 값을 가지는 타입

* **null / nil**

    존재하지 않는 것

* **void**

    빈것.

    null과 비슷한 의미

* **prefix / suffix**

    접두어, 접미어

    disconnect 의 dis 나 restart의 re 가 접두어

    player의 er나 nullable의 able 이 접미어 

* **release**

    출시

### 수치표현
* **binary number**

    2진수

    선두에 0b를 붙이는 표현. 0b10은 십진수 2

* **octal number**

    8진수

    선두에 0을 붙임. 010은 8

* **decimal number**

    10진수

* **hexadecimal number**

    16진수

    선두에 0x를 붙임. 0x10 은 16

* **even / odd**

    짝수, 홀수

### 진위 값
* **true / false**

    참, 거짓

* **isXXX / hasXXX / canXXX**

    상태를 측정하는 경우.

    isNull, isNumber, hasConnection, canSave 등

* **exists**

    파일 등이 물리적으로 존재하는지 아닌지.

* **contains**

    리스트 등에 포함되어 있는지 아닌지

* **equals**

    같은지 아닌지

### 도형
* **point / x / y / offset**

    좌표, x축, y축, 상대적인 위치

* **size / width / height**

    크기, 폭(가로), 높이

* **top / middle / bottom**

    left / center / right

* **front / middle / back**

    front / center / side / rear

* **fill**

    색칠하다

* **depth**

    심도, 깊이