# Object Destructuring

**Object Destructuring** is that you to specify the elements you want to extract from **an** **object** _on the left side of an assignment_. **The indexes are implied.** 

```javascript
const gemstone = {
  type: 'quartz',
  color: 'rose',
  carat: 21.29
};

const {type, color, carat} = gemstone;

console.log(type, color, carat); // quartz rose 21.29
```

 **The curly braces** `{ }` in line 7 represent the object being destructured.

**You don’t have to specify the property from where to extract the values.** Because the object has **a property named** specified,  the value is automatically stored in that variable. 

An object can hold functions as well as key-values. When destructurig, **this** context disappears if it is used in a function which is placed in an object.

```javascript
const circle = {
  radius: 10,
  color: 'orange',
  getArea: function() {
    return Math.PI * this.radius * this.radius;
  },
  getCircumference: function() {
    return 2 * Math.PI * this.radius;
  }
};

let {radius, getArea, getCircumference} = circle;
getArea(); // NaN, because not a part of the object. This context disappeared.
```



