---
date: 2026-02-26
tags:
  - webdev
  - javascript
---
## Special functions
**Higher-order functions** are functions that return other functions or take another function as a parameter.
**Callback functions** are functions that we pass to other functions.

Arrays have useful higher order functions:
- `arr.forEach(item => func)` - do stuff for each item in the array
- `arr.map(item => func)` - change every item in the array and create a new array of it
- `arr.filter(item => bool)` - create a new array with only the items that pass the test
- `arr.find(item => item.startsWith("s"))` - find the first element matching the condition
- `arr.reduce((total, currentValue) => func, initialValue)` - sums everything in the array into one total (could be string, int, or object)
