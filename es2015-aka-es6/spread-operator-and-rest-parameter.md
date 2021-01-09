# Spread Operator and Rest Parameter

### Spread operator <a id="spread-operator"></a>

The **spread operator**, written with three consecutive dots \( `...` \), is new in ES6 and gives the ability to expand, or _spread_, iterable objects into multiple elements.

```javascript
const names = ["Talat", "Serdar", "Talha"];
console.log(...names); // Talat Serdar Talha
```

```javascript
const primes = new Set([2, 3, 5, 7, 11, 13, 17, 19]);
console.log(...primes); // 2 3 5 7 11 13 17 19
```

### 

### Combining Arrays 

Spread operator gives a better way for combining arrays.

```javascript
const fruits = ["apples", "bananas"];
const vegetables = ["corn", "carrots"];

// This, below, wouldn't not work ! 
const produce = [fruits, vegetables]; // [Array[3], Array[3]]

// prior to the spread operator, we use the Array’s concat() method.
const produce = fruits.concat(vegetables); // apples bananas corn carrots

// with spread operator, it is better way.
const produce = [...fruits, ...vegetables]; // apples bananas corn carrots
```

###  <a id="rest-parameter"></a>

### Rest parameter <a id="rest-parameter"></a>

The **rest parameter**, also written with _three consecutive dots_ \( `...` \), allows to represent an **indefinite number of elements as an array**. By using the rest parameter, `...rest_parameter` is assigned the _rest_ _of the values_ in the array \(as an array\).

```javascript
const order = [20.17, 1.50, "cheese", "eggs"];
const [total, tax, ...items] = order;
console.log(total, tax, items); // 20.17 1.5 ["cheese", "eggs"]
```

**Another use case** **for the rest parameter** is when you’re working with variadic functions. **Variadic functions** are functions that take an indefinite number of arguments.

```javascript
// This version of the sum() function is more concise and is easier to read. 
function sum(...nums) {
  let total = 0;  
  for(const num of nums) {
    total += num;
  }
  return total;
}

sum(2, 3, 5); // 10
sum(2); // 2
```

**In previous versions of JavaScript,** variadic functions would be handled using the **arguments object** which is ****_an array-like object_ that is available as a local variable **inside all functions**. 

```javascript
function sum() {
  let total = 0;  
  for(const argument of arguments) {
    total += argument;
  }
  return total;
}
```

This is misleading because the definition for the `sum()` doesn't have any parameter but we know it can handle an indefinite amount of arguments. And, it can be hard to understand, If never used the arguments object before.

