# Getting Started with Anime.js

Anime.js is a lightweight JavaScript animation library with a simple yet powerful API. It works with CSS properties, SVG, DOM attributes, and JavaScript Objects. This guide will help you get started with Anime.js in your projects.

## Installation

You can install Anime.js using one of the following methods:

### NPM

To install Anime.js via npm, run the following command in your project directory:

```bash
npm install animejs --save
```

### Manual Download

You can also download Anime.js manually from the [GitHub repository](https://github.com/juliangarnier/anime/archive/master.zip).

## Usage

### ES6 Modules

If you're using ES6 modules, you can import Anime.js like this:

```javascript
import anime from 'animejs/lib/anime.es.js';
```

### CommonJS

For CommonJS environments, use the following:

```javascript
const anime = require('animejs');
```

### File Include

If you're not using a module system, you can include Anime.js directly in your HTML file:

```html
<script src="path/to/anime.min.js"></script>
```

## Basic Example

Here's a simple example to get you started with Anime.js:

```javascript
anime({
  targets: 'div',
  translateX: 250,
  rotate: '1turn',
  backgroundColor: '#FFF',
  duration: 800
});
```

This animation will:
- Target all `div` elements
- Translate them 250 pixels along the X-axis
- Rotate them one full turn (360 degrees)
- Change their background color to white
- Complete the animation in 800 milliseconds

## Key Concepts

1. **Targets**: Elements to animate (can be CSS selectors, DOM elements, or JavaScript objects)
2. **Properties**: CSS properties, transforms, or object properties to animate
3. **Parameters**: Control the animation behavior (duration, easing, delay, etc.)

## Further Resources

- [Full Documentation](https://animejs.com/documentation/)
- [Demos and Examples](http://codepen.io/collection/b392d3a52d6abf5b8d9fda4e4cab61ab/)
- [GitHub Repository](https://github.com/juliangarnier/anime)

Start experimenting with Anime.js to create stunning animations for your web projects!