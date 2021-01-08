# Template Literals

ES6, supports **string interpolation** using **backticks** ````````and placeholders. This feature is called **template literals**.

**Template literals** are essentially **string literals** that include embedded expressions.

Denoted with **backticks** \(\` \`\) instead of single quotes \( `''` \) or double quotes \( `""` \), template literals can contain placeholders which are represented using `${expression}`. This makes it _much easier_ to build strings.

```javascript
let message = `Dear ${student.name}, your exam result is ${point}.`;
// returns: Dear Talat, your exam result is 100.
```

It is also easy to build multi line strings ****by using **template literals**:

```javascript
let note = `${teacher.name} 

  Please excuse ${student.name}
  He is recovering from the flu.
  
  Thank you
  
  ${student.guardian}`;
  
console.log(note);
```

**Template literals can hold any javascript expression within `${expression}`**

```javascript
console.log(`Your total point is ${point + extra}.`);
const result = `Dear ${name}, you ${doEvaluate(id) ? 'passed' : 'failed' }.`;
console.log(result);
```

**Prior to ES6**, the old way to concatenate strings together was by using the **string concatenation operator** \( `+` \).

```javascript
let message = ' Dear ' + student.name + ', your exam result is ' + point + '.';
// returns: Dear Talat, your exam result is 100.
```

For building multi-line strings, the old way was like this::

```javascript
let note = teacher.name + ',\n\n' +
  'Please excuse ' + student.name + '.\n' +
  'He is recovering from the flu.\n\n' +
  'Thank you,\n\n' +
  student.guardian;
```

