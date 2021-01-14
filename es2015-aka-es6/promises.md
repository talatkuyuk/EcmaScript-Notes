# Promises

## Promises <a id="promises"></a>

**A promise** will let a process start that will be done **asynchronously** and let the main process get back to its regular work.

A JavaScript Promise is created with the constructor function - `new Promise()`

**A promise** must have **a asynchronous function** as an argument while constructed. 

```javascript
new Promise(function () {
    window.setTimeout(function createSundae(flavor = 'chocolate') {
        const sundae = {};
        // request ice cream
        // get cone
        // warm up ice cream scoop
        // scoop generous portion into cone!
    }, Math.random() * 2000);
});
```

### Indicating the Request Successful  or a Failed <a id="indicated-a-successful-request-or-a-failed-request"></a>

**The Promise** notify us the process is finished by passing **two functions** into Promise constructor function. Typically we call these **`resolve`** and **`reject`**.

**The `resolve` method** is used to indicate that the request is completed _successfully_. It passes the data we want to return - in this case the data that's being returned is the completed sundae. 

```javascript
new Promise(function (resolve, reject) {
    window.setTimeout(function createSundae(flavor = 'chocolate') {
        const sundae = {};
        // request ice cream
        // get cone
        // warm up ice cream scoop
        // scoop generous portion into cone!
        resolve(sundae);
    }, Math.random() * 2000);
});
```

**The `reject` method** is used when the request _could not be completed_. Even though the request fails, we can still return data - in this case we're just returning text that says an excuse..

```javascript
new Promise(function (resolve, reject) {
    window.setTimeout(function createSundae(flavor = 'chocolate') {
        const sundae = {};
        // request ice cream
        // get cone
        // warm up ice cream scoop
        // scoop generous portion into cone!
        if ( /* iceCreamConeIsEmpty(flavor) */ ) {
            reject(`Sorry, we're out of that flavor :-(`);
        }
        resolve(sundae);
    }, Math.random() * 2000);
});
```

A Promise constructor takes a function that will run and then, after some amount of time, will either complete **successfully** \(using the `resolve` method\) or **unsuccessfully** \(using the `reject` method\). When the outcome has been finalized \(the request has either completed successfully or unsuccessfully\), the promise is now _**fulfilled**_ and will notify us so we can decide what to do with the response.

### Promises Return Immediately <a id="promises-return-immediately"></a>

A Promise will immediately return an object. That object has a **`.then()` method** on it that we can use to have it notify us if the request we made in the promise was either successful or failed. 

The `.then()` method **takes two functions**:

1. the function to run if the request completed successfully
2. the function to run if the request failed to complete

```javascript
// const mySundae = new Promise(function (resolve, reject) {...});
// mySundae.then(function(sundae) {...}, function(msg) {...});

mySundae.then(function(sundae) {
    console.log(`Time to eat my delicious ${sundae}`);
}, function(msg) {
    console.log(msg);
    self.goCry(); // not a real method
});
```

**The first function** that's passed to `.then()` will be called and passed the data that the Promise's `resolve` function used. In this case, the function would receive the `sundae` object. 

**The second function** will be called and passed the data that the Promise's `reject` function was called with. In this case, the function receives the error message.

