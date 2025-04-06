# Targets and Selectors in anime.js

anime.js provides flexible options for selecting and targeting elements for animation. This guide covers the various ways you can specify targets in your animations, including DOM selectors, JavaScript objects, and SVG elements.

## DOM Selectors

anime.js supports CSS selectors to target DOM elements. You can use any valid CSS selector string to select elements for animation.

```javascript
anime({
  targets: '.my-class', // Selects all elements with the class 'my-class'
  // ... animation properties
});

anime({
  targets: '#my-id', // Selects the element with the id 'my-id'
  // ... animation properties
});

anime({
  targets: 'div', // Selects all div elements
  // ... animation properties
});
```

## JavaScript Objects and Variables

You can also target JavaScript objects or variables directly. This is useful for animating properties of objects that aren't necessarily DOM elements.

```javascript
const myObject = { prop1: 0, prop2: '100%' };

anime({
  targets: myObject,
  prop1: 100,
  prop2: '0%',
  easing: 'linear',
  update: function() {
    console.log(myObject.prop1, myObject.prop2);
  }
});
```

## NodeList and HTMLCollection

anime.js can handle NodeList and HTMLCollection objects, which are returned by methods like `querySelectorAll()` or properties like `children`.

```javascript
const elements = document.querySelectorAll('.animate-me');

anime({
  targets: elements,
  // ... animation properties
});
```

## SVG Elements

You can target SVG elements just like any other DOM element. Additionally, anime.js provides special features for SVG animations, such as the ability to animate along a path.

```javascript
anime({
  targets: '#my-svg-circle',
  r: ['0%', '100%'],
  easing: 'easeInOutQuad',
  duration: 1000,
});
```

## Arrays of Targets

You can pass an array of mixed target types to animate multiple elements or objects simultaneously.

```javascript
const el1 = document.querySelector('.el1');
const el2 = document.querySelector('.el2');
const obj = { prop: 0 };

anime({
  targets: [el1, el2, obj, '.el3'],
  translateX: 250,
  rotate: '1turn',
  backgroundColor: '#FFF',
  duration: 800
});
```

## Function as Targets

For more complex scenarios, you can use a function that returns the target(s). This function will be called once for each target in the animation.

```javascript
anime({
  targets: function() { return document.querySelectorAll('.element'); },
  translateX: 250,
  rotate: 540
});
```

## Conclusion

anime.js provides a wide range of options for selecting and targeting elements or objects for animation. Whether you're working with DOM elements, JavaScript objects, or SVG, you can easily specify your targets using selectors, direct references, or even functions. This flexibility allows you to create complex and dynamic animations with ease.