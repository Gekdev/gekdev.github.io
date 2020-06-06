---
layout: default
title: basic
parent: HTML
nav_order: 1
---

# BASIC HTML

기본적인 WEB의 개념과 HTML의 내용을 담았습니다. 
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

챕터1 웹 프로그래밍과 html 개요
1. 웹 개요
웹의 기본 목적과 구성
	목적 : 한 컴퓨터에서 만든 문서를 다른 컴퓨터에서 쉽게 볼 수 있도록 하는 것
	기능 : 서버(문서나 이미지 동영상 등의 데이터 저장), 클라이언트(데이터를 사용자에게 업, 다운로드)
	웹 서버는 웹 서버 소프트웨어를 웹 클라이언트는 웹 브라우저를 탑재해야 한다

인터넷과 웹은 다르다
	인터넷 : IP주소를 부여받아 서로 연결하는 통신의 기본 체계
	웹(www): 문서를 서버에 올려놓고 인터넷을 통해 쉽게 주고받을 수 있게 한 인터넷 서비스 중 하나
	고속도로(인터넷) – 물류산업(웹)

웹 서버와 웹 사이트
	웹사이트 – 웹 서버 컴퓨터 [웹 서버 소프트웨어 – 웹 서버 응용프로그램 – 데이터베이스]
	웹 서버 소프트웨어 Apache, GWS
	웹 서버 응용프로그램 (소프트웨어 개발) C/C++, Java, JSP...

2. 웹의 시작과 성공
웹 브라우저 – 서버로부터 제공받은 데이터들을 해석하고 출력해주는 역할

3. 웹 페이지 구성
웹페이지 3대 구성요소
	HTML – 웹 페이지의 구조와 내용
	CSS – 웹 페이지의 모양
	Javascript – 웹 페이지의 동적 변경 및 응용프로그램 작성

4. html5
html5란?
	웹을 둘러싼 난무한 비 표준을 지양하고 지능적이고 실행 가능한 웹 구현을 위해 탄생한 차세대 웹 표준 기술
	문서공유, 문서표현 -> 하나의 응용프로그램으로 진화
	기존의 html 표준의 한계를 극복하는 차세대 웹 표준
	추가적인 플러그인 없이 리치웹 응용을 가능하게 한다
	시멘틱 마크업 - 더 명확한 의미표현
	목적: 웹 디자이너와 웹 개발자들에게 마크업 언어를 쓰기 쉽게 만드는 것

html5의 기능
	웹 문서 작성을 위한 표준화된 html 태그 셋(html 문서가 구조화되게 함)
	플러그인 없이 미디어 등을 재생할 수 있게 한다
	웹 페이지를 애플리케이션으로 만들 수 있도록 한 API

대표 사이트
	W3C : https://html.spec.whatwg.org/multipage/
	마크업 관련 자료 : http://html5doctor.com/
	쇼케이스 사이트 : http://html5gallery.com/
	테스트 : http://html5test.com/
	
 
5. html5 웹 프로그래밍 개발 과정
html5, css3, javascript 셋 다 검증 사이트 다름
디버깅 = 오류수정 과정, 디버깅 도구=개발자 도구

View this site's [_config.yml](https://github.com/pmarsceill/just-the-docs/tree/master/_config.yml) file as an example.

## Site logo

```yaml
# Set a path/url to a logo that will be displayed instead of the title
logo: "/assets/images/just-the-docs.png"
```

## Search

```yaml
# Enable or disable the site search
# Supports true (default) or false
search_enabled: true

# Enable support for hyphenated search words:
search_tokenizer_separator: /[\s/]+/

```

## Aux links

```yaml
# Aux links for the upper right navigation
aux_links:
  "Just the Docs on GitHub":
    - "//github.com/pmarsceill/just-the-docs"
```

## Heading anchor links

```yaml
# Heading anchor links appear on hover over h1-h6 tags in page content
# allowing users to deep link to a particular heading on a page.
#
# Supports true (default) or false/nil
heading_anchors: true
```

## Footer content

```yaml
# Footer content appears at the bottom of every page's main content
footer_content: "Copyright &copy; 2017-2019 Patrick Marsceill. Distributed by an <a href=\"https://github.com/pmarsceill/just-the-docs/tree/master/LICENSE.txt\">MIT license.</a>"
```

## Color scheme

```yaml
# Color scheme currently only supports "dark" or nil (default)
color_scheme: "dark"
```
<button class="btn js-toggle-dark-mode">Preview dark color scheme</button>

<script type="text/javascript" src="{{ "/assets/js/dark-mode-preview.js" | absolute_url }}"></script>

See [Customization]({{ site.baseurl }}{% link docs/customization.md %}) for more information.

## Google Analytics

```yaml
# Google Analytics Tracking (optional)
# e.g, UA-1234567-89
ga_tracking: UA-5555555-55
```
