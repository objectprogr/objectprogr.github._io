---
layout: post
title: "Day 6 - JavaScript - hoisting, event bubbling, prototype etc."
date:   2018-10-29 14:00:00
excerpt: "That's mean that JS engine moves all variables to beginning of the lexical scope."
paermalink: /2018/10/day-6-javascript-hoisting-event-bubbling-prototype.html
tags: oldBlog
--- 

#### Hoisting
That's mean that JS engine moves all variables to beginning of the lexical scope.

**Example:**

```javascript
function hoisting() { console.log(x); // undefined - that's mean that variable x aleready exists! 
  if (true) {
    var x = 1;
  }
console.log(x); // 1
}
```

JS engine transform above code:

```javascript
function hoisting() { 
var x; //JS moves variables declaration to begining
console.log(x); 
  if (true) {
    var x = 1;
  }
console.log(x);
```
**More informations and examples**
[MDN web docs](https://developer.mozilla.org/pl/docs/Glossary/Hoisting)

## Tips

**Good practice - declare all variables on the beginning of the code**

## Event bubbling

Event Bubbling is the event starts from the deepest element or target element to its parents, then all its ancestors which are on the way to bottom to top.

![Event bubbling](/assets/posts/media/event_bubbling.png)

*Source [javascript.info](https://javascript.info/bubbling-and-capturing)*

**More informations**
[Medium](https://medium.com/@vsvaibhav2016/event-bubbling-and-event-capturing-in-javascript-6ff38bec30e)
[javascript.info](https://javascript.info/bubbling-and-capturing)

## Prototype

The prototype is a reference to another object and it is used whenever JS can’t find the property you’re looking for on the current object. Prototype inheritance provide posibility interact with any elements as an object. 
JavaScript objects have a link to a prototype object. When trying to access a property of an object, the property will not only be sought on the object but on the prototype of the object, the prototype of the prototype, and so on until either a property with a matching name is found or the end of the prototype chain is reached.

![Prototype diagram](/assets/posts/media/prototype_diagram.png)

*More informations*
- [hackernoon.com](https://hackernoon.com/inheritance-in-javascript-21d2b82ffa6f)
- [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [medium.com - 1](https://medium.com/@kevincennis/prototypal-inheritance-781bccc97edb)
- [medium.com - 2](https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9)
- [stackoverflow](https://stackoverflow.com/questions/2800964/benefits-of-prototypal-inheritance-over-classical)