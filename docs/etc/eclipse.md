---
layout: default
title: Eclipse
parent: ect
nav_order: 1
---

# Eclipse
{: .no_toc .text_beta .fw_700 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Eclipse

### Template Modify

![](https://gekdev.github.io/docs/etc/images/eclipse_html_set.jpg)

위와 같이 html 템플릿을 수정할 수 있음

---

## Eclipse Shortcut

---

## Eclipse Common Issues

### Refresing

이클립스로 spring 프로젝트를 진행하던 중 이미지 업로드 기능을 ajax 를 통해 구현하는데

이미지가 정상적으로 업로드 되었음에도 불구하고 이미지를 읽어오지 못하는 경우가 있었다.

이미지는 업로드가 되었지만 이클립스에서는 refresh 를 해주지 않아서 이클립스 내에서 파일을 인식하지 못하는 상황임을 알 수 있었다.

그래서 이 상황을 해결하려면

이클립스의 **window-preference** 에 들어가서 **general-workspace**에 보면

**build탭에서 refresh using native hooks or polling 과 save automatically before build** 이 두 항목을 체크해주면

빌드 되기전에 리프레시를 먼저 하여 파일을 인식할 수 있게 된다.

### [Run on Server](https://h2hyun37.tistory.com/79)

eclipse 에서 Run On Server 가 보이지 않는 경우, 

해당 프로젝트 Properties -> Project Facets -> Dynamic Web Module 체크 추가 해준다.

Version은 Java 버전에 맞는 J2EE 버전을 선택하면 된다.  



