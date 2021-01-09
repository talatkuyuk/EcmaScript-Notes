# Default Function Parameters

**ES6** has introduced a new way to create defaults. It's called _**default function parameters**_**.**

**Default function parameters** are quite easy to read since they're placed in the function's parameter list. To create a default parameter, you add an equal sign \( `=` \) and then whatever you want the parameter to default to if an argument is not provided. It can be any JavaScript type!

```javascript
function greet(name = 'Student', greeting = 'Welcome') {
  return `${greeting} ${name}!`;
}

greet(); // Welcome Student!
greet('James'); // Welcome James!
greet('Richard', 'Howdy'); // Howdy Richard!
```

\*\*\*\*

**If we don't use this functionality,** we would implement the same function like below: Look at the first two lines of the `greet()`. All of that is there to provide default values for the function if the required arguments aren't provided. 

```javascript
function greet(name, greeting) {
  name = (typeof name !== 'undefined') ?  name : 'Student';
  greeting = (typeof greeting !== 'undefined') ?  greeting : 'Welcome';

  return `${greeting} ${name}!`;
}

greet(); // Welcome Student!
greet('James'); // Welcome James!
greet('Richard', 'Howdy'); // Howdy Richard!
```

###  <a id="default-function-parameters"></a>

