---
layout: default
title: Introduction
parent: html
nav_order: 1
---

# Introduction
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## HTML Intronduction

### What is HTML5?
**웹을 둘러싼 난무한 비 표준을 지양하고 지능적이고 실행 가능한 웹 구현을 위해 탄생한 차세대 웹 표준 기술**

* 문서공유, 문서표현 -> 하나의 응용프로그램으로 진화
* standard markup language for creating Web pages
* 기존의 html 표준의 한계를 극복하는 차세대 웹 표준 
* 추가적인 플러그인 없이 리치웹 응용을 가능하게 한다
* 시멘틱 마크업 - 더 명확한 의미표현
* HTML elements are represented by tags
* 목적: 웹 디자이너와 웹 개발자들에게 마크업 언어를 쓰기 쉽게 만드는 것

### Features of HTML5
* 웹 문서 작성을 위한 표준화된 html 태그 셋(html 문서가 구조화되게 함)
* 플러그인 없이 미디어 등을 재생할 수 있게 한다
* 웹 페이지를 애플리케이션으로 만들 수 있도록 한 API
* HTML Is Not Case Sensitive
    **W3C recommends lowercase in HTML, and demands lowercase for stricter document types like XHTML.**
* attribute값 안에 불필요한 공백이 들어가면 오류 but 파일 이름 등 필수로 들어가는 경우 “”로 묶어야지 속성 값 안에 빈칸이 들어가는 경우 오류가 안남


### Basic Terms
* 디버깅 : 오류수정 과정
* 디버깅 도구 : 개발자 도구

### A Simple HTML Document
![](https://gekdev.github.io/assets/images/noname01.png)

* <!DOCTYPE html> declaration defines this document to be HTML5
	This represents the document type, and helps browsers to display web pages correctly.
* <html> element is the root element of an HTML page
* <head> element contains meta information about the document
 	metadata is data about the HTML document
* <title> element specifies a title for the document
* <body> element contains the visible page content 
    (바디에는 높이가 없음 이미 width가 100%)
* <h1> element defines a large heading
* <p> element defines a paragraph

### HTML Tags
* HTML Elements
    HTML tags normally come in pairs like `<p> {start tag(opening tag)} </p>{end tag(closing tag)}`
    The end tag is written like the start tag, but with a forward slash inserted before the tag name
    ```html
    <tagname>content goes here</tagname>
    ```

* Empty HTML Elements
    Empty elements : HTML elements with no content. Empty elements do not have an end tag, such as the `<br>` element


### Representative site
[W3C](https://html.spec.whatwg.org/multipage/)<br>
[마크업 관련 자료](http://html5doctor.com/)<br>
[쇼케이스 사이트](http://html5gallery.com/)<br>
[테스트](http://html5test.com/)<br>


