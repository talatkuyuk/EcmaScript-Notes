# Classes

### Class preview in ES6

```javascript
class Dessert {
  constructor(calories = 250) {
    this.calories = calories;
  }
}

class IceCream extends Dessert {
  constructor(flavor, calories, toppings = []) {
    super(calories);
    this.flavor = flavor;
    this.toppings = toppings;
  }
  addTopping(topping) {
    this.toppings.push(topping);
  }
}

const cookie = new Dessert(); // It is just a regular function
```

JavaScript uses **functions** to create objects and links objects together by **prototypal inheritance**.

While ES6 intoduces us **new keywords** like `class`, `super`, `extends`; **JavaScript still uses functions and prototypal inheritance under the hood**. It is cleaner way to write the same functionality. _JavaScript is not class-based language._

### How to create a "class" with ES5

```javascript
function Plane(numEngines) {
  this.numEngines = numEngines;
  this.enginesActive = false;
}

// methods "inherited" by all instances
Plane.prototype.startEngines = function () {
  console.log('starting engines...');
  this.enginesActive = true;
};

var richardsPlane = new Plane(1);
richardsPlane.startEngines();
```

The `Plane` function above is a _constructor function_ that will create new Plane objects. Methods that are "inherited" by each Plane object are placed on the `Plane.prototype` object. Things to note:

* the constructor function is called with the `new` keyword
* the constructor function, by convention, starts with a capital letter
* the constructor function controls the setting of data on the objects that will be created
* "inherited" methods are placed on the constructor function's prototype object

### ES6 Classes <a id="es6-classes"></a>

Here's what that same `Plane` class would look like if it were written using the new `class` syntax:

```javascript
class Plane {
  constructor(numEngines) {
    this.numEngines = numEngines;
    this.enginesActive = false;
  }

  startEngines() {
    console.log('starting engines…');
    this.enginesActive = true;
  }
  
  addEngine() {
    this.numEngines++;
  }
  
  static badWeather(planes) {
    for (plane of planes) {
      plane.enginesActive = false;
    }
  }
  
}

var jamesPlane = new Plane(4);
jamesPlane.startEngines();

typeof Plane; // function
typeof Plane === "function" // true

Plane.badWeather([plane1, plane2, plane3]); // static method

const myplane = Plane(1); // throws an error
// Uncaught TypeError: Class constructor Plane cannot be invoked without 'new'
```

The **constructor method** that exists in a class is used initialize new objects. 

**A class is just a function** in JavaScript. `class` is a mirage over prototypal inheritance.

**There aren't any** _**commas**_ **between the method definitions in the Class.** Commas are not used to separate properties or methods in a Class. If you add them, you'll get a `SyntaxError` of `unexpected token ,`

To add a **static method**, the keyword `static` is placed in front of the method name. That makes `badWeather()` a method that's accessed directly on the `Plane` class.

When creating a **new instance** of a JavaScript class, **the `new` keyword must be used.**

