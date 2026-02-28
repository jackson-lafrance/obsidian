---
date: 2026-02-26
tags:
  - webdev
  - javascript
---
## Shallow and deep copies
Primitive types are passed by value (string, numbers, etc).
Arrays, objects, and functions are passed by reference.

**Spread notation** creates a shallow copy of an object (doesn't go deeper to copy objects in the object):
```javascript
let clone = {...original}
```
- Also works on arrays
- Can use it on a string to extract the letters into an array
- Can use it to merge objects like:
```javascript
let merged = {...original1, ...original2} // second one takes precedence
```

Otherwise we can use `Object.assign()` to copy the content from one object to a new one:
```javascript
let newone = Object.assign({}, oldone)
```

If we want a deep copy we need to use JSON functions:
1. Convert to JSON: `let json = JSON.stringify(original)`
2. Convert it back to an object: `let copy = JSON.parse(json)`

This creates a deep copy where all of the inner objects are also cloned.
