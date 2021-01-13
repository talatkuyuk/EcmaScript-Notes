# WeakMaps

The **`WeakMap`** object is a collection of key/value pairs in which the keys are weakly referenced. _The keys_ must be objects and _the values_ can be arbitrary values \( _a value can be anything, including an object or a function_\).

Keys of WeakMaps are of the type `Object` only. Primitive data types as keys are not allowed \(e.g. a `Symbol` can't be a `WeakMap` key\).

**A WeakMap** is just like a normal Map with a few key differences:

1. a WeakMap can **only** contain objects as keys,
2. a WeakMap is **not** iterable which means it can’t be looped and
3. a WeakMap does **not** have a `.clear()` method.

`WeakMap()`You can create a WeakMap with constructor. 

`.delete(key)`Removes any value associated to the `key`. 

`.get(key)`Returns the value associated to the `key`, or `undefined` if there is none.

`.has(key)`Returns a Boolean whether a value associated to the `key` in the `WeakMap` object or not.

`.set(key, value)`Sets the `value` for the `key` in the `WeakMap` object. Returns the `WeakMap` object.

```javascript
const book1 = { title: 'Pride', author: 'Jane' };
const book2 = { title: 'The Catcher', author: 'Salinger' };
const book3 = { title: 'Travels', author: 'Swift' };

const library = new WeakMap();
library.set(book1, true);
library.set(book2, false);
library.set(book3, 5);

console.log(library);
// WeakMap {Object {title:'Pride', author:'Jane'}=>true, Object {...}=>false,...}
```

…but if you try to add something other than an object as a key, you’ll get an error! This is expected behavior because **WeakMap can only contain objects as keys**. Again, similar to WeakSets, WeakMaps leverage garbage collection for easier use and maintainability.

```javascript
library.set('The Grapes of Wrath', false);
// Uncaught TypeError: Invalid value used as weak map key(…)
```

### Garbage Collection <a id="garbage-collection"></a>

In JavaScript, memory is allocated when new values are created and is "automatically" freed up when those values are no longer needed. This process of freeing up memory after it is no longer needed is what is known as _garbage collection_.

WeakMaps take advantage of this by exclusively working with objects as keys. If you set an object to `null`, then you’re essentially deleting the object. And when JavaScript’s garbage collector runs, the memory that object previously occupied will be freed up to be used later in your program.

```text
book1 = null;
console.log(library);
```

> `WeakMap {Object {title: 'The Catcher in the Rye', author: 'J.D. Salinger'} => false, Object {title: 'Gulliver’s Travels', author: 'Jonathan Swift'} => true}`

_\*\*\*\*_

What makes this so useful is you don’t have to worry about deleting keys that are referencing deleted objects in your WeakMaps, JavaScript does it for you! When an object is deleted, the object key will also be deleted from the WeakMap when garbage collection runs. This makes WeakMaps useful in situations where you want an efficient, lightweight solution for creating groupings of objects with metadata.

The point in time when garbage collection happens is dependent on a lot of different factors. Check out [MDN’s documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management#Garbage_collection) to learn more about the algorithms used to handle garbage collection in JavaScript.

