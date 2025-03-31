# Performance Tips for anime.js

This guide provides performance tips and best practices for using anime.js effectively, especially when animating large numbers of elements or creating complex animations.

## Table of Contents

1. [Efficient DOM Manipulation](#efficient-dom-manipulation)
2. [Optimizing Animation Properties](#optimizing-animation-properties)
3. [Batching Animations](#batching-animations)
4. [Using requestAnimationFrame](#using-requestanimationframe)
5. [Leveraging Hardware Acceleration](#leveraging-hardware-acceleration)
6. [Reducing JavaScript Calculations](#reducing-javascript-calculations)
7. [Optimizing for Mobile Devices](#optimizing-for-mobile-devices)

## Efficient DOM Manipulation

When animating large numbers of elements, efficient DOM manipulation is crucial for performance:

- Use `document.querySelectorAll()` or `document.getElementsByClassName()` instead of jQuery selectors.
- Cache DOM elements that you'll be animating frequently.
- Consider using a virtual DOM library for complex, frequently updating UIs.

Example:

```javascript
// Inefficient
anime({
  targets: '.element',
  translateX: 250
});

// More efficient
const elements = document.querySelectorAll('.element');
anime({
  targets: elements,
  translateX: 250
});
```

## Optimizing Animation Properties

Choose animation properties wisely to ensure smooth performance:

- Prefer `transform` and `opacity` for animations, as they are GPU-accelerated.
- Avoid animating layout properties like `width`, `height`, or `position` when possible.
- Use `will-change` to hint at properties that will be animated.

Example:

```javascript
// Less performant
anime({
  targets: '.element',
  left: '250px',
  top: '100px'
});

// More performant
anime({
  targets: '.element',
  translateX: 250,
  translateY: 100
});
```

## Batching Animations

When animating multiple elements, batch them together in a single anime.js instance:

- Use the `targets` property to select multiple elements.
- Utilize the `anime.stagger()` function for creating offset animations.

Example:

```javascript
// Inefficient
elements.forEach((el, i) => {
  anime({
    targets: el,
    translateX: 100,
    delay: i * 100
  });
});

// More efficient
anime({
  targets: elements,
  translateX: 100,
  delay: anime.stagger(100)
});
```

## Using requestAnimationFrame

anime.js uses `requestAnimationFrame` internally, but you can optimize your code further:

- Use `requestAnimationFrame` for any custom animation logic outside of anime.js.
- Avoid using `setInterval` or `setTimeout` for animation-related tasks.

Example:

```javascript
function update() {
  // Custom animation logic here
  requestAnimationFrame(update);
}

requestAnimationFrame(update);
```

## Leveraging Hardware Acceleration

Take advantage of hardware acceleration to improve performance:

- Use 3D transforms (e.g., `translateZ(0)`) to trigger GPU acceleration.
- Be cautious with excessive use of shadows, gradients, or filters, as they can impact performance.

Example:

```javascript
anime({
  targets: '.element',
  translateX: 250,
  translateY: 50,
  translateZ: 0 // Triggers hardware acceleration
});
```

## Reducing JavaScript Calculations

Minimize JavaScript calculations during animations:

- Precompute values when possible and store them.
- Use anime.js's built-in functions like `anime.random()` for efficient calculations.
- Avoid complex calculations within animation callbacks.

Example:

```javascript
const randomValues = Array.from({ length: 100 }, () => anime.random(0, 100));

anime({
  targets: '.element',
  translateX: () => randomValues[anime.random(0, randomValues.length - 1)]
});
```

## Optimizing for Mobile Devices

When targeting mobile devices, consider these additional tips:

- Reduce the number of animated elements on screen at once.
- Use simpler easing functions (e.g., 'linear' or 'easeInOutSine' instead of 'easeOutElastic').
- Test on lower-end devices to ensure smooth performance.

Example:

```javascript
const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);

anime({
  targets: '.element',
  translateX: 250,
  duration: isMobile ? 400 : 250,
  easing: isMobile ? 'easeInOutSine' : 'easeOutElastic(1, .5)'
});
```

By following these performance tips, you can create smoother, more efficient animations with anime.js, even when working with large numbers of elements or complex animation sequences.