---
layout: post
title:  "Day 7 - Fetch API / Ajax (XHR)"
date:   2018-10-30 14:00:00
excerpt: "This is interface which allows to asynchronous download of resources from server. Early to this we use object XMLHttpRequest (XHR). Fetch API was created for simplify communication with server. "
paermalink: /2018/10/day-7-fetch-api-ajax.html
tags: oldblog javascript
categories: homepage
--- 

#### Fetch API
This is interface which allows to asynchronous download of resources from server. Early to this we use object XMLHttpRequest (XHR). Fetch API was created for simplify communication with server. 
Fetch API priovide objects: **Request, Response, Headers and Body**.

![github](/assets/posts/media/github.png) [Example code on my github](https://github.com/objectprogr/30dayschallenge/tree/day7FetchAPI)

#### fetch() method:
Basis work with Fetch API is using method `fetch()` to asynchronous download data from server.
Example:

```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(response => response.json())
  .then(json => console.log(json));
```

Method download data from server and change data to json object and displaying in console.
Ofcourse, next to GET method to data downloading, are yet methods: POST, PUT and DELETE.
POST example:

```javascript
const data = {
    title: 'Test title',
    body: 'Test body',
    userId: 42
}
 
const options = {
   method: 'POST',
   body: JSON.stringify(data),
   headers: {
       'Content-Type': 'application/json'
   }
};
 
fetch('https://jsonplaceholder.typicode.com/posts', options)
  .then(response => response.json())
  .then(json => console.log(json));
```

**More informations:**
[Polish tutorial](https://devenv.pl/fetch-api/)
[English tutorial](https://scotch.io/tutorials/how-to-use-the-javascript-fetch-api-to-get-data)

#### XMLHttpRequest (XHR)
The XMLHttpRequest object can be used to request data from a web server.
The XMLHttpRequest object is a developers dream, because you can:

- Update a web page without reloading the page
- Request data from a server - after the page has loaded
- Receive data from a server  - after the page has loaded
- Send data to a server - in the background

Example:

```javascript
var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
       // Typical action to be performed when the document is ready:
       document.getElementById("demo").innerHTML = xhttp.responseText;
    }
};
xhttp.open("GET", "filename", true);
xhttp.send();
```
