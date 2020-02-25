---
layout: post
title:  "Day 16 - Package managers - npm and Yarn"
date:   2018-11-08 13:00:00
excerpt: "A package manager or package management system is a collection of software tools that automates the process of installing, upgrading, configuring, and removing software packages for a computer's operating system."
paermalink: /2018/11/day-16-package-managers-npm-yarn.html
tags: oldblog
--- 

### What it's package managers?

A package manager or package management system is a collection of software tools that automates the process of installing, upgrading, configuring, and removing software packages for a computer's operating system.

*Source - [Wikipedia](https://en.wikipedia.org/wiki/Package_manager)*

### Npm (Node Package Module)

![npm](/assets/posts/media/npm.png)

npm is the package manager for JavaScript and the world’s largest software registry. We can use npm to:

- Adapt packages of code to your apps, or incorporate packages as they are.
- Download standalone tools you can use right away.
- Run packages without downloading using npx.
- Share code with any npm user, any where.
- Restrict code to specific developers.
- Form Orgs (organizations) to coordinate package maintenance, coding, and developers.
- Form virtual teams by using Orgs.
- Manage multiple versions of code and code dependencies.
- Update applications easily when underlying code is updated.
- Discover multiple ways to solve the same puzzle.
- Find other developers who are working on similar problems and projects.

*Source - [npm documentation](https://docs.npmjs.com/getting-started/what-is-npm)*

#### How to start with npm

Go to [npm website](https://www.npmjs.com/) and find interested package using searchbar - for example, I looking for bootstrap.

Next install package in your project:

`npm install bootstrap`

And now you can use bootstrap in your project.

But better way is using `package.json` - read npm [documentation](https://docs.npmjs.com/getting-started/using-a-package.json)

### Yarn

![yarn](/assets/posts/media/yarn.png)

Yarn is a package manager for your code. It allows you to use and share code with other developers from around the world. Yarn does this quickly, securely, and reliably so you don’t ever have to worry.
Yarn dosn`t have a own repository, but using others repositories ex. npm repository. Yarn is faster than npm, and it is a fact. Check test - [npm vs yarn](https://medium.freecodecamp.org/npm-vs-yarn-benchmark-9b456de4aa96)

#### How to using yarn?

This is nice [tutorial](https://yarnpkg.com/en/docs/install#windows-stable)* which help you start with yarn.

Similar how with `npm`, we must find packages. Go to *[website](https://yarnpkg.com/en/)* and use searchbar. I looking for bootstrap.

Next We install the package:

`yarn add bootstrap`

And We can use bootstrap in our project.

For more informations read a [documentation](https://yarnpkg.com/en/docs).

## Conclusion

Personally, I using `yarn`, because it`s faster and more confortable in usage for me.