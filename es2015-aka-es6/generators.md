# Generators

### Normal functions are "run-to-completion" in JavaScript

Whenever a function is invoked, the JavaScript engine starts at the top of the function and runs every line of code until it gets to the bottom. There's no way to stop the execution of the function in the middle and pick up again at some later point. This refers **"**run-to-completion**".**

### Generator Functions _\(Pausable Functions\)_ <a id="pausable-functions"></a>

If we  want to be able to pause a function mid-execution, then we'll need a new type of function available to us in ES6 - **generator functions**! 

```javascript
function* getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Farrin', 'James'];

    for (const name of names) {
        console.log( name );
    }

    console.log('the function has ended');
}
```

**The** **asterisk** \(`*`\) right after the `function` keyword indicates that this function is actually **a generator**!

The asterisk of the generator can actually be placed anywhere between the `function` keyword and the function's name. So all three of these are **valid** **generator declarations**!

* `function* names() { /* ... */ }  //prefer this`
* `function * names() { /* ... */ }`
* `function *names() { /* ... */ }`

**When a generator is invoked**, _it doesn't actually run any of the code inside the function_. Instead, **it creates and returns an iterator.** This iterator can then be used to execute the actual generator's inner code.

The first time the iterator's `.next()` method was called it ran all of the code inside the generator. The code never paused! 

```javascript
getEmployee(); // it doesn't actually run any of the code inside the function.

const generatorIterator = getEmployee(); // Actually it returns an iterator.
generatorIterator.next();

/*
the function has started
Amanda
Diego
Farrin
James
the function has ended
*/
```

### The Yield Keyword <a id="the-yield-keyword"></a>

The `yield` keyword is new and was introduced with ES6. It can only be used inside generator functions. `yield` is what causes the generator to pause. 

There's now a `yield` inside the `for...of` loop. We invoke the generator \(which produces an iterator\) and then call `.next().`

```javascript
function* getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Farrin', 'James'];

    for (const name of names) {
        console.log(name);
        yield;
    }

    console.log('the function has ended');
}

const generatorIterator = getEmployee();

generatorIterator.next();
// the function has started
// Amanda

generatorIterator.next();
// Diego
```

### The number of .next\(\) method to complete the generator function. <a id="yielding-data-to-the-outside-world"></a>

It will be called **one more time than the number of `yield` expressions** in the generator function.

In order to fully complete the `udacity` generator function below, the iterator's `.next()` method need to be called **three times**. 

The **first** **call** to `.next()` will start the function and run to the first `yield`. The **second** **call** to `.next()` will pick up where things left off and run to the second `yield`. The **third and final** **call** to `.next()` will pick up where things left off again and run to the end of the function.

```javascript
function* udacity() {
    yield 'Richard';
    yield 'James'
}
```

### Yielding Data to the "Outside" World <a id="yielding-data-to-the-outside-world"></a>

Below the code "return" the name and then pause. 

When the generator is run, it will "yield" the name back out to the function _and then pause its execution_.

```javascript
function* getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Farrin', 'James'];

    for (const name of names) {
        yield name; // instead of console.log(name);
    }

    console.log('the function has ended');
}

const generatorIterator = getEmployee();
let result = generatorIterator.next();
result.value // is "Amanda"

generatorIterator.next().value // is "Diego"
generatorIterator.next().value // is "Farrin"
```

### Send Data back _into_ the Generator <a id="yielding-data-to-the-outside-world"></a>

We can also send data back _into_ the generator, too. We do this using the `.next()` method:

```javascript
function* displayResponse() {
    const response = yield;
    console.log(`Your response is "${response}"!`);
}

const iterator = displayResponse();

// starts running the generator function
iterator.next(); 

// send data into the generator
iterator.next('Hello Udacity'); // Your response is "Hello Udacity"!
```

Calling `.next()` with data \(i.e. `.next('Richard')`\) will send data into the generator function where it last left off. It will "replace" the yield keyword with the data that you provided.

So the `yield` keyword is used to pause a generator _and_ used to send data outside of the generator, and then the `.next()` method is used to pass data _into_ the generator. Here's an example that makes use of both of these to cycle through a list of names one at a time:

```text
function* getEmployee() {
    const names = ['Amanda', 'Diego', 'Farrin', 'James', 'Kagure', 'Kavita', 'Orit', 'Richard'];
    const facts = [];

    for (const name of names) {
        // yield *out* each name AND store the returned data into the facts array
        facts.push(yield name); 
    }

    return facts;
}

const generatorIterator = getEmployee();

// get the first name out of the generator
let name = generatorIterator.next().value;

// pass data in *and* get the next name
name = generatorIterator.next(`${name} is cool!`).value; 

// pass data in *and* get the next name
name = generatorIterator.next(`${name} is awesome!`).value; 

// pass data in *and* get the next name
name = generatorIterator.next(`${name} is stupendous!`).value; 

// you get the idea
name = generatorIterator.next(`${name} is rad!`).value; 
name = generatorIterator.next(`${name} is impressive!`).value;
name = generatorIterator.next(`${name} is stunning!`).value;
name = generatorIterator.next(`${name} is awe-inspiring!`).value;

// pass the last data in, generator ends and returns the array
const positions = generatorIterator.next(`${name} is magnificent!`).value; 

// displays each name with description on its own line
positions.join('\n'); 
```

