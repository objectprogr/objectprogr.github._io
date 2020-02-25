---
layout: post
title: "Day 5 - JavaScript - DOM manipulate"
date:   2018-10-28 11:00:00
excerpt: "The Document Object Model (DOM) is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style, and content."
paermalink: /2018/10/day-5-javascript-dom-manipulate.html
tags: oldBlog
--- 

#### What is the DOM?
The Document Object Model (DOM) is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style, and content. A Web page is a document. This document can be either displayed in the browser window or as the HTML source.

#### JavaScript basic syntax
[More examples](https://www.w3schools.com/js/js_htmldom_document.asp)

**GetElementById**

```javascript
    var byId = document.getElementById('exampleId');
    console.log(byId.id);
    //output = exampleId
```

**GetElementsByTagName**

```javascript
    var byId = document.getElementsByTagName('p');
```

**GetElementsByClassName**

```javascript
    var byId = document.getElementsByClassName('testClass')[0];
    console.log(byId.className);
    // output = "testClass"
```

#### Changing HTML elements

**innerHtml**

```javascript
    var byId = document.getElementById('exampleId');
    console.log(byId.id);
    byId.innerHTML = "New div content";
```

**Adding and deleting elements**

```javascript
//adding
    var btn = document.createElement('button');
    document.body.appendChild(btn);

//deleteing
    var div1 = document.getElementById('id1');
    div1.remove();
```

**Add class**

```javascript
    var div1 = document.getElementById('id1');
    div1.className += ' newClass';
    //output = <div class='oldCLass newClass'></div>
```

**Set attribute**

```javascript
    var div1 = document.getElementById('id1');
    div1.setAttribute('class', 'newClass');
    //output = <div class='newClass'></div>
```