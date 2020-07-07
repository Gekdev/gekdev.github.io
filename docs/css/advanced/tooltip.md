---
layout: default
title: Tooltip
parent: Advanced
grand_parent: CSS
nav_order: 2
---

# Tooltip
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## CSS Tooltip
{: .no_toc}

### Basic Tooltip

html의 title 속성과는 다름 // 좀더 CSS적으로 예쁘게 꾸민것

```css
<style>
/* Tooltip container */
.tooltip {
  position: relative;
  display: inline-block;
  border-bottom: 1px dotted black; /* If you want dots under the hoverable text */
}

/* Tooltip text */
.tooltip .tooltiptext {
  visibility: hidden;
  width: 120px;
  background-color: black;
  color: #fff;
  text-align: center;
  padding: 5px 0;
  border-radius: 6px;
 
  /* Position the tooltip text */
  position: absolute;
  z-index: 1;
}

/* Show the tooltip text when you mouse over the tooltip container */
.tooltip:hover .tooltiptext {
  visibility: visible;
}
</style>

<div class="tooltip">Hover over me
  <span class="tooltiptext">Tooltip text</span>
</div>
```

### Positioning Tooltips

* right tooltip

    ```css
    .tooltip .tooltiptext {
      top: -5px;
      left: 105%;
    }
    ```

* left tooltip

    ```css
    .tooltip .tooltiptext {
      top: -5px;
      right: 105%;
    }
    ```
    
* top tooltip

    ```css
    .tooltip .tooltiptext {
      width: 120px;
      bottom: 100%;
      left: 50%;
      margin-left: -60px; /* Use half of the width (120/2 = 60), to center the tooltip */
    }
    ```
    
* bottom tooltip

    ```css
    .tooltip .tooltiptext {
      width: 120px;
      top: 100%;
      left: 50%;
      margin-left: -60px; /* Use half of the width (120/2 = 60), to center the tooltip */
    }
    ```
    
### Tooltip Arrows

border-width나 margin-left 속성으로 화살표를 만듦

* right arrow

```css
.tooltip .tooltiptext::after {
  content: " ";
  position: absolute;
  top: 50%;
  left: 100%; /* To the right of the tooltip */
  margin-top: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: transparent transparent transparent black;
}
```

* left arrow

```css
.tooltip .tooltiptext::after {
  content: " ";
  position: absolute;
  top: 50%;
  right: 100%; /* To the left of the tooltip */
  margin-top: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: transparent black transparent transparent;
}
```

* top arrow

```css
.tooltip .tooltiptext::after {
  content: " ";
  position: absolute;
  bottom: 100%;  /* At the top of the tooltip */
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: transparent transparent black transparent;
}
```

* bottom arrow

```css
.tooltip .tooltiptext::after {
  content: " ";
  position: absolute;
  top: 100%; /* At the bottom of the tooltip */
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: black transparent transparent transparent;
}
```

### Fade In Tootip

**천천히 보이게 할때 사용**

```css
.tooltip .tooltiptext {
  opacity: 0;
  transition: opacity 1s;
}

.tooltip:hover .tooltiptext {
  opacity: 1;
}
```
