# Transpiler

We use transpiler to convert Java to JavaScript.

The most popular JavaScript transpiler is called Babel. [https://babeljs.io](https://babeljs.io)

Originally, Babel would convert ES6 code to ES5 code. Now, Babel does a lot more. It'll convert ES6 to ES5, JSX to JavaScript, and Flow to JavaScript. [https://babeljs.io/repl](https://babeljs.io/repl)

The way Babel transforms code from one language to another is through plugins. For a full list, check out [all of Babel's plugins](http://babeljs.io/docs/plugins/).

Instead of having to use a bunch of individual plugins, Babel has **presets** which are groups of plugins bundled together. For example, we'll just use the [ES2015 preset](http://babeljs.io/docs/plugins/preset-es2015/) that is a collection of all the plugins we'll need to convert all of our ES6 code to ES5.

```text
npm install --save-dev @babel/preset-es2015
```

 `.babelrc` configutaion file:This is where to put all of the plugins and/or presets that the project will use.

```text
{
  "presets": ["@babel/preset-es2015"]
}
```

### an example app and transpilation

Simple app that demos transpiling ES6 code to ES5 code with Babel: [https://github.com/udacity/course-es6/tree/master/lesson-4/walk-through-transpiling](https://github.com/udacity/course-es6/tree/master/lesson-4/walk-through-transpiling) This small app transpiles "ES6" directory that contains the ES6 code to ES5 code that will be able to run in every browser \(using Babel\). 

**ES6 Code:** \['Richard', 'James'\].map\(name =&gt; `${name}!`\);

**ES5 Code:** \['Richard', 'James'\].map\(function \(name\) { return "".concat\(name, "!"\); }\);

### Conclusion

We can write in ES6 and then use a transpiler to convert it to ES5 code. This lets us transform our project's code base to the newest version of the language while still letting it run everywhere. 

Then, once all of the browsers your app has to run on fully support ES6 code, you can stop transpiling your code and just serve the straight ES6 code, directly!x

