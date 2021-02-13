---
description: 'https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills'
---

# Polyfills

A polyfill, or polyfiller, is a piece of code \(or plugin\) that provides the technology that you, the developer, expect the browser to provide natively.

[https://en.wikipedia.org/wiki/Polyfill](https://en.wikipedia.org/wiki/Polyfill)

> A polyfill is just regular JavaScript.

### An example to Polyfill

```javascript
if (!String.prototype.startsWith) {
  String.prototype.startsWith = function (searchString, position) {
    position = position || 0;
    return this.substr(position, searchString.length) === searchString;
  };
}

/* sample usage */
'Udacity'.startsWith('Udac'); // returns `true`
'Udacity'.startsWith('Udac', 2); // returns `false`
'Udacity'.startsWith('ES6'); // returns `false`
```

The `startsWith()` polyfill begins with `if (!String.prototype.startsWith)` in order to avoid overwriting the native one originated from EcmaScript.

### Beyond to Polyfill

JavaScript is the language used to create a polyfill, but a polyfill doesn't just patch up missing JavaScript features! There are polyfills for all sorts of browser features:

* SVG
* Canvas
* Web Storage \(local storage / session storage\)
* Video
* HTML5 elements
* Accessibility
* Web Sockets
* and many more!

[https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills)

