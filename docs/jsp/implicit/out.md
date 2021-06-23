---
layout: default
title: Out
parent: Implicit Object
grand_parent : JSP
nav_order: 6
---

# Out Implicit Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Out Implicit Object

### Out Implicit Object Basic

**웹 브라우저에 데이터를 전송하는 출력 스트림 객체로서 jsp가 생성한 데이터를 출력**

&#9656; JSP 컨테이너는 JSP 페이지에 사용되는 모든 표현문 태그와 HTML, 일반텍스트 등을 out 내장 객체를 통해 웹 브라우저에 그대로 전달

&#9656; 스크립틀릿 태그에 사용하여 단순히 값을 출려가는 표현문 태그(<%= ...%>)와 같은 결과를 얻을 수 있음

### 출력메서드 

print()		데이터를 출력
println()	데이터를 줄바꿈 문자(\r\n 또는 \n)와 출력
newLine()	줄바꿈문자(\r\n 또는 \n)를 출력

### buffer관련 메서드

| getBufferSize()	| 버퍼의 크기를 리턴											|
| getRemaining()	| 버퍼에 남은 크기를 리턴										  |
| clear()			| 버퍼를 비움, 이미 flush가 되어있다면 익셉션이 발생 			 |
| clearBuffer()		| 버퍼를 비움, 이미 flush가 되어있어도 익셉션이 발생하지 않음	 |
| flush()			| 버퍼를 flush													 |
| isAutoFlush()		| 자동 flush여부를 boolean으로 리턴 							   |

