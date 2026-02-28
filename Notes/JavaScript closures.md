---
date: 2026-02-26
tags:
  - webdev
  - javascript
---
## Closures
Every function has its own scope, which allows us to have local variables. Functions have access to the scope "above" them in nesting. So if you create a variable in a function, any inner functions have access to it.

A **closure** is when a function remembers the variables in which it was created, even after that scope is done executing. JavaScript uses lexical scoping, which means that inner functions remember the variables in the outer function based on where they were written, not when they are run. Even after the outer function has returned, the inner function keeps access to its variables because the JavaScript engine keeps the scope alive for any active references.
