# anime.js API Reference

This document provides a comprehensive reference for the public API of anime.js, a lightweight JavaScript animation library.

## Table of Contents

1. [Core Function](#core-function)
2. [Animation Parameters](#animation-parameters)
3. [Targets](#targets)
4. [Animation Properties](#animation-properties)
5. [Property Parameters](#property-parameters)
6. [Animation Controls](#animation-controls)
7. [Callbacks and Promises](#callbacks-and-promises)
8. [SVG Animations](#svg-animations)
9. [Easing Functions](#easing-functions)
10. [Helpers](#helpers)

## Core Function

### anime(params)

The main function to create an animation instance.

```javascript
const animation = anime({
  targets: '.element',
  translateX: 250,
  rotate: '1turn',
  duration: 800,
  easing: 'easeInOutQuad'
});
```

## Animation Parameters

- `targets`: Element(s) to animate. Can be a CSS selector, DOM node, or an array.
- `duration`: Animation duration in milliseconds. Default: 1000.
- `delay`: Delay before starting the animation in milliseconds. Default: 0.
- `endDelay`: Delay after the animation ends in milliseconds. Default: 0.
- `easing`: Easing function. Default: 'easeOutElastic(1, .5)'.
- `round`: Rounds values to the nearest integer. Default: 0 (disabled).
- `loop`: Number of times to loop the animation. Default: 1. Use `true` for infinite loops.
- `direction`: Animation direction. Can be 'normal', 'reverse', or 'alternate'.
- `autoplay`: Whether to start the animation immediately. Default: true.

## Targets

Targets can be specified in various ways:

- CSS Selectors: `'.element'`, `'#id'`
- DOM Nodes: `document.querySelector('.element')`
- JavaScript Objects: `{prop1: value1, prop2: value2}`
- Arrays: `['.el1', '.el2']`, `[obj1, obj2]`

## Animation Properties

anime.js can animate various properties:

- CSS properties: `opacity`, `backgroundColor`, `fontSize`, etc.
- Transforms: `translateX`, `rotate`, `scale`, etc.
- Object properties: `prop1`, `prop2`, etc.
- SVG attributes: `fillOpacity`, `strokeDashoffset`, etc.

## Property Parameters

Properties can have additional parameters:

```javascript
anime({
  targets: '.element',
  translateX: {
    value: 250,
    duration: 800,
    easing: 'easeInOutQuad'
  },
  rotate: {
    value: '1turn',
    duration: 1800,
    easing: 'easeInOutSine'
  },
  scale: {
    value: 2,
    duration: 1600,
    delay: 800,
    easing: 'easeInOutQuart'
  }
});
```

## Animation Controls

- `play()`: Starts or resumes the animation.
- `pause()`: Pauses the animation.
- `restart()`: Restarts the animation from the beginning.
- `reverse()`: Reverses the animation direction.
- `seek(time)`: Moves the animation to a specific time (in milliseconds).
- `remove(targets)`: Removes one or more targets from the animation.

```javascript
const animation = anime({
  targets: '.element',
  translateX: 250,
  autoplay: false
});

animation.play();
animation.pause();
animation.restart();
animation.reverse();
animation.seek(500);
animation.remove('.element');
```

## Callbacks and Promises

anime.js provides several callback functions and returns a Promise:

- `update`: Called at every frame of the animation.
- `begin`: Called when the animation begins.
- `complete`: Called when the animation completes.
- `loopBegin`: Called at the beginning of each loop.
- `loopComplete`: Called at the end of each loop.
- `changeBegin`: Called when the animation enters an active period.
- `changeComplete`: Called when the animation enters an inactive period.

```javascript
const animation = anime({
  targets: '.element',
  translateX: 250,
  update: function(anim) {
    console.log('progress: ' + Math.round(anim.progress) + '%');
  },
  complete: function(anim) {
    console.log('animation completed');
  }
});

animation.finished.then(() => {
  console.log('animation finished promise resolved');
});
```

## SVG Animations

anime.js provides special functions for SVG animations:

- `anime.setDashoffset(el)`: Sets the dash offset for line drawing animations.
- `anime.path(path)`: Creates a path function for motion path animations.

```javascript
const path = anime.path('.motion-path-demo path');

anime({
  targets: '.square',
  translateX: path('x'),
  translateY: path('y'),
  rotate: path('angle'),
  easing: 'linear',
  duration: 2000,
  loop: true
});
```

## Easing Functions

anime.js includes various easing functions and allows custom easing:

- Built-in functions: `linear`, `easeInOutQuad`, `easeInOutCubic`, etc.
- Custom functions: `cubicBezier(x1, y1, x2, y2)`, `spring(mass, stiffness, damping, velocity)`
- Elasticity: `easeOutElastic(amplitude, period)`

```javascript
anime({
  targets: '.element',
  translateX: 250,
  easing: 'easeOutElastic(1, .8)'
});
```

## Helpers

- `anime.random(min, max)`: Generates a random number between min and max.
- `anime.stagger(value, options)`: Creates staggered timing for multiple elements.
- `anime.morphPath(pathFrom, pathTo, options)`: Generates a function for path morphing animations.

```javascript
anime({
  targets: '.stagger-demo div',
  translateX: 250,
  delay: anime.stagger(100, {start: 500})
});

// Path morphing example
const morphPath = anime.morphPath('#pathFrom', '#pathTo');

anime({
  targets: '#morphedPath',
  d: morphPath,
  duration: 2000,
  easing: 'easeInOutQuad',
  loop: true,
  direction: 'alternate'
});
```

This API reference covers the main features and functions of anime.js. For more detailed information and advanced usage, please refer to the official documentation and examples.