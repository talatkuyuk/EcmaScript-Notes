# Sets

A **set** is a collection of **distinct items** in mathematics. For example, `{2, 4, 5, 6}` is a set because each number is unique and appears only once. However, `{1, 1, 2, 4}` is _not_ a set because it _contains duplicate entries_.

In JavaScript, **arrays** _do not enforce items to be unique_.

In ES6, there’s a new built-in object that behaves like a mathematical set and works similarly to an array. This new object is conveniently called a "Set". 

The biggest differences between a set and an array are:

* Sets are not indexed-based - you do not refer to items in a set based on their position in the set
* items in a Set can’t be accessed individually

Basically, a Set is an object that lets you store unique items. You can add items to a Set, remove items from a Set, and loop over a Set. These items can be either primitive values or objects.

###  <a id="how-to-create-a-set"></a>

### How to Create a Set <a id="how-to-create-a-set"></a>

```javascript
const games = new Set(); // creates an empty Set games with no items.
console.log(games); // Set {}

const games = new Set(['Super Mario', 'Banjo-Kazooie', 'Super Mario']);
console.log(games); // Set {'Super Mario', 'Banjo-Kazooie'}
```

If you want to create a Set from a list of values, you use an array: Set removes the duplicate entry.

###  <a id="modifying-sets"></a>

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

The `.forEach(callbackFn[, thisArg])` method calls `callbackFn` once for each value present in the `Set` object, in insertion order. If a `thisArg` parameter is provided, it will be used as the `this` value for each invocation of `callbackFn`.

```javascript
console.log(months.values());
// SetIterator {'January', 'February', 'March', 'April', 'May', 'June', 
// 'July', 'August', 'September', 'October', 'November', 'December'}

console.log(months.entries());
// 
```



