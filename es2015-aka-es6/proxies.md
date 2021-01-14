# Proxies

**A JavaScript Proxy** will let one object stand in for another object to handle all the interactions for that other object. **The proxy** can handle requests directly pass data back and forth to the target object, whole bunch of other things.

To create a proxy object use the Proxy constructor - `new Proxy();`which takes two arguments:

* **the target object** that it will be the proxy for.
* **the handler object:** an object containing the list of methods it will handle for the proxied object.

If we provide **an empty handler object**, the proxy just passes the request directly to the source object.

```javascript
var richard = {status: 'looking for work'};
var agent = new Proxy(richard, {});

agent.status; // returns 'looking for work'
```

**If we want the proxy object to actually intercept the request, that's what the handler object is for!**

The key to making Proxies useful is the **handler object** that's passed as the second object to the Proxy constructor. The handler object is made up of a methods that will be used for property access. 

### Get Trap <a id="get-trap"></a>

The `get` trap is used to "intercept" calls to properties:

```javascript
const richard = {status: 'looking for work'};
const handler = {
    get(target, prop, receiver) {
        console.log(target); // the `richard` object
        console.log(prop); // the name of the property 
};
const agent = new Proxy(richard, handler);
agent.status; // logs out the richard object (not the agent object!) and,
// the name of the property being accessed (`status`)
```

The `handler` object has a `get` method \(called a "**trap**" since it's being used in a Proxy\). 

When the code `agent.status;` The proxy "**intercepts**" the call to get the `status` property and runs the `get` trap function. This will log out the target object of the proxy \(the `richard` object\) and then logs out the name of the property being requested \(the `status` property\). 

It **does not** actually log out the property! This is important - _if a trap is used, you need to make sure you provide all the functionality for that specific trap_.

#### Accessing the target object from inside the proxy <a id="accessing-the-target-object-from-inside-the-proxy"></a>

If we wanted to actually provide the real result, we would need to return the property on the target object:  `return target[propName];`will access the property on the target object and will return it. 

```javascript
const richard = {status: 'looking for work'};
const handler = {
    get(target, prop, receiver) {
        console.log(target);
        console.log(prop);
        return target[prop];
    }
};
const agent = new Proxy(richard, handler);
agent.status; 
// (1)logs the richard object, 
// (2)logs the property being accessed, 
// (3)returns the text in richard.status
```

#### Having the proxy return info, directly <a id="having-the-proxy-return-info-directly"></a>

Alternatively, we could use the proxy to provide direct feedback: With this code, the Proxy doesn't even check the target object, it just directly responds to the calling code. So the `get` trap will take over whenever any property on the proxy is accessed. 

```javascript
const richard = {status: 'looking for work'};
const handler = {
    get(target, propName) {
        return `You should offer a contract.`;
    }
};
const agent = new Proxy(richard, handler);
agent.status; // returns the text `You should offer a contract.`
```

### Set Trap <a id="get-trap"></a>

If we want to intercept calls to _**change**_ **properties**, then the `set` trap needs to be used!

The `set` trap is used for intercepting code that will _change a property_. The `set` trap receives: the object it proxies the property that is being set the new value for the proxy

```javascript
const richard = {status: 'looking for work'};
const handler = {
    set(target, propName, value) {
        if (propName === 'payRate') { // if the pay is being set, take 15% as commission
            value = value * 0.85;
        }
        target[propName] = value;
    }
};
const agent = new Proxy(richard, handler);
agent.payRate = 1000; // set the actor's pay to $1,000
agent.payRate; // $850 the actor's actual pay
```

In the code above, notice that the `set` trap checks to see if the `payRate` property is being set. If it is, then the proxy \(the agent\) takes 15 percent off the top for her own commission! Then, when the actor's pay is set to one thousand dollars, since the `payRate` property was used, the code took 15% off the top and set the actual `payRate` property to `850`;

### Other Traps <a id="other-traps"></a>

There are actually a total of **13 different traps** that can be used in a handler!  Check it out at below link:

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Proxy](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)





