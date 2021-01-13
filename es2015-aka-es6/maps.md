# Maps

### **Sets vs. Maps**

**Maps** are collection of **key-value pairs**. `{key1 = value1, key2 = "something"}` **`MAPS::OBJECTS`**

**Sets** are collection of **unique values**.`[val1, val2, val3]`  **SETS::ARRAYS**

**Sets** can be created from a list of values; but not **Maps**.

### Maps

**Maps** are similar to _Objects_ because Maps store key-value pairs similar to how objects contain named properties with values. 

**A Map** is an object that lets you store key-value pairs where both the keys and the values can be **objects, primitive values**, or **a combination of the two.**

### How to Create and Modify a Map <a id="how-to-create-a-map"></a>

A map can be created with **`new Map()`method.**

Key-values can be added by using the Map’s **`.set()` method** which takes _two arguments_. The first argument is the key, which is used to reference the second argument, the value.

To remove key-value pairs, simply use the **`.delete()` method**.

Similar to Sets, you can use the **`.clear()` method** to remove all key-value pairs from the Map.

You can use the **`.has()` method** to check if a key-value pair exists in your Map by passing it a key.

You can also retrieve values from a Map, by passing a key to the **`.get()` method**.

```javascript
const employees = new Map(); // empty "Map" employee with no key-value pairs.
console.log(employees); // Map {}

employees.set('james@udacity', { 
    fName: 'James',
    lName: 'Parkes'
});
employees.set('julia@udacity', {
    fName: 'Julia',
    lName: 'Van Cleve'
});

console.log(employees);
// Map {'james@udacity' => Object {...}, 'julia@udacity' => Object {...}}

console.log(members.has('james@udacity')); // true

console.log(members.get('james@udacity')); // {fName: 'James', lName: 'Parkes'}

employees.delete('james@udacity');
console.log(employees);
// Map {'julia@udacity' => Object {fName: 'James', lName: 'Parkes'}}

console.log(members.has('james@udacity')); // false

employees.clear();
console.log(employees); // Map {}

```

> If you `.set()` a key-value pair to a Map that already uses the same key, you won’t receive an error, but the key-value pair will overwrite what currently exists in the Map. Also, if you try to `.delete()` a key-value that is not in a Map, you won’t receive an error, and the Map will remain unchanged.

> The `.delete()` method returns `true` if a key-value pair is successfully deleted from the `Map` object, and `false` if unsuccessful. The return value of `.set()` is the `Map` object itself if successful.

### How to Loop Through a Map <a id="how-to-create-a-map"></a>

We’ve got three different options to choose from:

1. Step through each key or value using the **Map’s default iterator**
2. Loop through each key-value pair using the new **`for...of` loop**
3. Loop through each key-value pair using the Map’s **`.forEach()` method**

### 1. Using the MapIterator <a id="1-using-the-mapiterator"></a>

Using both the `.keys()` and `.values()` methods on a Map will return a new iterator object called `MapIterator`. You can store that iterator object in a new variable and use `.next()` to loop through each key or value. 

```javascript
const members = new Map();
members.set('Evelyn', 75.68);
members.set('Liam', 20.16);
members.set('Sophia', 0);
members.set('Marcus', 10.25);

let iteratorObjForKeys = members.keys();
iteratorObjForKeys.next(); // Object {value: 'Evelyn', done: false}
iteratorObjForKeys.next(); // Object {value: 'Liam', done: false}
iteratorObjForKeys.next(); // Object {value: 'Sophia', done: false}

let iteratorObjForValues = members.values();
iteratorObjForValues.next(); // Object {value: 75.68, done: false}
```

### 2. Using a for...of Loop <a id="2-using-a-for-of-loop"></a>

Your second option for looping through a Map is with a `for...of` loop.

```javascript
for (const member of members) {
  console.log(member); // ['Evelyn', 75.68] and so on.
}

for (const member of members) { 
    [key, value] = member; 
    let myobject = {key: value};
    console.log(myobject); // {'Evelyn': 75.68}
}
```

### 3. Using a forEach Loop <a id="3-using-a-foreach-loop"></a>

Your last option for looping through a Map is with the `.forEach()` method.

```javascript
members.forEach((value, key) => console.log(key, value));
```



