# Troubleshooting Guide for anime.js

This guide addresses common issues users might encounter when working with anime.js and provides solutions and workarounds.

## Table of Contents
1. [Animation Not Starting](#animation-not-starting)
2. [Unexpected Animation Behavior](#unexpected-animation-behavior)
3. [Performance Issues](#performance-issues)
4. [Browser Compatibility](#browser-compatibility)
5. [Timeline Issues](#timeline-issues)

## Animation Not Starting

### Problem: Animation doesn't play when created
**Possible Cause:** The `autoplay` option is set to `false` or not specified.

**Solution:** Ensure that `autoplay` is set to `true` in your animation options, or manually start the animation using the `play()` method.

```javascript
// Option 1: Set autoplay to true
const animation = anime({
  targets: '.element',
  translateX: 250,
  autoplay: true
});

// Option 2: Manually start the animation
const animation = anime({
  targets: '.element',
  translateX: 250
});
animation.play();
```

### Problem: Animation doesn't affect the target elements
**Possible Cause:** Incorrect selector or non-existent elements.

**Solution:** Double-check your selector and ensure the target elements exist in the DOM when the animation is created.

```javascript
// Make sure the element with class 'element' exists
const animation = anime({
  targets: '.element',
  translateX: 250
});
```

## Unexpected Animation Behavior

### Problem: Animation values are not as expected
**Possible Cause:** Unit mismatch or incorrect value type.

**Solution:** Ensure you're using the correct units and value types for properties.

```javascript
// Correct usage of units
const animation = anime({
  targets: '.element',
  translateX: '250px', // Use quotes for pixel values
  rotate: '1turn',    // Use quotes for turn values
  scale: 1.5          // No quotes for unitless values
});
```

### Problem: Easing function not working as expected
**Possible Cause:** Incorrect easing function name or parameters.

**Solution:** Verify the easing function name and parameters.

```javascript
// Correct usage of easing functions
const animation = anime({
  targets: '.element',
  translateX: 250,
  easing: 'easeOutElastic(1, .5)' // Correct syntax for parameterized easing
});
```

## Performance Issues

### Problem: Animations are sluggish or causing high CPU usage
**Possible Cause:** Too many simultaneous animations or complex property changes.

**Solution:** Optimize your animations by reducing the number of animated elements or simplifying the animated properties.

```javascript
// Optimize by animating transforms instead of position properties
const animation = anime({
  targets: '.element',
  translateX: 250, // Use translateX instead of left
  scale: 1.2,      // Use scale instead of width and height
  duration: 1000
});
```

## Browser Compatibility

### Problem: Animations not working in specific browsers
**Possible Cause:** Use of unsupported features in older browsers.

**Solution:** Check the browser support table in the anime.js documentation and use appropriate fallbacks or polyfills for unsupported features.

```javascript
// Example of providing a fallback for older browsers
const animation = anime({
  targets: '.element',
  translateX: 250,
  rotate: anime.random(0, 360), // Use anime.random instead of Math.random for better compatibility
});
```

## Timeline Issues

### Problem: Animations in a timeline not playing in the expected order
**Possible Cause:** Incorrect use of timelineOffset or misunderstanding of how timelines work.

**Solution:** Review your timeline setup and ensure you're using timelineOffset correctly.

```javascript
// Correct usage of timeline
const timeline = anime.timeline({
  duration: 1000,
  easing: 'easeOutElastic(1, .5)'
});

timeline
  .add({
    targets: '.element1',
    translateX: 250
  })
  .add({
    targets: '.element2',
    translateX: 250
  }, '+=500'); // Starts 500ms after the previous animation ends
```

Remember, if you encounter issues not covered in this guide, refer to the official anime.js documentation or seek help from the community forums.