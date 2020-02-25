---
layout: post
title: "Day 3 - Media querie and responsive websites"
date:   2018-10-26 11:00:00
excerpt: "With the help of media queries we can define diffrent style adapted to diffrent devices ( ex. computer, tablet, phone, smartwatch) using values ex. width, height."
paermalink: /2018/10/day-3-media-querie-and-responsive-website.html
tags: oldblog
--- 

#### Media queries

With the help of media queries we can define diffrent style adapted to diffrent devices ( ex. computer, tablet, phone, smartwatch) using values ex. width, height.

*See example code on my github*

![Github](/assets/posts/media/github.png) [Github](https://github.com/objectprogr/30dayschallenge/tree/day3MediaQueries)

[Interactive example ( resize your browser and look how change background and layout)](https://www.w3schools.com/css/tryit.asp?filename=trycss_mediaqueries_ex1 "Interactive example ( resize your browser and look how change background and layput)")

[MDN web docs](https://developer.mozilla.org/pl/docs/Web/CSS/Media_Queries/Using_media_queries "MDN web docs")

```css
body {
    background-color: tan;
    color: black;
}
/* On screens that are 992px wide or less, the background color is blue */
@media screen and (max-width: 992px) {
    body {
        background-color: blue;
        color: white;
    }
}
/* On screens that are 600px wide or less, the background color is olive */
@media screen and (max-width: 600px) {
    body {
        background-color: olive;
        color: white;
    }
}
```

#### Responsive websites

This is design technique websites so that its appearance nad layout it automatically adjusts to the size of the browser (computer, tablet, phone etc.).

[Wikipedia](https://pl.wikipedia.org/wiki/Responsive_web_design "Wikipedia")

![Responsive web design](/assets/posts/media/responsive_web_design.jpg)

*Source* [Medium](https://medium.com/level-up-web best-practices-of-responsive-web-design-6da8578f65c4)