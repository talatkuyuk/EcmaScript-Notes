# Sets

A **set** is a collection of **distinct items** in mathematics. For example, `{2, 4, 5, 6}` is a set because each number is unique and appears only once. However, `{1, 1, 2, 4}` is _not_ a set because it _contains duplicate entries_.

In JavaScript, **arrays** _do not enforce items to be unique_.

In ES6, there’s a new built-in object that behaves like a mathematical set and works similarly to an array. This new object is conveniently called a "Set". 

The biggest differences between a set and an array are:

* Sets are not indexed-based - you do not refer to items in a set based on their position in the set
* items in a Set can’t be accessed individually

Basically, a Set is an object that lets you store unique items. You can add items to a Set, remove items from a Set, and loop over a Set. These items can be either primitive values or objects.

### How to Create a Set <a id="how-to-create-a-set"></a>

```javascript
const games = new Set(); // creates an empty Set games with no items.
console.log(games); // Set {}

const games = new Set(['Super Mario', 'Banjo-Kazooie', 'Super Mario']);
console.log(games); // Set {'Super Mario', 'Banjo-Kazooie'}
```

If you want to create a Set from a list of values, you use an array: Set removes the duplicate entry.

### Modifying and Working with Sets <a id="modifying-sets"></a>

Properties of Set: `.size` 

Methods of Set, `.add()`   `.delete()`   `.clear()`   `.has()`   `.values()`   `.keys()` 

```javascript
const names = new Set(['John', 'Katie', 'Mario', 'Katie']);

names.add('Tool');
names.add('More');
names.delete('Mario');

console.log(names); // Set {'John', 'Katie', 'Tool', 'More'}
console.log(names.size); // 4
console.log(names.has('John')); // true

games.clear()
console.log(games); // Set {}
console.log(names.size); // 0
console.log(names.has('John')); // false
```

Attempting to `.add()` a duplicate item to a Set won’t give an error, but the item will not be added. `.add()` returns the `Set` if an item is successfully added.

Attempting to `.delete()` an item that is not in a Set, won’t give an error. The Set will remain unchanged. `.delete()` returns a Boolean \(`true` or `false`\) depending on successful deletion.

if you want to delete all the items from a Set, you can use the `.clear()` method.

Use the `.has()` method to check if an item exists in a Set. If the item is in the Set, then `.has()` will return `true`. If the item doesn’t exist in the Set, then `.has()` will return `false`.

Sets can’t be accessed by their index like an array, so you use the `.size` property instead of `.length` property to get the size of the Set.

### Retrieving All Values

The `.values()` method returns the values in a Set which is a `SetIterator` object. In other words, it returns a new iterator object that yields the **values** for each element in the `Set` object in insertion order. 

The `.keys()` method will behave the exact same way as the `.values()` method. The `.keys()` method is an alias for the `.values()`method.

The `.entries()` method returns a new iterator object that contains **an array of `[value, value]`** for each element in the `Set` object, in insertion order. This is similar to the `Map` object, so that each entry's _key_ is the same as its _value_ for a `Set`.

```javascript
console.log(months.values());
// SetIterator {'January', 'February', 'March', 'April', 'May', 'June', 
// 'July', 'August', 'September', 'October', 'November', 'December'}

console.log(months.entries());
// 

```

### Iterating Sets

🧰 We can use the **Set’s default iterator** to step through each item in a Set, one by one.

Because the `.values()` method returns a new iterator object \(called `SetIterator`\), we can store that iterator object in a variable and loop through each item in the Set using `.next()`.  until `done` equals `true` which marks the end of the Set.

```javascript
const iterator = months.values();
iterator.next(); // Object {value: 'January', done: false}
iterator.next(); // Object {value: 'February', done: false}
```

🧰 We can use the new **`for...of` loop** to loop through each item in a Set.

An easier method to loop through the items in a Set is the `for...of` loop.

```javascript
const colors = new Set(['red', 'orange', 'yellow', 'green', 'blue']);
for (const color of colors) console.log(color);
for (let color of colors.keys()) console.log(color);
for (let item of colors.values()) console.log(item);
for (let [key, value] of colors.entries()) console.log(key);
```

### forEach Method

The `.forEach(callbackFn[, thisArg])` method calls `callbackFn` once for each value present in the `Set` object, in insertion order. If a `thisArg` parameter is provided, it will be used as the `this` value for each invocation of `callbackFn`. The callback function is provided with three parameters as follows:

* the _element key_
* the _element value_
* the _Set object_ to be traversed

```javascript
var set1 = new Set(); 
  
set1.add({Firstname: "Sumit", Lastname: "Ghosh"}); 
set1.add(50); 
set1.add(30); 
set1.add(40); 
set1.add("Geeks"); 
set1.add("GFG"); 
  
const printOne = value => console.log(value);
set1.forEach(printOne); 
  
const printTwo = (key, value) => onsole.log(key+"  "+value);
set1.forEach(printTwo); 
  
function printThree(key, value, set) 
{            
    console.log(key+"  "+values); 
    console.log(set); 
} 
set1.forEach(printThree); 
```

### Some Usage of Sets

```javascript
// Remove duplicate elements from the array
const numbers = [2,3,4,4,2,3,3,4,4,5,5,6,6,7,5,32,3,4,5];
const setNumbers = [...new Set(numbers)];
console.log(setNumbers);

// convert Set object to an Array object, with Array.from
let myArr = Array.from(setNumbers);

let myArray = ['value1', 'value2', 'value3']

// Use the regular Set constructor to transform an Array into a Set
let mySet = new Set(myArray)
mySet.has('value1')     // returns true

// Use the spread operator to transform a set into an Array.
console.log([...mySet]) // Will show you exactly the same Array as myArray

//case sensitive & duplicate ommision
new Set("Firefox")  // Set(7) [ "F", "i", "r", "e", "f", "o", "x" ]
new Set("firefox")  // Set(6) [ "f", "i", "r", "e", "o", "x" ]

// the following will also work if run in an HTML document
mySet.add(document.body)
mySet.has(document.querySelector('body')) // true

// Use Set to ensure the uniqueness of a list of values
const array = Array
  .from(document.querySelectorAll('[id]'))
  .map((e) => e.id);

const setim = new Set(array);
console.assert(setim.size == array.length);
```

There are more methods implementing basic set operations \(**isSuperset, union, intersection, difference, symmetricDifference** etc.\) at below official link:

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)



