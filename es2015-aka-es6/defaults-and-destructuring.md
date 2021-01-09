# Defaults and Destructuring

Combining **default function parameters** with **destructuring** is super powerfull.

### Defaults and destructuring arrays

```javascript
function createGrid([width = 5, height = 5]) {
  return `Generates a ${width} x ${height} grid`;
}

createGrid([]); // Generates a 5 x 5 grid
createGrid([2]); // Generates a 2 x 5 grid
createGrid([2, 3]); // Generates a 2 x 3 grid
createGrid([undefined, 3]); // Generates a 5 x 3 grid

createGrid(); // throws an error, it expects an array to be passed to it.
// Uncaught TypeError: Cannot read property 'Symbol(Symbol.iterator)' of undefined

// to prevent this issue, add default parameter to array itself.
function createGrid([width = 5, height = 5] = []) {
  return `Generates a ${width} x ${height} grid`;
}

createGrid(); // Generates a 5 x 5 grid
```



### Defaults and destructuring objects <a id="defaults-and-destructuring-objects"></a>

```javascript
function createSundae({scoops = 1, toppings = ['Hot Fudge']}) {
  const scoopText = scoops === 1 ? 'scoop' : 'scoops';
  return `Your sundae has ${scoops} ${scoopText} with ${toppings.join(' and ')} toppings.`;
}

createSundae({}); 
// Your sundae has 1 scoop with Hot Fudge toppings.

createSundae({scoops: 2}); 
// Your sundae has 2 scoops with Hot Fudge toppings.

createSundae({scoops: 2, toppings: ['Sprinkles']}); 
// Your sundae has 2 scoops with Sprinkles toppings.

createSundae({toppings: ['Cookie Dough']}); 
// Your sundae has 1 scoop with Cookie Dough toppings.

createSundae(); // throws an error
// Uncaught TypeError: Cannot match against 'undefined' or 'null'.


// We can prevent this issue by providing a default object to the function:
function createSundae({scoops = 1, toppings = ['Hot Fudge']} = {}) {
  const scoopText = scoops === 1 ? 'scoop' : 'scoops';
  return `Your sundae has ${scoops} ${scoopText} with ${toppings.join(' and ')} toppings.`;
}

createSundae(); // Your sundae has 1 scoop with Hot Fudge toppings.
```



### Array defaults vs. object defaults <a id="array-defaults-vs-object-defaults"></a>

One benefit of _object defaults_ over _array defaults_ is **how they handle** _**skipped**_ **options.** 

```javascript
function createSundae({scoops = 1, toppings = ['Hot Fudge']} = {}) { … }

// if you want to use the default value for scoops but change the toppings
createSundae({toppings: ['Hot Fudge', 'Sprinkles', 'Caramel']});
```

**Compare** the above example with the same function that **uses array defaults with destructuring**.

```javascript
function createSundae([scoops = 1, toppings = ['Hot Fudge']] = []) { … }

// if you want to use the default value for scoops but change the toppings
createSundae([undefined, ['Hot Fudge', 'Sprinkles', 'Caramel']]);
```

Since **arrays are positionally based**, we have to pass `undefined` to "skip" over the first argument \(and accept the default\) to get to the second argument.

**Unless you've got a strong reason to use array defaults with array destructuring, we recommend going with object defaults with object destructuring!**

