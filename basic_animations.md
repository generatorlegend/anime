# Basic Animations with anime.js

This guide will walk you through creating basic animations using anime.js, covering properties like translation, rotation, and scaling. We'll provide multiple examples with explanations to help you get started with this powerful animation library.

## Table of Contents

1. [Introduction](#introduction)
2. [Setting Up](#setting-up)
3. [Basic Translation Animation](#basic-translation-animation)
4. [Rotation Animation](#rotation-animation)
5. [Scaling Animation](#scaling-animation)
6. [Combining Multiple Properties](#combining-multiple-properties)
7. [Easing and Duration](#easing-and-duration)
8. [Conclusion](#conclusion)

## Introduction

anime.js is a lightweight JavaScript animation library that allows you to create smooth and complex animations with ease. It works with CSS properties, SVG, DOM attributes, and JavaScript Objects, making it versatile for various animation needs.

## Setting Up

Before we start creating animations, make sure you have anime.js included in your project. You can do this by either downloading the library or using a CDN link.

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
```

Or if you're using npm:

```bash
npm install animejs
```

Then import it in your JavaScript file:

```javascript
import anime from 'animejs/lib/anime.es.js';
```

## Basic Translation Animation

Let's start with a simple translation animation that moves an element horizontally.

```javascript
anime({
  targets: '.box',
  translateX: 250,
  duration: 1000,
  easing: 'easeInOutQuad'
});
```

In this example:
- `targets` specifies the element(s) to animate (in this case, elements with the class 'box').
- `translateX` moves the element 250 pixels to the right.
- `duration` sets the animation duration to 1000 milliseconds (1 second).
- `easing` defines how the animation progresses over time.

## Rotation Animation

Now, let's create an animation that rotates an element.

```javascript
anime({
  targets: '.spinner',
  rotate: '1turn',
  duration: 2000,
  easing: 'linear',
  loop: true
});
```

Here's what's happening:
- `rotate` spins the element one full turn (360 degrees).
- `loop: true` makes the animation repeat indefinitely.
- `easing: 'linear'` ensures a constant rotation speed.

## Scaling Animation

Let's create a pulsing effect by scaling an element up and down.

```javascript
anime({
  targets: '.pulse',
  scale: [1, 1.2],
  duration: 800,
  direction: 'alternate',
  easing: 'easeInOutQuad',
  loop: true
});
```

In this animation:
- `scale` array `[1, 1.2]` scales the element from its original size to 1.2 times its size.
- `direction: 'alternate'` makes the animation play forwards then backwards.

## Combining Multiple Properties

anime.js allows you to animate multiple properties simultaneously. Let's combine translation, rotation, and scaling.

```javascript
anime({
  targets: '.multi',
  translateX: 250,
  rotate: '1turn',
  scale: 1.5,
  duration: 1500,
  easing: 'easeInOutExpo'
});
```

This animation will move the element, rotate it, and scale it up all at once.

## Easing and Duration

Easing functions and duration play crucial roles in how your animations feel. Let's explore a few options:

```javascript
anime({
  targets: '.easing-demo',
  translateX: 250,
  duration: 2000,
  easing: 'spring(1, 80, 10, 0)'
});
```

This example uses a spring physics model for easing, creating a bouncy effect. anime.js provides various easing functions, including:

- Linear: `'linear'`
- Ease-in: `'easeInQuad'`, `'easeInCubic'`, `'easeInQuart'`, etc.
- Ease-out: `'easeOutQuad'`, `'easeOutCubic'`, `'easeOutQuart'`, etc.
- Ease-in-out: `'easeInOutQuad'`, `'easeInOutCubic'`, `'easeInOutQuart'`, etc.

Experiment with different easing functions and durations to achieve the desired feel for your animations.

## Conclusion

This guide has covered the basics of creating animations with anime.js, including translation, rotation, scaling, and combining multiple properties. We've also touched on the importance of easing and duration in crafting smooth and engaging animations.

Remember, anime.js is a powerful library with many more features, including keyframes, staggering, and timeline animations. As you become more comfortable with these basics, explore the [official documentation](https://animejs.com/documentation/) to unlock its full potential.

Happy animating!