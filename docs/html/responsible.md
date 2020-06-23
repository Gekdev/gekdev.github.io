---
layout: default
title: Responsive
parent: HTML
nav_order: 8
---

# Responsive 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## HTML Responsive

### What is Responsive?

♣ HTML Responsive layout
1. Setting The Viewport
<meta name="viewport" content="width=device-width, initial-scale=1.0">
2. Responsive Images
Using the width Property
<img src="img_girl.jpg" style="width:100%;">

Using the max-width Property
max-width property is set to 100%, the image will scale down if it has to, but never scale up to be larger than its original size:

Show Different Images Depending on Browser Width
The HTML <picture> element allows you to define different images for different browser window sizes.
<picture>
  <source srcset="img_smallflower.jpg" media="(max-width: 600px)">
  <source srcset="img_flowers.jpg" media="(max-width: 1500px)">
  <source srcset="flowers.jpg">
  <img src="img_smallflower.jpg" alt="Flowers">
</picture>
3. Responsive Text Size
The text size can be set with a "vw" unit, which means the "viewport width".
Viewport is the browser window size. 1vw = 1% of viewport width. If the viewport is 50cm wide, 1vw is 0.5cm.
<h1 style="font-size:10vw">Hello World</h1>

4. Media Queries
In addition to resize text and images, it is also common to use media queries in responsive web pages.

With media queries you can define completely different styles for different browser sizes.

/* Use a media query to add a break point at 800px: */
@media screen and (max-width:800px) {
  .left, .main, .right {
    width:100%; /* The width is 100%, when the viewport is 800px or smaller */
  }
}
https://www.w3schools.com/html/tryit.asp?filename=tryhtml_responsive_media_query

5. Responsive Web Page - Full Example
A responsive web page should look good on large desktop screens and on small mobile phones.

a. 뷰포트 설정
다양한 기기에 최적화된 페이지는 문서의 헤드에 meta viewport 태그를 포함해야 합니다. meta viewport 태그는 페이지의 크기 및 배율을 제어하는 방법을 브라우저에 알려줍니다.

● meta viewport 태그를 사용하여 브라우저 뷰포트의 너비와 배율을 제어합니다.
● 기기 독립적 픽셀에서 화면 너비에 맞추려면 width=device-width를 포함합니다.
● 기기 독립적 픽셀과 CSS 픽셀 간에 1:1 관계를 설정하려면 initial-scale=1을 포함합니다.
initial-scale=1 속성을 추가하면, 기기 방향에 상관없이 브라우저가 기기 독립적 픽셀과 CSS 픽셀 간에 1:1 관계를 설정하고, 페이지에서 전체 가로 너비를 활용할 수 있습니다.
● 사용자 배율 조정을 비활성화하지 않고도 여러분의 페이지에 액세스할 수 있도록 합니다.

<meta name="viewport" content="width=device-width, initial-scale=1">

initial-scale 설정과 더불어 뷰포트에서 다음 속성을 설정할 수도 있습니다.

minimum-scale
maximum-scale
user-scalable
이들 속성이 설정된 경우, 사용자가 뷰포트를 확대/축소할 수 없으므로 접근성에 문제가 생길 수 있습니다.

//
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
content 값에 너무 많은 내용이 들어 간 듯 하지만, 천천히 살펴 보도록 하겠습니다.

width=device-width
페이지 너비를 기기의 너비와 동일하게 합니다. 'initial-scale=1.0'과 동일하다 할 수 있습니다.
minimum-scale=1.0
기기에서 줌 아웃을 할 때 가장 줄어들 수 있는 비율입니다. 예를 들어 0.8이라면 실제 페이지의 80%까지 더 축소할 수 있습니다. 1이면 실제 페이지에서 축소가 안됩니다.
maximum-scale=1.0
기기에서 줌 인을 할 때 가장 커질 수 있는 비율입니다. 2라면 두 배까지 확대 가능 합니다. 역시 1이라면 확대가 되지 않습니다.
user-scalable=no
이는 사용자가 페이지를 줌 인, 줌 아웃을 할 수 없도록 만듭니다. minimum-scale=1.0, maximum-scale=1.0 이 두 가지를 선언 한 것과 같은 기능이라 할 수 있습니다.


