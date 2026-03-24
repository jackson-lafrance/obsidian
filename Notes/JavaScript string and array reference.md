---
date: 2026-02-26
tags:
  - javascript
---
## JavaScript string functions
- `str.length`
- `str.toUpperCase()`
- `str.toLowerCase()`
- `str.includes(str)`
- `str.startsWith(str)`
- `str.endsWith(str)`
- `str.indexOf(str)`
- `str.lastIndexOf(str)`
- `str.slice(0, 4)` (first is inclusive last is exclusive)
- `str.substring(4, 10)` (ditto)
- `"   str   ".trim()`
- `"   str   ".trimStart()` (only removes front spaces)
- `str.replace(toreplace, newword)`
- `str.replaceAll(toreplace, newword)`
- `str.split(str)`
- `str.concat([str])` (splatted array of strings to concat)
- `str.charAt(1)` (gets the char at the second spot)
- `str.charCodeAt(1)` (same but gives ascii code)

## Array functions
- `arr.length`
- `arr.sort()`
- `arr.reverse()`
- `arr.push(item)`
- `arr.pop()` (removes end)
- `arr.shift()` (removes front)
- `arr.unshift(item)` (adds item to front)
- `arr.includes(item)`
- `arr.indexOf(item)`
- `arr.slice(0, 2)` (same as string)
- `arr.splice(1, 1, item)` (replaces items from 1 to 1 with item)
- `arr.join(delimiter str)` (joins the array into a string)

## Control flow
`condition ? result : else`

```javascript
for (let i = 0; i < max; i++) {
  // do stuff
}
```

```javascript
for (const item of itemslist) {
  // do stuff
}
```
