---
date: 2026-02-26
tags:
  - webdev
  - javascript
---
## Synchronous vs asynchronous Code
JavaScript code can be either sync or async.

**Sync** -> code is executed line by line and every statement waits for the previous statement to finish before executing.
**Async** -> code does not have to wait and the next step can start while the current step is still running.

When we use async, the order of completion is not guaranteed. We can make 5 requests, but we won't know in what order they will be answered. The browser only has one main thread to run our JavaScript and how we manage it can impact our page's reaction time, loading speed, and server fetching.

Synchronous code has the advantage that it is simple and predictable, but it means we can only do one thing at a time and can cause lots of freezing while things are loading.

Asynchronous code is harder to predict, but it doesn't block the main thread and lets our browser stay responsive to the user. It's useful for things like fetching data, waiting for user input, and animations/timers.

JavaScript can only execute one instruction at a time, but we can manipulate our code to behave in an async way. We can use the `setTimeout()` function to delay the execution of a certain piece of code without stopping the rest of the code from running. It works like this:
```javascript
setTimeout(callbackFunc, delayInMS)
```

This function will keep track of the time since the timeout was called and keep running the rest of our code, then pause when it is time to run the timeout function. Then it continues to execute the code where it was before the timeout ran out.

`setInterval` is a similar function that sets code to loop based on a timer:
```javascript
setInterval(callbackFunc, intervalInMS)
```

We can nest timeout calls too, this can be useful to retry something later if the first attempt didn't work (getting data), waiting for other work to finish before we run this code, and changing timing on the fly (adjust how often we are checking for data or performing an action as conditions change).
