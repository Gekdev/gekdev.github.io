---
layout: default
title: Session
parent: Implicit Object
grand_parent : JSP
nav_order: 3
---

# Session Implicit Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Session

### 세션 사용하기 

웹 브라우저에 정보를 보관할 때 쿠키를 사용한다면 세션은 웹서버(웹 컨테이너)에 정보를 보관할 때 사용

세션은 오직 웹 서버에만 생성이 됨

웹 컨테이너는 기본적으로 한 웹브라우저마다 한 세션을 생성함

웹 브라우저마다 세션이 따로 존재하기 때문에 세션은 웹 브라우저와 관련된 정보를 저장하기에 사용

즉, 쿠키가 클라이언트 측의 데이터 저장소라면 세션은 서버측의 저장소

세션을 생성하면 session 기본객체를 이용해 세션을 사용할 수 있게 됨

JSP에셔는 세션을 생성하려면 page디렉티브의 session 속성을 true(기본값)으로 지정하면 됨

### Session 객체

session 객체는 request객체와 마찬가지로 속성을 제공하고 setAttribute(), getAttrubute() 메서드를 사용해 session의 속성값을 저장하거나 읽을 수 있음
다만 session객체는 세션만의 고유 정보를 제어할 수 있는 메서드가 추가로 제공됨

| getId() | 세션ID(세션마다 고유의 ID값)를 리턴 |
| getCreationTime() | 세션이 생성된 시간을 리턴 |
| getLastAccessedTime() | 웹 브라우저가 마지막에 접근한 시간을 리턴 |

### session 객체의 속성

한번 생성된 세션은 지정한 유효시간동안 유지가 되기 때문에 웹 애플리케이션을 실행하는 동안 지속적으로 사용해야 하는 데이터의 저장소로 세션을 사용

request객체가 하나의 요청을 처리하는데 사용된다면 session 객체는 웹 브라우저의 여러 요청을 처리하는 JSP페이지에서 공유됨

로그인한 회원정보 등 웹브라우저와 일대일로 관련 값을 저장할 때 에는 쿠키보다는 세션을 사용하는게 좋음

### Why use Session instead of Cookie?

1. 쿠키 대신 세션을 사용하는 가장 큰 이유는 세션이 쿠키보다 보안에서 더 안정적이라는 점에 있음
	
	쿠키의 이름이나 값은 네트워크를 통해 전달되기 때문에 http 프로토콜을 사용하는 경우 중간에 쿠키값을 해킹할 수 있지만
	
	세션의 값은 오직 웹 서버에만 저장되기 때문에 중요한 자료를 보관할 때 알맞은 저장소가 됨

2. 웹 브라우저가 쿠키를 지원하지 않을 경우 또는 강제적으로 쿠키를 사용하지 못하게 할 경우 세션은 쿠키 설정여부와 상관없이 사용할 수 있음
 
### 세션 종료

**세션을 유지할 필요가 없다면 session.invalidate() 메서드를 사용해서 세션을 종료**

세션을 종료하면 사용중인 session기본객체를 삭제하고 session객체에 저장되었던 속성정보도 삭제가 됨

### 세션유효시간

세션은 최종 접근시간 정보를 가지고 있는데 session 객체를 사용할 때 마다 최종 접근시간이 갱신됨

세션은 마지막 접근 이후, 일정시간 내에 다시 세션에 접근하지 않을 경우에는 자동으로 세션을 종료하는 기능을 가지고 있음

세션 유효시간 설정

* web.xml에 <session-config> 태그를 사용해 분단위로 지정

* setMaxInactiveInterval() 메서드를 사용해 초단위로 지정

### 세션 생성

HttpSession(session 객체)를 생성하는 또 다른 방법은 request.getSession() 메서드를 이용하는 것

이 메서드는 현재 요청과 관련된 session 객체를 리턴, session이 존재하면 해당 session을 리턴하고 없다면 새로운 session 객체를 생성해서 리턴


session이 생성된 경우에만 session 객체를 구하고 싶을 경우 매개값으로 false를 지정하면 세션이 존재하는 경우만 리턴하고 없을 경우엔 null리턴