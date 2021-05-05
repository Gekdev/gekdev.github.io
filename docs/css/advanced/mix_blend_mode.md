---
layout: default
title: Mix Blend Mode
parent: Advanced
grand_parent: CSS
nav_order: 9
---

# Mix Blend Mode
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## CSS Mix Blend Mode

### Syntax

```css
mix-blend-mode: ;
```

### Blending with parents

* multiply

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: multiply;" src="http://gekdev.github.io/assets/images/100.png" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: multiply;" src="http://placehold.it/100" alt="">
    </div>
    ```

* hue

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: hue;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: hue;" src="http://placehold.it/100" alt="">
    </div>
    ```

* lighten

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: lighten;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: lighten;" src="http://placehold.it/100" alt="">
    </div>
    ```

* luminosity

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: luminosity;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: luminosity;" src="http://placehold.it/100" alt="">
    </div>
    ```

* normal

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: normal;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: normal;" src="http://placehold.it/100" alt="">
    </div>
    ```

* overlay

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: overlay;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: overlay;" src="http://placehold.it/100" alt="">
    </div>
    ```

* saturation

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: saturation;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: saturation;" src="http://placehold.it/100" alt="">
    </div>
    ```

* screen

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: screen;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: screen;" src="http://placehold.it/100" alt="">
    </div>
    ```

* soft-light

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: soft-light;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: soft-light;" src="http://placehold.it/100" alt="">
    </div>
    ```

* inherit

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: inherit;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: inherit;" src="http://placehold.it/100" alt="">
    </div>
    ```

* initial

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: initial;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: initial;" src="http://placehold.it/100" alt="">
    </div>
    ```

* unset

    <div class="code-example" markdown="1">
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: unset;" src="http://placehold.it/100" alt="">
    </div>
    </div>
    ```html
    <div style="background-color: greenyellow; width: 120px;">
        <img style="mix-blend-mode: unset;" src="http://placehold.it/100" alt="">
    </div>
    ```

### Blending with siblings

<div class="code-example" markdown="1">
<img src="https://gekdev.github.io/assets/images/blend_with_sib.jpg" alt="">
</div>
```css
<div class="box2">
        <img class="img14" src="http://placehold.it/100" alt="">
        <div class="blend"></div>
</div>

...

.box2{
    position: relative;
    width: 120px;
    height: 100px;
}

.blend{
    position: absolute;
    width: 100%;
    height: 50px;
    background-color: lightcoral;
    mix-blend-mode: soft-light;
}

.img14{
    position: absolute;
}
```

### Blending two images

<div class="code-example" markdown="1">
<img src="https://gekdev.github.io/assets/images/blend_two_imgs.jpg" alt="">
</div>
```css
<div class="box3">
        <div class="blend1"></div>
        <div class="blend2"></div>
</div>

...

.box3{
    position: relative;
    width: 120px;
    height: 100px;
}

.blend1{
    width: 100px;
    height: 100px;
    position: absolute;
    background-color: lightgreen
}

.blend2{
    width: 100px;
    height: 100px;
    position: absolute;
    margin-left:20px;
    background-color: lightsalmon;
    mix-blend-mode:overlay
}
```
