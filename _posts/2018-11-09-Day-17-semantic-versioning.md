---
layout: post
title:  "Day 17 - Semantic versionig"
date:   2018-11-09 13:00:00
excerpt: "Versioning our apps helps us keep track of what’s been added/removed at what point. SemVer (Semantic versioning) is a 3-component system in the format of `x.y.z` where:"
paermalink: /2018/11/day-17-semantic-versioning.html
tags: oldblog
categories: homepage
--- 

#### What it is semantic versioning?

Versioning our apps helps us keep track of what’s been added/removed at what point. SemVer (Semantic versioning) is a 3-component system in the format of `x.y.z` where:

- `x`- stands for a major version
- `y`- stands for a minor version
- `z`- stands for a patch

`Major.Minor.Patch.`

### Example

Therefore a package with version `1.3.5` means the following:

| major  | .  | minor  |  . |  patch |   
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
|  1 |   | 3  |   |  5 |   |

### More informations from npm

If a project is going to be shared with others, it should start at `1.0.0`, (though some projects on npm don't follow this rule).

After this, changes should be handled as follows:

| Code status  |  Stage  | Rule  |  Example version |  
| ------------ | ------------ | ------------ | ------------ | ------------ | 
|  First release | New product  |Start with 1.0.0   | 1.0.0  | 
|  Backward compatible bug fix | Patch release  | Increment the third digit  | 1.0.1  |  
|  Backward compatible new feature |  Minor release |  Increment the middle digit and reset last digit to zero | 1.1.0  |   
|  Changes that break backward compatibility |Major release   | Increment the first digit and reset middle and last digits to zero  | 2.0.0  | 

*Source: [npm documentation](https://docs.npmjs.com/getting-started/semantic-versioning)*