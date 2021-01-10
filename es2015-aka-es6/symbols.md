# Symbols

A **symbol** is a _unique and immutable data type_ that is often used to identify object properties.

**To create a symbol**, you write **`Symbol()`** with an optional string as its **description**._The description is just a way to describe the symbol, but it can’t be used to access the symbol itself._

If you **compare** two symbols with the same description, they are **not equal**, because the description is _only_ used to describe the symbol. It’s not used as part of the symbol itself—each time a new symbol is created, regardless of the description.

```javascript
const sym1 = Symbol('apple');
console.log(sym1); // Symbol(apple)

const sym2 = Symbol('banana');
const sym3 = Symbol('banana');
console.log(sym2 === sym3); // false
```



### A benefit of Symbols in objects

Instead of adding another banana to the bowl, banana **is** **overwritten** by the new banana being added to the bowl. \(first part below\)

To fix this problem, change the bowl’s properties to use symbols, each property is a unique Symbol and the first banana **doesn’t get overwritten** by the second banana. \(second part below\)

```javascript
const bowl = {
  'apple': { color: 'red', weight: 136.078 },
  'banana': { color: 'yellow', weight: 183.151 },
  'orange': { color: 'orange', weight: 170.097 },
  'banana': { color: 'yellow', weight: 176.845 }
};

// dublicates are overriden.
console.log(bowl); // Object {apple: Object, banana: Object, orange: Object}
```

```javascript
const bowl = {
  [Symbol('apple')]: { color: 'red', weight: 136.078 },
  [Symbol('banana')]: { color: 'yellow', weight: 183.15 },
  [Symbol('orange')]: { color: 'orange', weight: 170.097 },
  [Symbol('banana')]: { color: 'yellow', weight: 176.845 }
};
console.log(bowl); 
// Object {Symbol(apple): Object, Symbol(banana): Object, 
// Symbol(orange): Object, Symbol(banana): Object}
```

>



