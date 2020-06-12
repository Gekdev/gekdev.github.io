---
layout: default
title: Blog
parent: Ect
nav_order: 99
---

# 블로그 사용법
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## UI Components

기본적으로 반응형 레이아웃

### Typography

* Responsive type scale

| Selector              | Small screen size `font-size`    | Large screen size `font-size` |
|:----------------------|:---------------------------------|:------------------------------|
| `h1`, `.text-alpha`   | 32px                             | 36px                          |
| `h2`, `.text-beta`    | 18px                             | 24px                          |
| `h3`, `.text-gamma`   | 16px                             | 18px                          |
| `h4`, `.text-delta`   | 14px                             | 16px                          |

epsilon, zeta도 있는데 폰트사이즈가 더 커짐 - 최대한 사용하지 않기

(기본 폰트사이즈 14px = h4 .text-delta)

* Headings

```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```
기본적으로 테이블 레이아웃에 나옴

* blockquote following a header

<div class="code-example" markdown="1">
> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.
</div>
```markdown
> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.
```

* Inline elements

```markdown
Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](another-page).
```

### Buttons

* Button colors

<div class="code-example" markdown="1">
[Link button](http://example.com/){: .btn }
[Link button](http://example.com/){: .btn .btn-purple }
[Link button](http://example.com/){: .btn .btn-blue }
[Link button](http://example.com/){: .btn .btn-green }
[Link button](http://example.com/){: .btn .btn-outline }
</div>

```markdown
[Link button](http://example.com/){: .btn }
[Link button](http://example.com/){: .btn .btn-purple }
[Link button](http://example.com/){: .btn .btn-blue }
[Link button](http://example.com/){: .btn .btn-green }
[Link button](http://example.com/){: .btn .btn-outline }
```

* Button size

span 태그를 부모로 감싸주고 클래스로 크기를 줘서 버튼크기 조절

<div class="code-example" markdown="1">
<span class="fs-6">
[Big ass button](http://example.com/){: .btn }
</span>

<span class="fs-3">
[Tiny ass button](http://example.com/){: .btn }
</span>
</div>
```markdown
<span class="fs-8">
[Link button](http://example.com/){: .btn }
</span>

<span class="fs-3">
[Tiny ass button](http://example.com/){: .btn }
</span>
```

마진 클래스를 줄수도 있음

### Labels

형광펜처럼 강조를 하고싶을때 사용, 기본이 blue

<div class="code-example" markdown="1">
Default label
{: .label }

Blue label
{: .label .label-blue }

Stable
{: .label .label-green }

New release
{: .label .label-purple }

Coming soon
{: .label .label-yellow }

Deprecated
{: .label .label-red }
</div>
```markdown
Default label
{: .label }

Blue label
{: .label .label-blue }

Stable
{: .label .label-green }

New release
{: .label .label-purple }

Coming soon
{: .label .label-yellow }

Deprecated
{: .label .label-red }
```

### Tables

기본 테이블구조

<div class="code-example" markdown="1">

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

</div>
```markdown
| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |
```

### Lists

* 순서목록 : 동시에 같이써야 카운트됨 ㅠㅠ

<div class="code-example" markdown="1">
1. Item 1
1. Item 2
1. Item 3
</div>
```markdown
1. Item 1
1. Item 2
1. Item 3
```

* 비순서목록 : 둘다 점으로 나옴

```markdown
- Item 1
- Item 2
- Item 3

_or_

* Item 1
* Item 2
* Item 3
```

! 이렇게 섞어서 써도 됨

```
- level 1 item (ul)
  1. level 2 item (ol)
  1. level 2 item (ol)
    - level 3 item (ul)
    - level 3 item (ul)
- level 1 item (ul)
  1. level 2 item (ol)
  1. level 2 item (ol)
    - level 3 item (ul)
    - level 3 item (ul)
  1. level 4 item (ol)
  1. level 4 item (ol)
    - level 3 item (ul)
    - level 3 item (ul)
- level 1 item (ul)
```

* 체크박스

<div class="code-example" markdown="1">
- [ ] hello, this is a todo item
- [ ] hello, this is another todo item
- [x] goodbye, this item is done
</div>
```markdown
- [ ] hello, this is a todo item
- [ ] hello, this is another todo item
- [x] goodbye, this item is done
```

* 정의목록

```html
<dl>
  <dt>Name</dt>
  <dd>Godzilla</dd>
  <dt>Born</dt>
  <dd>1952</dd>
  <dt>Birthplace</dt>
  <dd>Japan</dd>
  <dt>Color</dt>
  <dd>Green</dd>
</dl>
```

### Image

![](https://guides.github.com/activities/hello-world/branching.png)

```
![](https://guides.github.com/activities/hello-world/branching.png)
```

### Code

* 인라인 코드

<div class="code-example" markdown="1">
`<inline code snippet>`
</div>

짧은 코드를 쓸때 사용

* 블록 코드

{% highlight markdown %}
```js 
    //자바스크립트
```

```yaml or bash or scss or ruby... 와같이 사용언어 적기
```
{% endhighlight %}

---

## Utilities

### Responsive Modifiers

| Modifier  | Screen size                          |
|:----------|:-------------------------------------|
| (none)    | All screens until the next modifier  |
| `xs`      | 320px (20rem) and up                 |
| `sm`      | 500px (31.25rem) and up              |
| `md`      | 740px (46.25rem) and up              |
| `lg`      | 1120px (70rem) and up                |
| `xl`      | 1400px (87.5rem) and up              |

### Layout
* Spacing

| Classname prefix | What it does                  |
|:-----------------|:------------------------------|
| `.m-`            | `margin`                      |
| `.mx-`           | `margin-left`, `margin-right` |
| `.my-`           | `margin top`, `margin bottom` |
| `.mt-`           | `margin-top`                  |
| `.mr-`           | `margin-right`                |
| `.mb-`           | `margin-bottom`               |
| `.ml-`           | `margin-left`                 |

| Classname prefix | What it does                    |
|:-----------------|:--------------------------------|
| `.p-`            | `padding`                       |
| `.px-`           | `padding-left`, `padding-right` |
| `.py-`           | `padding top`, `padding bottom` |
| `.pt-`           | `padding-top`                   |
| `.pr-`           | `padding-right`                 |
| `.pb-`           | `padding-bottom`                |
| `.pl-`           | `padding-left`                  |

Spacing values are based on a `1rem = 16px` spacing scale, broken down into these units:

| Spacer/suffix  | Size in rems  | Rem converted to px |
|:---------------|:--------------|:--------------------|
| `1`            | 0.25rem       | 4px                 |
| `2`            | 0.5rem        | 8px                 |
| `3`            | 0.75rem       | 12px                |
| `4`            | 1rem          | 16px                |
| `5`            | 1.5rem        | 24px                |
| `6`            | 2rem          | 32px                |
| `7`            | 2.5rem        | 40px                |
| `8`            | 3rem          | 48px                |

#### Examples
{: .no_toc }

In Markdown, use the `{: }` wrapper to apply custom classes:

```markdown
This paragraph will have a margin bottom of 1rem/16px at large screens.
{: .mb-lg-4 }

This paragraph will have 2rem/32px of padding on the right and left at all screen sizes.
{: .px-6 }
```

* Vertical Alignment 

| Classname              | What it does                    |
|:-----------------------|:--------------------------------|
| `.v-align-baseline`    | `vertical-align: baseline`      |
| `.v-align-bottom`      | `vertical-align: bottom`        |
| `.v-align-middle`      | `vertical-align: middle`        |
| `.v-align-text-bottom` | `vertical-align: text-bottom`   |
| `.v-align-text-top`    | `vertical-align: text-top`      |
| `.v-align-top`         | `vertical-align: top`           |

* Display

| Class             |                         |
|:------------------|:------------------------|
| `.d-block`        | `display: block`        |
| `.d-flex`         | `display: flex`         |
| `.d-inline`       | `display: inline`       |
| `.d-inline-block` | `display: inline-block` |
| `.d-none`         | `display: none`         |

Use these classes in conjunction with the responsive modifiers.

#### Examples
{: .no_toc }

In Markdown, use the `{: }` wrapper to apply custom classes:

```markdown
This button will be hidden until medium screen sizes:

[ A button ](#url)
{: .d-none .d-md-inline-block }

These headings will be `inline-block`:
```

### Color

텍스트나 배경 색상 클래스 모음

* Light Greys

| Color value    | Font color utility   | Background color utility |
|:---------------|:---------------------|:-------------------------|
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-lt-000"></span> `grey-lt-000` | `.text-grey-lt-000` | `.bg-grey-lt-000` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-lt-100"></span> `grey-lt-100` | `.text-grey-lt-100` | `.bg-grey-lt-100` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-lt-200"></span> `grey-lt-200` | `.text-grey-lt-200` | `.bg-grey-lt-200` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-lt-300"></span> `grey-lt-300` | `.text-grey-lt-300` | `.bg-grey-lt-300` |

* Dark Greys

| Color value    | Font color utility   | Background color utility |
|:---------------|:---------------------|:-------------------------|
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-dk-000"></span> `grey-dk-000` | `.text-grey-dk-000` | `.bg-grey-dk-000` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-dk-100"></span> `grey-dk-100` | `.text-grey-dk-100` | `.bg-grey-dk-100` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-dk-200"></span> `grey-dk-200` | `.text-grey-dk-200` | `.bg-grey-dk-200` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-dk-250"></span> `grey-dk-250` | `.text-grey-dk-250` | `.bg-grey-dk-250` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-grey-dk-300"></span> `grey-dk-300` | `.text-grey-dk-300` | `.bg-grey-dk-300` |

* Purples

| Color value    | Font color utility   | Background color utility |
|:---------------|:---------------------|:-------------------------|
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-purple-000"></span> `purple-000` | `.text-purple-000` | `.bg-purple-000` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-purple-100"></span> `purple-100` | `.text-purple-100` | `.bg-purple-100` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-purple-200"></span> `purple-200` | `.text-purple-200` | `.bg-purple-200` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-purple-300"></span> `purple-300` | `.text-purple-300` | `.bg-purple-300` |

* Blues

| Color value    | Font color utility   | Background color utility |
|:---------------|:---------------------|:-------------------------|
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-blue-000"></span> `blue-000` | `.text-blue-000` | `.bg-blue-000` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-blue-100"></span> `blue-100` | `.text-blue-100` | `.bg-blue-100` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-blue-200"></span> `blue-200` | `.text-blue-200` | `.bg-blue-200` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-blue-300"></span> `blue-300` | `.text-blue-300` | `.bg-blue-300` |

* Greens

| Color value    | Font color utility   | Background color utility |
|:---------------|:---------------------|:-------------------------|
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-green-000"></span> `green-000` | `.text-green-000` | `.bg-green-000` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-green-100"></span> `green-100` | `.text-green-100` | `.bg-green-100` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-green-200"></span> `green-200` | `.text-green-200` | `.bg-green-200` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-green-300"></span> `green-300` | `.text-green-300` | `.bg-green-300` |

* Yellows

| Color value    | Font color utility   | Background color utility |
|:---------------|:---------------------|:-------------------------|
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-yellow-000"></span> `yellow-000` | `.text-yellow-000` | `.bg-yellow-000` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-yellow-100"></span> `yellow-100` | `.text-yellow-100` | `.bg-yellow-100` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-yellow-200"></span> `yellow-200` | `.text-yellow-200` | `.bg-yellow-200` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-yellow-300"></span> `yellow-300` | `.text-yellow-300` | `.bg-yellow-300` |

* Reds

| Color value    | Font color utility   | Background color utility |
|:---------------|:---------------------|:-------------------------|
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-red-000"></span> `red-000` | `.text-red-000` | `.bg-red-000` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-red-100"></span> `red-100` | `.text-red-100` | `.bg-red-100` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-red-200"></span> `red-200` | `.text-red-200` | `.bg-red-200` |
| <span class="d-inline-block p-2 mr-1 v-align-middle bg-red-300"></span> `red-300` | `.text-red-300` | `.bg-red-300` |

### Typography

* Font size

아래처럼 1부터 10까지 쓸수는 있는데 2-6사이가 제일 많이 쓰임

| Class   | Small screen size `font-size`  | Large screen size `font-size` |
|:--------|:-------------------------------|:------------------------------|
| `.fs-1` | 9px                            | 10px                          |
| `.fs-2` | 11px                           | 12px                          |
| `.fs-3` | 12px                           | 14px                          |
| `.fs-4` | 14px                           | 16px                          |
| `.fs-5` | 16px                           | 18px                          |
| `.fs-6` | 18px                           | 24px                          |
| `.fs-7` | 24px                           | 32px                          |
| `.fs-8` | 32px                           | 38px                          |
| `.fs-9` | 38px                           | 42px                          |
| `.fs-10`| 42px                           | 48px                          |

* Font weight

300~500 다같음

<div class="code-example" markdown="1">
Font weight 300
{: .fw-300 }
Font weight 400
{: .fw-400 }
Font weight 500
{: .fw-500 }
Font weight 700
{: .fw-700 }
</div>
```markdown
In Markdown, use the `{: }` wrapper to apply custom classes:

Font weight 300
{: .fw-300 }
Font weight 400
{: .fw-400 }
Font weight 500
{: .fw-500 }
Font weight 700
{: .fw-700 }
```

* Line height

| Class         | `line-height` value  | Notes                         |
|:--------------|:---------------------|:------------------------------|
| `.lh-0`       | 0                    |                               |
| `.lh-tight`   | 1.1                  | Default for headings          |
| `.lh-default` | 1.4                  | Default for body (paragraphs) |

---

## Navigation Structure

### Main navigation

네비게이션은 2차 자손까지 만들 수 있음, 순서는 nav_order에서 작성

### Excluding pages

네비게이션에 포함되는걸 원치 않는 페이지(나만보는)

#### Example
{: .no_toc }

```yaml
---
layout: default
title: 404
nav_exclude: true
---
```

### Pages with children

* 부모 YAML

```yaml
---
layout: default
title: UI Components
nav_order: 2
has_children: true
---
```

* 자식 YAML

```yaml
---
layout: default
title: Buttons
parent: UI Components
nav_order: 2
---
```


! 부모페이지에서 자동으로 자식 페이지를 table로 설정하는데 원하지 않을경우

```yaml
---
layout: default
title: UI Components
nav_order: 2
has_children: true
has_toc: false
---
```

### Children with children

자식이 자손을 가질경우 (투뎁스)

- 부모 YAML

```yaml
---
layout: default
title: Buttons
parent: UI Components
nav_order: 2
has_children: true
---
```

- 자식 YAML

```yaml
---
layout: default
title: Buttons Child Page
parent: Buttons
grand_parent: UI Components
nav_order: 1
---
```

### In-page navigation with Table of Contents

: 목차범위 재설정

`ol` 다음 `{:toc}` 을 작성하면 테이블이 자동으로 작성됨, 테이블에 나타나고싶지 않은 헤딩은 `{:no_toc}`을 사용

## Customization

변경은 대부분 `_sass/custom/custom.scss` 에서 하기. 삭제하지 않고 수정만!

`_sass/support/variables.scss`파일은 건들지 마세요

`_sass/overrides.scss.`파일에 클래스를 직접 지정해서 넣을 수 있음

---

## Search

객체지향 검색 인터페이스를 JSON으로 사용 

### Hiding pages from search

검색되지 않길 원하는 페이지

```yaml
---
layout: default
title: Page not found
nav_exclude: true
search_exclude: true
---
```