---
layout: default
title: Background
parent: CSS
nav_order: 4
---

# CSS Background
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background Properties

### Background 

**Shorthand**

**background: color image repeat attachment position 순서로 진행**

```css
body {
  background: #ffffff url("img_tree.png") no-repeat right top;
}
```

### background-color

**배경 색상 지정**

```css
body {
    background-color: red;
}
```
    
### background-image
    
**배경 이미지 지정**

&#9656; 하나 이상의 이미지를 사용할 수 있음

&#9656; 제일 먼저 선언한 이미지가 제일 앞에 나옴

```css
body {
  background-image: url("paper.gif");
}

/*2개 이상의 이미지 겹쳐서 사용하기*/
body {
    background-image: url(img_flwr.gif), url(paper.gif);
    background-position: right bottom, left top;
    background-repeat: no-repeat, repeat;
}

or

#example1 {
  background: url(img_flwr.gif) right bottom no-repeat, url(paper.gif) left top repeat;
}
```

### background-repeat

**배경 반복하기**

* repeat : 기본값

* repeat-x : 수평 반복(가로로 길어짐), horizontally

* repeat-y : 수직 반복(세로로 길어짐), vertically

* no-repeat : 한번만 출력

```css
background-repeat: repeat   
background-repeat: repeat-x   
background-repeat: repeat-y   
background-repeat: no-repeat 
```
    
### background-attachment

**배경의 고정 유무**

* fixed : 고정됨, 스크롤 영향 X

* scroll : 고정안됨, 스크롤 영향 O

```css
background-attachment: fixed   
background-attachment: scroll  
```

### background-position 

**배경 이미지의 위치**

좌 / 우 방향으로 움직임, **left center right/ top center bottom**

```css
body {
  background-image: url("img_tree.png");
  background-repeat: no-repeat;
  background-position: right top;
}
```

### background-size 

**배경 이미지의 크기를 지정**

* contain : 배경이 비율에 맞춰 꼭 콘텐츠 내부에 들어가야 하는것, 컨텐츠 배경이 보일 수 있음

* cover : 콘텐츠 내부에 꽉차게 하는것, 배경이 잘릴수도 있음

&#9656; 여러 배경 이미지를 동시에 정의할 수 있음

```css
background-size: px px; or %   // 이미지를 작거나 크게 만들 때 
background-size: contain
background-size: cover         // entire element is always covered

/*동시에 정의하기*/
#example1 {
  background: url(img_tree.gif) left top no-repeat, url(img_flwr.gif) right bottom no-repeat, url(paper.gif) left top repeat;
  background-size: 50px, 130px, auto;
}
```

### background-clip

**배경의 부분을 색칠하기**

* border-box : painted to the outside edge of the border (default)

* padding-box : painted to the outside edge of the padding

* content-box : painted within the content box

```css
background-clip: border-box;
background-clip: padding-box;
background-clip: content-box;
```

