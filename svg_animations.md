# SVG Animations with anime.js

This guide explains how to animate SVG elements using anime.js, including techniques for path morphing, line drawing, and manipulating SVG attributes.

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Path Morphing](#path-morphing)
4. [Line Drawing](#line-drawing)
5. [Animating SVG Attributes](#animating-svg-attributes)
6. [Advanced Techniques](#advanced-techniques)

## Introduction

anime.js is a lightweight JavaScript animation library that works great with SVG elements. It provides a simple and powerful API to create complex animations, including those involving SVG paths and attributes.

## Getting Started

To start animating SVG elements with anime.js, first include the library in your project:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
```

## Path Morphing

Path morphing allows you to animate the transition between two different SVG paths. This is useful for creating smooth shape transitions.

Example:

```javascript
anime({
  targets: 'path',
  d: [
    { value: 'M50 50 L150 50 L150 150 L50 150 Z' },
    { value: 'M50 50 L150 50 L100 150 Z' }
  ],
  duration: 2000,
  easing: 'easeInOutQuad',
  loop: true,
  direction: 'alternate'
});
```

This animation morphs a square into a triangle and back.

For more advanced path morphing, you can use the `anime.morphPath()` function:

```javascript
const morphPath = anime.morphPath('#path1', '#path2');

anime({
  targets: '#morphPath',
  d: morphPath,
  duration: 2000,
  easing: 'easeInOutQuad',
  loop: true,
  direction: 'alternate'
});
```

This function takes two path elements as input and returns a function that interpolates between them, allowing for smoother and more complex shape transitions.

## Line Drawing

Line drawing animation creates the effect of a line being drawn on the screen. This is achieved by animating the `stroke-dashoffset` property of an SVG path.

Example:

```javascript
const path = anime.path('path');

anime({
  targets: path,
  strokeDashoffset: [anime.setDashoffset, 0],
  easing: 'easeInOutSine',
  duration: 1500,
  loop: true
});
```

This animation creates a line drawing effect for the specified SVG path.

## Animating SVG Attributes

anime.js allows you to animate various SVG attributes such as `fill`, `stroke`, `opacity`, and more.

Example:

```javascript
anime({
  targets: 'circle',
  r: 50,
  fill: '#FF0000',
  stroke: '#00FF00',
  strokeWidth: 4,
  duration: 1000,
  easing: 'easeInOutExpo'
});
```

This animation changes the radius, fill color, stroke color, and stroke width of a circle element.

## Advanced Techniques

### Staggering SVG Animations

You can create staggered animations for multiple SVG elements using the `stagger` option:

```javascript
anime({
  targets: 'rect',
  translateY: 50,
  opacity: 0.5,
  delay: anime.stagger(100),
  duration: 1000
});
```

This animation applies a staggered effect to multiple rectangle elements.

### Combining Animations

Create complex SVG animations by combining multiple animation properties:

```javascript
anime({
  targets: '#logo path',
  strokeDashoffset: [anime.setDashoffset, 0],
  fill: ['#FFF', '#000'],
  scale: [0.5, 1],
  duration: 2000,
  easing: 'easeInOutQuad',
  direction: 'alternate',
  loop: true
});
```

This example combines line drawing, fill color change, and scaling animations for an SVG logo.

By leveraging these techniques, including the new `anime.morphPath()` function, you can create even more engaging and interactive SVG animations using anime.js. Experiment with different properties, easings, and timings to achieve the desired effects for your project.