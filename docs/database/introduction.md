---
layout: default
title: Introduction
parent: Database
nav_order: 1
---

# Database Introduction
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background Knowledge 

### Data and Information

* 데이터 : **단순한 관찰이나 측정 등의 수단을 통해 현실 세계로부터 수집된 사실이나 값**

* 정보 : **데이터 중에서도 조직화되고 체계화 된 데이터로서 의사 결정권자에게 의미를 제공하는 것**

**★ 데이터베이스에서 데이터는 정보를 의미함**

### Data Processing

**정보처리, 데이터에서 정보를 추출하는 과정, 방법을 나타냄**

상황에 맞게 해석해 의미 있는 결과 도출

### Data System

**조직 운영에 필요한 데이터를 수집해 저장해 두었다가 필요할 때 유용한 정보를 만들어 주는 수단**

### Database

**한 조직의 여러 응용시스템들이 공유해서 사용할 수 있도록 데이터들을 통합해 체계적으로 조직한 후 저장한 운영데이터의 집합**
 
![](https://gekdev.github.io/docs/database/basic/example/data_system.png)

### Database Users

* 클라이언트 : 일반 사용자

* 응용프로그래머 : 데이터베이스 전문 지식을 가지고 어플리캐이션을 개발할 목적으로 데이터베이스를 사용하는 사용사

* 데이터베이스 관리자(DBA) : 데이터베이스를 구축, 운영, 통제하는 특별한 소수 사용자

* DB서버 : DBMS를 사용하는 서버

![](https://gekdev.github.io/docs/database/basic/example/db_basic_structure.png)

---

## Classification of data (Bigdata)

정형 데이터와 비정형 데이터는 서로 배척관계가 아님

### Structured Data

**정형 데이터**

&#9656; 구조화된 데이터, 즉 미리 정해진 구조(schema)에 따라 저장된 데이터

ex) 엑셀의 스프레드시트, 관계 데이터베이스의 테이블

### Semi-structured Data

**반정형 데이터**

&#9656; 구조에 따라 저장된 데이터이지만, 데이터 내용 안에 구조에 대한 설명이 함께 존재

&#9656; 구조 파악하는 파싱(parsing) 과정 필요

&#9656; 보통 파일 형태로 저장

ex) HTML, XML, JSON 문서, 웹 로그, 센서 데이터

### Unstructured Data

**비정형 데이터**

&#9656; 정해진 구조가 없이 저장된 데이터

ex) 소셜 데이터의 텍스트, 영상, 이미지, 워드, PDF 문서 등의 멀티미디어 데이터

![](https://gekdev.github.io/docs/database/basic/example/datatype3.png)

---

## Reference site

* [데이터베이스 기초 - (1)기초개념익히기](https://www.bsidesoft.com/4754)

* [데이터, 데이터베이스란?](https://ahnty0122.tistory.com/26)

* [데이터 베이스 기초 강의 (DB의 개념)](https://nackwon.tistory.com/96)