다음 글
메타 요소 (meta 태그)
최초 작성일 2015-02-09 최종 수정일 2015-02-09
이번 시간에는...
HTML head 태그에 들어가는 meta 태그에 대해 더 다룹니다. 검색엔진을 위한 description, keyword 외에도 author, refresh, IE용 메타, 그리고 모바일기기를 위한 viewport 메타도 살펴 봅니다.
이번 시간에는 head 요소 안에 들어가는 meta 요소에 대해 살펴봅니다. 사실 우린 이미 메타(meta) 요소에 대해서 지난 'HTML 초급 강의 - head 요소'에서 다뤘습니다. 사실 그것 만으로도 충분할 수 있겠습니다만, 좀더 고급과정으로써 다루지 않았던 meta 요소에 대해서 더 다뤄보도록 하겠습니다. 물론 전 강의에서 다뤘던 메타 항목들도 복습차원에서 간단히 짚고 넘어가겠습니다.

문자셋 (charset) 메타 정보
 <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
이미 다뤘던 메타 정보로, 현재 페이지의 인코딩(문자셋)을 어떠한 방식으로 출력할 지 결정하는 속성입니다. 만약 제작한 웹 페이지의 한글이 깨져 보인다면, 거의 이 메타정보와 실제 페이지의 문자셋이 달라 생긴 문제일 가능성이 매우 큽니다. 이러한 현상은 이 메타 정보가 아예 선언되지 않았을 때에도 종종 발생하므로, 올바른 문자셋 정보를 꼭 넣는 것을 권장합니다. (관련 포스트 : 글자 깨짐 현상)

국내에서는 보통 'UTF-8'과 'EUC-KR'을 많이 사용하고 있습니다. 그리고 현재 추세는 다른 언어의 사용자가 접근 시에도 올바르게 보여질 수 있는 'UTF-8'를 권장하고 있습니다.


 
디스크립션(description)과 키워드(keyword) 메타 정보
 <meta name="Description" content="소개 내용" />
<meta name="Keywords" content="키워드들의 나열, abc, 123" />
이 디스크립션(description)과 키워드(keyword) 메타 정보는 주로 검색엔진과 관련이 있습니다.

디스크립션(description) 정보 같은 경우는 현재 페이지를 간략히 소개하는 문구를 적도록 합니다. 이를 검색엔진이 검색된 페이지에 페이지 제목과 같이 표현하며, '공유하기' 같은 것을 했을 때에 활용이 될 수도 있습니다.

키워드(keyword)는 페이지에 대한 키워드 정보들을 담고 있습니다. 페이지의 주요한 단어들을 콤마(,)로 구분하여 값을 넣어주도록 합니다. 이 키워드 정보는 검색엔진이 보다 검색엔진을 용이하도록 하게 만듭니다만, 이를 악용한 광고성 페이지들은 실제 콘텐츠와는 다른 단어들을 무작위로 넣기도 합니다. 이런 경우 검색엔진이 해당 페이지를 스팸 페이지로 인지할 수 있으니 주의하시기 바랍니다. 또한, 이런 이유 때문에 요새 검색엔진은 이 키워드 정보를 아예 수집하지 않는다는 의견도 있습니다.

작성자(author) 관련 메타 정보
<meta name="author" content="your name" />
<meta name="generator" content="dreamweaver cs6" />
name 속성의 값이 "author"인 정보는 페이지의 저자를 나타냅니다. content의 값으로 저자를 나타내는 문자열을 써야 합니다. 이 메타정보가 큰 의미를 가지진 않지만, 소스 상에서도 자신이 제작했음을 명시할 수 있습니다.

name 속성의 값이 "generator"인 정보는 이 페이지를 생성한 프로그램을 나타냅니다. content의 값은 해당 프로그램의 명칭이 들어갑니다. 다만 이 정보는 손으로 직접 코딩 한 경우에는 이 값을 사용하지 말아야 합니다. (예를 들어 메모장에서 작업한 경우는 직접 코딩 한 경우이므로, 값으로 'notepad'같은 것이 들어갈 일은 없을 것입니다.) 이 정보는 프로그램이 알아서 코드를 생성한 경우에 사용하기 때문에, 보통 그러한 프로그램을 사용할 경우 자동으로 추가가 될 가능성이 큽니다. 그런 이유로 이 메타정보를 쓸 일은 아마 없을 것이라 예상 됩니다.


 
우회 및 새로고침(refresh) 메타 정보
 <meta http-equiv="refresh" content="30" />
이 메타 요소는 조금 특이한 역할을 합니다. 바로 웹 페이지를 주기적으로 새로고침 하도록 만들어 줍니다. 이를 활용해서 광고를 새로고침 시키는 페이지들도 종종 있습니다만, 이는 좋은 방법이 아닙니다. 예상치 못하는 새로고침은 사용자로 하여금 불편을 야기하며, 특히 스크린리더로 접근하는 사람은 더욱 그렇습니다. 부분적인 영역의 새로고침 같은 경우는 자바스크립트를 통해 부분적으로 해결하는 것이 좋습니다. 요새 이 메타 요소를 사용하는 서비스는 별로 없으며, 이 요소는 사용하지 마시길 바랍니다.

