---
layout: default
title: Accessibility
parent: HTML
nav_order: 5
---

# HTML Accessibility
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## HTML Accessibility

웹사이트를 제작할때에는 항상 사용자에게 사이트를 탐색하고 상호 작용할 수있는 좋은 방법을 제공하기 위해 접근성을 염두해야함 특히 **스크린 리더들을 위해 신경써야 하는 부분**

### Semantic HTML

의미가 없는 `<div>`나 `<span>` 대신 시멘틱 태그를 사용하기를 권장

[시멘틱 태그 더 알아보기](https://gekdev.github.io/docs/html/elements/6.semantic/)

### Headings Are Important

꼭 흐름에 맞게 헤딩을 작성할 수 있도록 하기

굵거나 크게 만들기 위해 사용해서는 안됨

### Img Alternative Text

항상 이미지의 alt태그를 상세하게 적기 (스크린 리더기가 읽는 부분)

### Declare the Language

스크린 리더기와 검색엔진을 위해 꼭 신경써야 하는 부분

```html
<html lang="en">
```

### Use Clear Language

이해하기 쉽게 문장을 단순하게 사용하기

* Keep sentences as short as possible.
* Avoid dashes. Instead of writing 1-3, write 1 to 3
* Avoid abbreviations. Instead of writing Feb, write February
* Avoid slang words
* A link should explain clearly

### Link Titles

타이틀 속성은 툴팁도 가능하지만 요소의 추가적인 정보도 담고있다

<div class="code-example" markdown="1">
<a href="https://www.w3schools.com/html/" title="Go to W3Schools HTML section">Visit our HTML Tutorial</a>
</div>
```html
<a href="https://www.w3schools.com/html/" title="Go to W3Schools HTML section">Visit our HTML Tutorial</a>
```