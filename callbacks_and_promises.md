# Callbacks and Promises in anime.js

anime.js provides powerful callback functions and Promise support to help you respond to animation events and chain animations effectively. This guide will walk you through the usage of callbacks and promises in anime.js, enabling you to create more dynamic and interactive animations.

## Callbacks

anime.js offers several callback functions that you can use to execute code at specific points during an animation. These callbacks are:

- `begin`: Fires when the animation begins
- `update`: Fires on every frame of the animation
- `complete`: Fires when the animation completes
- `loopBegin`: Fires when an animation loop begins
- `loopComplete`: Fires when an animation loop completes
- `changeBegin`: Fires when an animation property change begins
- `changeComplete`: Fires when an animation property change completes

### Using Callbacks

To use a callback, simply add it as a property to your anime.js configuration object:

```javascript
anime({
  targets: '.element',
  translateX: 250,
  duration: 1000,
  begin: function(anim) {
    console.log('Animation began');
  },
  complete: function(anim) {
    console.log('Animation completed');
  }
});
```

In this example, the `begin` callback will fire when the animation starts, and the `complete` callback will fire when the animation finishes.

### Accessing Animation Instance in Callbacks

Each callback receives the animation instance as its first argument, allowing you to access and manipulate the animation's properties:

```javascript
anime({
  targets: '.element',
  translateX: 250,
  duration: 1000,
  update: function(anim) {
    console.log('Animation progress: ' + Math.round(anim.progress) + '%');
  }
});
```

This example uses the `update` callback to log the animation's progress on every frame.

## Promises

anime.js returns a Promise when you create an animation, allowing you to chain animations or perform actions after an animation completes using `.then()`.

### Basic Promise Usage

```javascript
const animation = anime({
  targets: '.element',
  translateX: 250,
  duration: 1000
});

animation.finished.then(() => {
  console.log('Animation finished!');
});
```

In this example, the console log will execute after the animation has completed.

### Chaining Animations

You can use Promises to chain multiple animations, ensuring they run in sequence:

```javascript
anime({
  targets: '.element',
  translateX: 250,
  duration: 1000
}).finished.then(() => {
  return anime({
    targets: '.element',
    translateY: 50,
    duration: 1000
  }).finished;
}).then(() => {
  console.log('Both animations completed!');
});
```

This code will first move the element horizontally, then vertically, and finally log a message when both animations are done.

## Combining Callbacks and Promises

You can use both callbacks and Promises in the same animation for more complex control:

```javascript
const animation = anime({
  targets: '.element',
  translateX: 250,
  duration: 1000,
  begin: function(anim) {
    console.log('Animation started');
  },
  complete: function(anim) {
    console.log('Animation completed');
  }
});

animation.finished.then(() => {
  console.log('Now we can start the next animation');
  return anime({
    targets: '.element',
    scale: 1.5,
    duration: 500
  }).finished;
}).then(() => {
  console.log('All animations finished!');
});
```

This example demonstrates how you can use callbacks for immediate feedback during the animation, while using Promises to control the flow of multiple animations.

## Best Practices

1. Use callbacks for immediate feedback or updates during an animation.
2. Use Promises for sequencing animations or performing actions after an animation completes.
3. Keep callback functions concise to avoid performance issues, especially in the `update` callback which fires on every frame.
4. When chaining multiple animations, consider using the `anime.timeline()` feature for more complex sequences.

By mastering callbacks and Promises in anime.js, you can create more sophisticated, interactive, and dynamic animations in your web projects.