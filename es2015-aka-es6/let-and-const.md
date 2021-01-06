# Let and Const

### The General Rules: 

* Variables declared with `let` can be reassigned.
* Variables declared with `const` must be assigned an initial value, and can’t be reassigned.
* Variables `let` or `const`, can’t be redeclared in the same scope.

Suggested that always declare variables with `const.`If there is need to update a variable or change it, then switch it from `const` to `let.`

* use `let` when you plan to reassign new values to a variable.
* use `const` when you don’t plan on reassigning new values to a variable.

**No need to use `var`any more, it is considered as bad practice.**

### Hoisting

Hoisting is a result of how JavaScript is interpreted by the browser. Essentially, before any JavaScript code is executed, all variables declared with `var` are "hoisted", which means they're raised to the top of the function scope. 

Variables declared with `var` are either scoped _globally_ or _locally_ to an **entire function scope**.

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

Because, at run-time, the `getClothing()` function actually looks more like this: That is, `freezing` variable is declared but not defined yet.

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

### 

### let and const

Variables declared with `let` and `const` eliminate this specific issue of hoisting because they’re scoped **to the block**, not to the function. 

If a variable is declared using `let` or `const` inside a block of code \(denoted by curly braces `{ }`\), then the variable is stuck in what is known as the **temporal dead zone** until the variable’s declaration is processed. 

This behavior prevents variables from being accessed only until after they’ve been declared.

In the example, if we describe the variables as `const`, it would _throw an error_: Because `freezing` is declared in another block, and if statement skip this declaration.

```javascript
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

