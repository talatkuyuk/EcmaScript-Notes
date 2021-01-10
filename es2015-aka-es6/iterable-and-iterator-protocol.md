# Iterable & Iterator Protocol

ES6 added two new protocols, the **iterable** protocol and the **iterator** protocol, which aren’t built-in.

### The Iterable Protocol

_ES6 introduces **a new iterable interface** that allows us to customize how objects are iterated._

**Iterable protocol,** allows JavaScript objects to define or customize their iteration behaviour. We can specify a way for iterating through values in an object thanks to iterable protocol.

For some objects, they already come built-in with this behavior. For example, **strings,** **arrays, sets** and **maps** are examples of **built-in iterables**.

```javascript
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
for (const digit of digits) {
  console.log(digit); // 0 1 2 3 4 5 6 7 8 9
}
```

In order for an object to be iterable, it must implement the **iterable interface**. in order for an object to be iterable it must contain a **default iterator method**. This method will define how the object should be iterated.

The **iterator method**, which is available via the constant `[Symbol.iterator]`, is a zero arguments function that **returns an iterator object**. _An iterator object is an object that conforms to the iterator protocol._

## The Iterator Protocol <a id="the-iterator-protocol"></a>

The **iterator protocol** is used to define a standard way that an object produces a sequence of values. 

We have a process for defining how an object will iterate. This is done through implementing the **`.next()`** method. An object becomes an iterator when it implements the `.next()` method. 

**The `.next()` method is** _**a zero arguments function**_ **that returns** **an object with two properties**:

1. **`value`** : the data representing the next value in the sequence of values within the object
2. **`done`** : a boolean representing if the iterator is _done_ going through the sequence of values
   * If done is _**true**_, then the iterator has reached the end of its sequence of values.
   * If done is _**false**_, then the iterator is able to produce another value in its sequence of values.

We are using the array’s default iterator to step through the each value in the array.

```javascript
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
const arrayIterator = digits[Symbol.iterator]();

console.log(arrayIterator.next()); // Object {value: 0, done: false}
console.log(arrayIterator.next()); // Object {value: 1, done: false}
console.log(arrayIterator.next()); // Object {value: 2, done: false}
```

