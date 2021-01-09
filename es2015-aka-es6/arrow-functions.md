# Arrow Functions

**Functions** are one of the primary data structures in JavaScript.

**Arrow functions** are very similar to _regular functions_ in behavior, but are quite different syntactically. Notice the _arrow_ in the arrow function \( `=>` \).

```javascript
// with regular function
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(function(name) { 
  return name.toUpperCase();
});

// with arrow function
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(
  name => name.toUpperCase()
);
```

The steps for converting the existing "normal" function into an arrow function.

* remove the `function` keyword
* remove the parentheses
* remove the opening and closing curly braces
* remove the `return` keyword
* remove the semicolon
* add an arrow \( `=>` \) between the parameter list and the function body

Regular functions can be either **function declarations** or **function expressions**, however arrow functions are _always_ **expressions**. In fact, their full name is "arrow function expressions".

**Arrow functions** can only be used where an expression is valid. This includes being:

* stored in a variable,
* passed as an argument to a function,
* and stored in an object's property.

```javascript
const greet = name => `Hello ${name}!`;
greet('Asser'); // Hello Asser!
```

if there are **two or more** items in the parameter list, or if there are **zero** items in the list, then you need to wrap the list in parentheses:

```javascript
// empty parameter list requires parentheses
const sayHi = () => console.log('Hello Udacity Student!');
sayHi(); // Hello Udacity Student!

// multiple parameters requires parentheses
const orderIceCream = (flavor, cone) => console.log(`Here's your ${flavor} ice cream in a ${cone} cone.`);
orderIceCream('chocolate', 'waffle'); // Here's your chocolate ice cream in a waffle cone.
```

Below all are valid arrow functions.

```javascript
const greet = () => "Hello";
const greet = _ => "Hello";
const bigVowel = (letter) => letter.toUpperCase(); 
const bigVowel = letter => letter.toUpperCase(); 
```



### Arrow functions with _Concise_ _Body_ _Syntax_ <a id="concise-and-block-body-syntax"></a>

When an arrow function **only has a single expression**, its body is called as _"**concise body syntax**"_.

* has _no curly braces_ surrounding the function body
* and automatically returns the expression.

```javascript
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(
  name => name.toUpperCase()
);
```

### Arrow functions with _Block Body Syntax_ <a id="concise-and-block-body-syntax"></a>

When an arrow function **has more than one line of code**, its body is called as _"**block body syntax**"_.

* it _uses curly braces_ to wrap the function body
* and a `return` statement needs to be used to actually return something from the function.

```javascript
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map( name => {
  name = name.toUpperCase();
  return `${name} has ${name.length} characters in their name`;
});
```



