# Array Destructuring

**Array Destructuring** is that you to specify the elements you want to extract from **an array** _on the left side of an assignment_.

```javascript
const point = [10, 25, -34];

const [x, y, z] = point;

console.log(x, y, z); // 10 25 -34
```

The brackets `[ ]` in line 3 represent the array being destructured. You don’t have to specify the indexes for where to extract the values from because the **indexes are implied.**

You can also ignore values when destructuring arrays.

```javascript
const point = [10, 25, -34];

const [x, , z] = point; // ignores the y coordinate and discards it.

console.log(x, z); // 10 -34
```

An example,

```javascript
const things = ['red', 'paperclip', 'green','earth', 'udacity', 'blue', 'dogs'];
const [one,, two,,, three] = things;
const colors = `List of Colors 1. ${one} 2. ${two} 3. ${three}`;
console.log(colors); // List of Colors 1. red 2. green 3. blue
```