추가적으로 이 요소에 'content'값을 약간 수정하면 페이지를 우회 시킬 수 있습니다.

 <meta http-equiv="refresh" content="10;url=http://google.com/" />
예를 들어 위와 같이 content 값에 기존 숫자를 ';'으로 구분 짓고서 'url='로 시작하는 부분에 URL 주소를 넣어준다면, 해당 숫자만큼의 초가 지나면 해당 주소의 페이지로 이동하게 됩니다. 예를 들어 어떤 페이지가 '공사 중 입니다. 10초 후에 다른 페이지로 이동합니다' 라는 식의 문구를 가진 페이지는 보통 이런 방식을 사용합니다. 그리고 만약 해당 숫자를 '0'으로 바꾼다면 페이지 접속하자마자 해당 url로 이동하게 됩니다.

이러한 우회 방식은 기존 링크이동과는 다르게 히스토리 조차 남지 않으며, 뒤로 가기에도 남아있지 않습니다. 그 만큼 이러한 방식 역시, 사용자에게 예상치 못한 상황을 발생시키기 때문에 접근성에 있어서도 좋지 않습니다. 또한 이런 방식은 검색엔진에 있어서도 좋지 않기 때문에 구글에서도 이와 같은 방식을 권장하지 않으며, 해당 페이지의 URL을 변경해야 하는 경우 '301 리디렉션'을 사용하길 권장합니다. (구글 - 301 리디렉션으로 페이지 URL 변경)

IE 모드(mode) 메타 정보
 <meta http-equiv="X-UA-Compatible" content="IE=edge" />
이 메타 요소는 전에 크로스 브라우징 시간에 다뤘던 요소입니다. 이 메타 정보는 IE(인터넷 익스플로러)가 하위 버전 IE모드로 렌더링 하도록 만들어 줍니다. 예를 들어 content속성 값에 "IE=EmulateIE7"로 넣는 경우, IE8 이상의 최신 IE 브라우저라도 IE7 버전처럼 페이지를 렌더링 합니다.

물론 전에 말씀 드렸듯이 이런 하위 렌더링 모드는 버전 업이 되면서, 조금씩 버그들이 생겨나고 있습니다. 때문에, 부득이한 경우가 아니라면 하위 모드는 사용하지 마시고, 대신 "IE=edge"를 넣어 해당 브라우저가 가장 표준적인 페이지로 렌더링 되도록 하시기 바랍니다.


 


뷰포트(viewport) 메타 정보
 <meta name="viewport" content="width=1200" />
이 메타 요소는 스마트폰이나 태블릿과 같은 모바일 환경을 위해 생긴 메타 정보입니다. 그래서 사실 이번 시간엔 다루지 말까 하다 XHTML에 넣어도 표준에 위배 되지 않고, 요즘 시대에 분명 유용한 메타 정보이기에 소개해드립니다.

요새는 많은 페이지들이 모바일용으로 따로 제작되긴 합니다만, 만약 스마트폰을 이용해서 PC 버전의 페이지를 접근했을 경우 보통 해당 페이지가 축소되어 전체 너비가 한 화면 안에 쏙 들어오게 보여집니다.

  모바일에서 PC용 웹 페이지를 봤을 때 모습. 모바일에서 본 웹 페이지
이 메타정보는 해당 페이지의 콘텐츠 너비를 명시 해줍니다. 만약 이 메타 정보를 명시하지 않고, 쇼핑몰 같은 곳에 들어가는 '최근 본 상품' 윙 영역 같은 부분이 있다면, 해당 윙 영역이 계산되지 않은 채 화면에 가려질 수 있습니다. 또한, 스마트폰에서 자동으로 맞게 축소하는 것은 부정확한 크기로 보여질 수 있으니, 이 메타 요소를 명시해 주는 것이 좋습니다.

  뷰포트값을 웹 페이지 너비와 같은 값을 줬을 땐 페이지가 꽉 차서 보이지만, 웹 페이지보다 큰 너비를 줄 경우 상대적으로 페이지가 작어 보입니다. 뷰포트 너비에 따른 페이지 비교
또한 이 속성은 PC버전용 페이지를 모바일 기기에서 접속했을 때 보다, 모바일용 페이지에서 더욱 중요한 역할을 합니다. content 속성 값에 "width" 말고 다른 속성을 넣을 수 있습니다. 다음과 같이요.

 <meta name="viewport" content="initial-scale=1.0" />
