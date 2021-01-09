# This keyword in Arrow functions

`This` keyword holds _a dynamic value_ that is different depending on:

* how a function is called **in regular functions**.
* where that function is located in the code **in arrow functions**.

### "This" and Regular Functions

#### 1. A new object <a id="1-a-new-object"></a>

If the function is called with `new`: the value of **`this`** inside the `Sundae` constructor function **is** **a new object** because it was called with `new`.

```javascript
const mySundae = new Sundae('Chocolate', ['Sprinkles', 'Hot Fudge']); 
```

#### 2. A specified object <a id="2-a-specified-object"></a>

If the function is invoked with `call`/`apply`: the value of **`this`** inside `printName()` **will refer to `obj2`** since the first parameter of `call()` is to explicitly set what `this` refers to.

```javascript
const result = obj1.printName.call(obj2);
```

#### 3. A context object <a id="3-a-context-object"></a>

If the function is a method of an object: the value of **`this`** inside `teleport()` **will refer to `data`**.

```text
data.teleport();
```

#### 4. The global object or undefined <a id="4-the-global-object-or-undefined"></a>

If the function is called with no context: the value of **`this`** inside `teleport()` **is either the global object or, if in strict mode, it's `undefined`.**

```text
teleport();
```



### "This" and Arrow Functions

With arrow functions, the value of `this` is based on _the function's surrounding context_. In other words, the value of `this` _inside_ an arrow function is the same as the value of `this` _outside_ the function. _Arrow functions inherit their `this` value from their surrounding context._

\*\*\*\*

**Example with `this` in regular function.** The function passed to `setTimeout()` is called without `new`, without `call()`, without `apply()`, and without a context object. That means the value of `this` inside the function is the **global object** and **NOT** the `dessert` object. 

```javascript
// constructor
function IceCream() {
  this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = function() {
  setTimeout(function() {
    this.scoops++; // this refers to global object.
    // a new scoops variable was created (with a default value of undefined) 
    // and was then incremented (undefined + 1 results in NaN)
    console.log('scoop added!');
  }, 500);
};

const dessert = new IceCream(); // new object is created with default value 0
dessert.addScoop(); // scoop added!
console.log(dessert.scoops); // 0
console.log(scoops); // NaN
```

\*\*\*\*

**One way around this is to use closure:** instead of using `this` inside the function, it sets the `cone` variable to `this` and then looks up the `cone` variable when the function is called. This works because it's using the value of the `this` outside the function.

```javascript
// constructor
function IceCream() {
  this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = function() {
  const cone = this; // sets `this` to the `cone` variable
  setTimeout(function() {
    cone.scoops++; // references the `cone` variable
    console.log('scoop added!');
  }, 0.5);
};

const dessert = new IceCream();
dessert.addScoop(); // scoop added!
console.log(dessert.scoops); // 1
```

\*\*\*\*

**Let's replace the function passed to `setTimeout()`with an arrow function:** Since arrow functions inherit their `this` value from the surrounding context, this code works! Since an arrow function is passed to `setTimeout()`, it's using its surrounding context to determine what `this` refers to inside itself. So since `this` _outside_ of the arrow function refers to `dessert`, the value of `this` _inside_ the arrow function will also refer to `dessert`.

```javascript
// constructor
function IceCream() {
  this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = function() {
  setTimeout(() => { // an arrow function is passed to setTimeout
    this.scoops++;
    console.log('scoop added!');
  }, 0.5);
};

const dessert = new IceCream();
dessert.addScoop(); // scoop added!
console.log(dessert.scoops); // 1
```

\*\*\*\*

**If we changed the `addScoop()` method also to an arrow function?**  It doesn't work. _Arrow functions inherit their `this` value from their surrounding context._ Outside of the `addScoop()` method, the value of `this` is the global object. So if `addScoop()` is an arrow function, the value of `this` _inside_ `addScoop()` is the global object. Which then makes the value of `this` in the function passed to `setTimeout()` also set to the global object!

```javascript
// constructor
function IceCream() {
    this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = () => { // addScoop is now an arrow function
  setTimeout(() => {
    this.scoops++;
    console.log('scoop added!');
  }, 0.5);
};

const dessert = new IceCream();
dessert.addScoop(); // scoop added!
console.log(dessert.scoops); // 0
console.log(scoops); // NaN
```



