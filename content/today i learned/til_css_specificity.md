---
title: "TIL: CSS Selector Specificity"
date: 2022-03-30T00:02:06-03:00
draft: false
tags: ["css"]
---
Today I've read a [post](https://blog.codeminer42.com/codetips2-how-specificity-works-in-css/) from the code miner blog talking about CSS specificity.
CSS Selector Specificity It's a way of avoiding the use of `!import` directive and it's quite simple:

Suppose that you have a CSS like this:

```css
div {
    background-color: white;
}

#box {
    background-color: red;
}

.box {
    background-color: black;
}
```

and this css code is applied to a HTML like this:

```html
<div id="box" class=".box">
```

##### The question is: "What will be the background color of that div?

The answer is the result of specificity calculation and it's like this:

| !important | style attributes | id  | Class, Attribute selector, pseudo-classes | Tag, pseudo-elements |
|------------|:----------------:|-----|:------------------------------------------|:---------------------|
| !import    |                  | #id |       .class,[type="input"],:hover        |   h1, ::before       |


The table of points will be:

| selector	| !important | style attributes | id  |Class, Attribute selector, pseudo-classes | Type, pseudo-elements |
|-----------|------------|------------------|-----|------------------------------------------|-----------------------|
|    div    |     0      |        0         |  0  |                    0                     |           1           |
|    #box	|     0      |        0         |  1  |                    0                     |           0           |
|    .box  	|     0      |        0         |  0  |                    1                     |           0           |


The biggest value we got is **#box**, which is **00100**. And the background color will be <span style="color: red">red!</span>

More examples can be found on the original post: [https://blog.codeminer42.com/codetips2-how-specificity-works-in-css/](https://blog.codeminer42.com/codetips2-how-specificity-works-in-css/)