이 내용을 처음 크기를 1:1 비율로 보여줍니다. 만약 'initial-scale'에 해당하는 값이 '2.0' 이라면 크기를 두 배 확대된 모습을 보여줄 것입니다. 모바일용 페이지라면 화면이 처음에 축소된 모습을 보이지 말아야 하기 때문에, 반드시 넣어줘야 하는 값입니다. 그리고 사실 이 속성값 말고도 추가적으로 더 넣어줍니다.

 <meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
content 값에 너무 많은 내용이 들어 간 듯 하지만, 천천히 살펴 보도록 하겠습니다.

width=device-width
페이지 너비를 기기의 너비와 동일하게 합니다. 'initial-scale=1.0'과 동일하다 할 수 있습니다.
minimum-scale=1.0
기기에서 줌 아웃을 할 때 가장 줄어들 수 있는 비율입니다. 예를 들어 0.8이라면 실제 페이지의 80%까지 더 축소할 수 있습니다. 1이면 실제 페이지에서 축소가 안됩니다.
maximum-scale=1.0
기기에서 줌 인을 할 때 가장 커질 수 있는 비율입니다. 2라면 두 배까지 확대 가능 합니다. 역시 1이라면 확대가 되지 않습니다.
user-scalable=no
이는 사용자가 페이지를 줌 인, 줌 아웃을 할 수 없도록 만듭니다. minimum-scale=1.0, maximum-scale=1.0 이 두 가지를 선언 한 것과 같은 기능이라 할 수 있습니다.
위에 어떻게 보면 중복된 기능을 담은 내용을 같이 적어 줬는데요, 모바일 기기 중에는 메타 정보 중에 몇 가지는 지원하지 않을 수 있기 때문에, 호환성을 위해 같이 넣었습니다.

모바일 기기에서 페이지를 접근 시, 사용자가 원하는 대로 줌 인, 줌 아웃을 할 수 있도록 하는 게 좋습니다. 하지만, 모바일 페이지의 경우 확대/축소 시 레이아웃 깨짐이 발생할 수 있기 때문에 이를 방지하는 경우가 많은데요, 그런 경우에는 꼭 글자 크기를 조절할 수 있는 옵션을 만들어 주는 것이 좋습니다. 대부분의 확대/축소는 글자를 보기 위함이기 때문이고, 이런 부분 하나하나가 사용자의 접근성을 보다 향상 시켜줍니다. (물론 그런 옵션 '동작'은 자바스크립트로 처리되어야 합니다.)

b. 뷰포트에 맞게 콘텐츠 크기 조정
데스크톱 및 휴대기기에서 사용자는 가로가 아닌 세로로 웹사이트를 스크롤하는 데 익숙하며, 전체 페이지를 확인하기 위해 가로 스크롤이나 축소를 강제로 수행해야 한다면 사용자 환경이 나빠질 것입니다.

TL;DR
● 너비가 고정된 큰 요소를 사용하지 마세요.
● 잘 렌더링되기 위해서는 콘텐츠가 특정 뷰포트 너비에 종속되어서는 안 됩니다.
● 큰 화면과 작은 화면에 다른 스타일을 적용하려면 CSS 미디어 쿼리를 사용합니다.

meta viewport 값 width=device-width를 사용하면 기기 독립적 픽셀에서 화면 너비에 맞게 페이지를 맞춥니다. 이렇게 하면 렌더링되는 화면이 작은 휴대폰이든 큰 데스크톱 모니터에든 상관없이, 다양한 화면 크기에 맞게 페이지의 콘텐츠를 재배치할 수 있습니다.

c. 응답성을 개선하기 위해 CSS 미디어 쿼리 사용
미디어 쿼리는 CSS 스타일에 적용될 수 있는 간단한 필터입니다. 이 필터를 사용하면, 콘텐츠를 렌더링하는 기기 특성(예: 표시 유형, 너비, 높이, 방향, 해상도 등을 포함)에 따라 쉽게 스타일을 변경할 수 있습니다.

TL;DR
● 기기 특성을 기반으로 스타일을 적용하려면 미디어 쿼리를 사용합니다.
● min-device-width보다 min-width를 사용하여 가장 넓은 환경을 보장합니다.
● 레이아웃이 깨지는 것을 막으려면 요소에 상대 크기를 사용합니다.

더 자세히...
https://developers.google.com/web/fundamentals/design-and-ux/responsive/?hl=ko

basic sample:
https://www.w3schools.com/html/tryit.asp?filename=tryhtml_responsive_media_query3

// framework를 사용하는 방법이 있음 -Using W3.CSS or Bootstrap

Web font 사용
1. @font-face : Using The Font You Want (내가 가지고있는 것 )
In the @font-face rule; first define a name for the font (e.g. myFirstFont) and then point to the font file.

Tip: Always use lowercase letters for the font URL. Uppercase letters can give unexpected results in IE.

