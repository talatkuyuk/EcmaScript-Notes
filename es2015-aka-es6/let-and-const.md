# Let and Const

**The general rule**: Suggested that always declare variables with `const` If there is need to update a variable or change it, then switch it from `const` to `let`

* use `let` when you plan to reassign new values to a variable.
* use `const` when you don’t plan on reassigning new values to a variable.

No need to use `var`any more, it is considered as bad practice.

## Hoisting

Hoisting is a result of how JavaScript is interpreted by the browser. Essentially, before any JavaScript code is executed, all variables declared with `var` are "hoisted", which means they're raised to the top of the function scope.

For example, below `getClothing(false)` returns _undefined_:

```javascript
function getClothing(isCold) {
  if (isCold) {
    var freezing = 'Grab a jacket!';
  } else {
    var hot = 'It’s a shorts kind of day.';
    console.log(freezing);
  }
}

getClothing(false); // undefined
```

Because, at run-time, the `getClothing()` function actually looks more like the second: That is, `freezing` variable is declared but not defined yet.

```javascript
function getClothing(isCold) {
  var freezing, hot;
  if (isCold) {
    freezing = 'Grab a jacket!';
  } else {
    hot = 'It’s a shorts kind of day.';
    console.log(freezing);
  }
}
```

But if we describe the variables as `const`, it would _throw an error_: Because `freezing` is declared in another scope, and if statement skip this decleration.

```text
function getClothing(isCold) {
  if (isCold) {
    const freezing = 'Grab a jacket!';
  } else {
    const hot = 'It’s a shorts kind of day.';
    console.log(freezing);
  }
}

getClothing(false); // Uncaught ReferenceError: freezing is not defined
```

