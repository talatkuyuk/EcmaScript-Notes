# Object Literal Shorthand

### Object literal shorthand <a id="object-literal-shorthand"></a>

A recurring trend in ES6 is to remove unnecessary repetition in your code. By removing unnecessary repetition, your code becomes easier to read and more concise. This trend continues with the introduction of new _shorthand_ ways for initializing objects and adding methods to objects.

We can remove the duplicate variables names from object properties _if_ the properties have **the same name as the variables being assigned to them.**

```javascript
let type = 'quartz';
let color = 'rose';
let carat = 21.29;

// OPTION-1 classic object composition
const gemstone = {
  type: type,
  color: color,
  carat: carat
};

// OPTION-2 with object literal shorthand
const gemstone = {
  type,
  color,
  carat
};
```

### Shorthand method names <a id="shorthand-method-names"></a>

Since there is only need to reference the building’s `calculateArea` property in order to call the function, having the function keyword is redundant, so it can be dropped.

```javascript
let type = 'home';

const building = {
  type,
  calculateArea: function() {
    // will calculate area of the building based on its type. 
  }
};

// With Shorthand method name
cconst building = {
  type,
  calculateArea() {
    // will calculate area of the building based on its type. 
  }
};
```

