---
layout: default
title: Getter and Setter
parent: Class
grand_parent: Java
nav_order: 6
---

# Class Package
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

클래스를 선언할 떄 필드는 일반적으로 private 접근 제한

읽기 전용 필드가 있을수도 있음 (Getter의 필요성)

외부에서 엉뚱한 값으로 변경할 수 없도록 해야함 (Setter의 필요성)

## Getter 

private필드의 값을 리턴하는 역할

필요할 경우 필드의 값을 가공함

이름 명명 : get으로 하되 필드 타입이 boolean일경우 is로 함

ex) getFieldName() or isFieldName()

## Setter

외부에서 주어진 값을 필드 값으로 수정

필요할 경우 외부의 값을 유효성 검사

이름명명 : set

FieldName(타입변수) 메소드, 매개변수타입은 필드의 타입과 동일 