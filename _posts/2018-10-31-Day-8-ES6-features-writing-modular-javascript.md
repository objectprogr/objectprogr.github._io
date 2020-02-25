---
layout: post
title:  "Day 8 - ES6+ new features, writing modular JavaScript"
date:   2018-10-31 13:00:00
excerpt: "Below i present the most important changes which provide ES6 (ECMAScript2015)."
paermalink: /2018/10/day-8-es6-new-features-writing-modular-javascript.html
tags: oldblog
--- 

#### ES6 new features
Below i present the most important changes which provide ES6 (ECMAScript2015).

- `Arrow function`

To create function using argument and arrow symbol without braces.

```javascript
// ECMAScript 6
odds  = evens.map(v => v + 1)

// ECMAScript 5
odds  = evens.map(function (v) { return v + 1; });
```

*Source - [psd2css.pl](https://psd2css.pl/baza-wiedzy/co-to-jest-es6)*

- `let` variable

`let` in contrast to `var` creates variable available only in a given block.

```javascript
var b = 0; // global variable "b"
for (let a = 0; a < 10; a++) { // block variable "a"
    b += a;
}

console.log((typeof b !== 'undefined') ? b : "undefined"); // 45
console.log((typeof a !== 'undefined') ? a : "undefined"); // undefined
```

*Source - [psd2css.pl](https://psd2css.pl/baza-wiedzy/co-to-jest-es6)*

- `const` variable

Create variable like `let` which her value are constant.

```javascript
// ECMAScript 6
const PI = 3.141593

// ECMAScript 5
Object.defineProperty(typeof global === "object" ? global : window, "PI", {
    value:        3.141593,
    enumerable:   true,
    writable:     false,
    configurable: false
})
```

*Source - [psd2css.pl](https://psd2css.pl/baza-wiedzy/co-to-jest-es6)*

`Class`

They don’t change the concept of inheritance. They are just syntactic sugar for prototypal inheritance.

```javascript
class Point {
    constructor(x, y) {
        this.x = x
        this.y = y
    }

    toString() {
        return '[X=' + this.x + ', Y=' + this.y + ']'
    }
}

class ColorPoint extends Point {
    static default() {
        return new ColorPoint(0, 0, 'black')
    }

    constructor(x, y, color) {
        super(x, y)
        this.color = color
    }

    toString() {
        return '[X=' + this.x + ', Y=' + this.y + ', color=' + this.color + ']'
    }
}

console.log('The first point is ' + new Point(2, 10))
console.log('The second point is ' + new ColorPoint(2, 10, 'green'))
console.log('The default color point is ' + ColorPoint.default())
```

*Source - [blog.programists.com](https://blog.pragmatists.com/top-10-es6-features-by-example-80ac878794bb)*

- ES6 added support for `modules`.



# Modules in ES6

Modules in ES6 are very simple to use. Like other usage of modules, ES6 provides a way to export modules so that they can be specified as dependencies to other modules.
Thanks modules we can divide project to smaller parts and keep more clean and more readable project.

#### Exporting Modules

Export function definition:

```javascript
export function setValue(x) {...}
export function getValue() {...}
```

Export object with the properties:

```javascript
function addValues() {...}
function sumValues() {...}
function otherFunction() {...}

export { addValues, sumValues};
```

#### Importing Modules

```javascript
// import all properties from values module
import * as values form './values.js';

vales.addValues();
```

Import specific elements from module

```javascript
import {addValues, sumValues} from './values.js';
```

*More informations:*

- [medium](https://medium.com/@crohacz_86666/basics-of-modular-javascript-2395c82dd93a)
- [freecodecamp](https://medium.freecodecamp.org/javascript-modules-a-beginner-s-guide-783f7d7a5fcc)


