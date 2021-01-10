# For .. of Loop

### For .. of Loop

The **for...of loop** is the most recent addition to the family of for loops in JavaScript. It combines the strengths of its siblings, the **for loop** and the **for...in loop**, to loop over any type of data that is **iterable.** 

The **for...of loop** is used to loop over any type of data that is _iterable_. The data types **String**, **Array**, **Map**, and **Set** are _default **iterable.**_ But, the **`Object`** data type \(i.e. `{}`\) is **not** _**iterable**_, by default.

```javascript
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const digit of digits) {
  console.log(digit); // 0 1 2 3 4 5 6 7 8 9
}
```

**The for...of loop** the _most concise version_ of all the for loops. You can **stop** or **break** a _for...of loop_ at anytime.

```javascript
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const digit of digits) {
  if (digit % 2 === 0) {
    continue;
  }
  console.log(digit); // 1 3 5 7 9
}
```

When adding new properties to objects, for example \(`Array.prototype.myfunction (){...}`\), the **for...of loop** will _only_ loop over **the values in the object**. \(_see below for .. in loop_\)

### 

### For Loop

The biggest downside of a for loop is having to keep track of **the counter** and **exit condition**.

```javascript
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (let i = 0; i < digits.length; i++) {
  console.log(digits[i]); // 0 1 2 3 4 5 6 7 8 9
}
```

While _for loops_ certainly have an advantage when looping through arrays, some data is not structured like an array, so _a for loop_ isn’t always an option.

###  <a id="the-for-in-loop"></a>

### The for...in loop <a id="the-for-in-loop"></a>

_The for...in loop_ improves upon the weaknesses of the for loop by _eliminating the counting logic and exit condition. \(But, still track the index !\)_

```javascript
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const index in digits) {
  console.log(digits[index]); // 0 1 2 3 4 5 6 7 8 9
}
```

The **for...in loop** can get you into big trouble when you need to add an extra method to an array \(or another object\). **Because for...in loops loop over all enumerable properties**, this means if you add any additional properties to the array's prototype, then those properties will also appear in the loop. _This is why for...in loops are discouraged when looping over arrays._

```javascript
Array.prototype.decimalfy = function() {
  for (let i = 0; i < this.length; i++) {
    this[i] = this[i].toFixed(2);
  }
};

const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const index in digits) {
  console.log(digits[index]); // 0 1 2 3 4 5 6 7 8 9 function(){...}
}
```

> **NOTE:** The **forEach loop** is another type of for loop in JavaScript. However, `forEach()` is actually an array method, so it can only be used exclusively with arrays. There is also no way to stop or break a forEach loop. If you need that type of behavior in your loop, you’ll have to use a basic for loop.