<span class="fs-2">
[W3C Example](https://www.w3schools.com/css/tryit.asp?filename=trycss3_background-clip){: .btn  .btn-outline .mt-2}
</span>
    
### background-origin

**배경 이미지가 어디에 위치할 것인지**

* border-box : the background image starts from the upper left corner of the border

* padding-box : the background image starts from the upper left corner of the padding edge (default)

* content-box : the background image starts from the upper left corner of the content

```css
background-origin: border-box;
background-origin: padding-box;
background-origin: content-box;
```

<span class="fs-2">
[W3C Exmaple](https://www.w3schools.com/css/tryit.asp?filename=trycss3_background-origin){: .btn  .btn-outline .mt-2}
</span>

---

## Background Decoration  

### Linear Gradients

**goes down/up/left/right/diagonally 으로 가는 그라데이션**

&#9656; background-image 속성을 사용해서 지정함

&#9656; 최소한 2개의 색상을 지정해야함

&#9656; 시작지점이나 각도를 조정할 수 있음 (top to bottom is default)

Syntax
{: .label .mt-3}
<div class="code-example" markdown="1">
background-image: linear-gradient(direction, color-stop1, color-stop2, ...);

or

background-image: linear-gradient(angle, color-stop1, color-stop2);
</div>

예제
{: .label .label-purple .mt-2}

* Top to Botoom

  <div class="code-example" markdown="1">
  <div style="width:300px;height:100px;background-image:linear-gradient(red,yellow);"></div>
  </div>
  ```css
  #grad {
    background-image: linear-gradient(red, yellow);
  }
  ```

* Left to Right

  <div class="code-example" markdown="1">
  <div style="width:300px;height:100px;background-image:linear-gradient(to right,red,yellow);"></div>
  </div>
  ```css
  #grad {
    background-image: linear-gradient(to right, red , yellow);
  }
  ```
    
* Diagonal

  <div class="code-example" markdown="1">
  <div style="width:300px;height:100px;background-image:linear-gradient(to bottom right,red,yellow);"></div>
  </div>
  ```css
  #grad {
    background-image: linear-gradient(to bottom right, red, yellow);
  }    
  ```
    
* Angles

  <div class="code-example" markdown="1">
  <div style="width:300px;height:100px;background-image:linear-gradient(-90deg,red,yellow);"></div>
  </div>
  ```css
  #grad {
    background-image: linear-gradient(-90deg, red, yellow);
  }
  ```    
* Multiple Color Stops

  <div class="code-example" markdown="1">
  <div style="width:300px;height:100px;background-image:linear-gradient(red,yellow,green);"></div>
  <br>
  <div style="width:300px;height:100px;background-image:linear-gradient(to right,red,orange,yellow,green,blue,indigo,violet);"></div>
  </div>
  ```css
  #grad {
    background-image: linear-gradient(red, yellow, green);
  }

  #grad {
    background-image: linear-gradient(to right, red,orange,yellow,green,blue,indigo,violet);
  }
  ```   

* Transparency

  <div class="code-example" markdown="1">
  <div style="width:300px;height:100px;background-image:linear-gradient(to right, rgba(255,0,0,0), rgba(255,0,0,1));"></div>
  </div>
  ```css
  #grad {
    background-image: linear-gradient(to right, rgba(255,0,0,0), rgba(255,0,0,1));
  }
  ```
    
* Repeating a linear-gradient

  <div class="code-example" markdown="1">
  <div style="width:300px;height:100px;background-image:repeating-linear-gradient(red, yellow 10%, green 20%);"></div>
  </div>
  ```css
  #grad {
    background-image: repeating-linear-gradient(red, yellow 10%, green 20%);
  }
  ```
    
### Radial Gradients

**가운데에서 시작하는 그라데이션**

최소한 2개이상 색상을 지정해야함

Syntax
{: .label .mt-3}
<div class="code-example" markdown="1">
background-image: radial-gradient(shape size at position, start-color, ..., last-color);
</div>

예제
{: .label .label-purple .mt-2}

* Evenly Spaced Color Stops

    default
    
    <div class="code-example" markdown="1">
    <div style="width:300px;height:100px;background-image:radial-gradient(red, yellow, green);"></div>
    </div>
    ```css
    #grad {
      background-image: radial-gradient(red, yellow, green);
    }
    ```
    
* Differently Spaced Color Stops

    <div class="code-example" markdown="1">
    <div style="width:300px;height:100px;background-image:radial-gradient(red 5%, yellow 15%, green 60%);"></div>
    </div>
    ```css
    #grad {
      background-image: radial-gradient(red 5%, yellow 15%, green 60%);
    }
    ```
    
* Circle Shape

    완벽한 원형의 그라데이션, 기본은 ellipse(타원형)
    
    <div class="code-example" markdown="1">
    <div style="width:300px;height:100px;background-image:radial-gradient(circle, red, yellow, green);"></div>
    </div>
    ```css
    #grad {
      background-image: radial-gradient(circle, red, yellow, green);
    }
    ```
    
* Repeating a radial-gradient
    
    <div class="code-example" markdown="1">
    <div style="width:300px;height:100px;background-image:repeating-radial-gradient(red, yellow 10%, green 15%);"></div>
    </div>
    ```css
    #grad {
      background-image: repeating-radial-gradient(red, yellow 10%, green 15%);
    }
    ```

#### Web Gradient Generator Site

<span class="fs-2">
[Ultimate CSS Gradient Generator](https://www.colorzilla.com/gradient-editor/){: .btn  .btn-outline .mt-2}
</span>

<span class="fs-2">
[CSS matic Gradient Generator](https://www.cssmatic.com/gradient-generator#'\-moz\-linear\-gradient\%28left\%2C\%20rgba\%28248\%2C80\%2C50\%2C1\%29\%200\%25\%2C\%20rgba\%28241\%2C111\%2C92\%2C1\%29\%2050\%25\%2C\%20rgba\%28246\%2C41\%2C12\%2C1\%29\%2051\%25\%2C\%20rgba\%28240\%2C47\%2C23\%2C1\%29\%2071\%25\%2C\%20rgba\%28231\%2C56\%2C39\%2C1\%29\%20100\%25\%29\%3B'){: .btn  .btn-outline}
</span>

###  Full Size Background Image

```css
html {
  background: url(img_man.jpg) no-repeat center fixed;
  background-size: cover;
}
```

---

## Similar property

### Opacity 

**투명도**

&#9656; 0 완전투명 - 1 완전 불투명

```css
opacity: 0.3
```

!Note
{: .label .label-yellow .mt-3}
<div class="code-example" markdown="1">
부모 객체에 투명도 줄 경우 자식들까지 투명해짐, 대안책으로 RGBA 사용
</div>
