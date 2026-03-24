---
date: 2026-02-26
tags:
  - javascript
  - backend
---
## Node.js basics
**Node.js** is an open-source and cross platform JavaScript runtime environment where developers can run JS outside of a web browser.  Its used for creating web servers, desktop apps, and multiplayer games.

### Main Features
- Generate dynamic page content using templating engines or frameworks
- Handle crud actions for a server
- Handle form submissions/parse through user input
- Interact with dbs and perform crud operations
- Handle thousands of simultaneous connections easily

### Node.js vs traditional servers
With normal servers, when a client request comes in it blocks the thread until it is done.  This gets really slow under high loads, since threads get tied up when they are waiting.  With node.js though, it uses non-blocking I/O and an event loop to stay responsive even while completing requests.  This makes it more scalable since it can handle more simultaneous requests efficiently.

| Step | Tradional Server (SYNC)                                | Node.js Server (ASYNC)                                               |
| ---- | ------------------------------------------------------ | -------------------------------------------------------------------- |
| 1    | Receives the file request from the client              | ditto                                                                |
| 2    | Sends command to file system to read the file          | ditto                                                                |
| 3    | **WAITS** until the file system finishes reading       | **CONTINUES** with the next request without waiting                  |
| 4    | Once file is read, it sends content back to the client | When file read is done, callback function/event sends file to client |
| 5    | Ready to handle next request                           | Already could handle more requests                                   |

Step three is the main difference.  Normal servers block to access the file/database so that the server can't handle any other incoming requests until its read and returned.  Node.js instead does not block, but adds an event listener to handle the file reading and sending, so while that is going on it is able to take on extra requests.

**Latency** is the time delay between when a request is made and when the response begins. 
![[Latency of common operations.png]]

## Three common server architectures
1. Originally, web servers handled each request by spawning different processes to handle each one separately.  There are two delays from this though, spawning each process is slow since it requires the OS to allocate separate memory, initialize resources, and setup a full execution environment, and since all processes share the same CPU they can hog CPU time and delay the others since they all happen consecutively.  Everyone has their own service team but uses the same kitchen.

![[Process Per Request Web Server.png]]

2. Later people started using threads instead of processes.  Threads are faster since they share the same memory and resources, can be created quicker, and its faster to switch between them.  **Thread pool server** pre-allocates a certain amount of threads to handle client requests.  New requests are placed in the queue and sent to the available threads as they become free, which allows us to reuse resources efficiently instead of creating a new thread for every single request.  **Apache** uses this

![[Thread Pool Web Server.png]]

3. Eventually with the advent of Node.js, the strategy of using a single-threaded event loop that can handle requests asynchronously was invented.  When a request comes in, it's registered as a callback and the event loop keeps running without blocking the request io.  Non-blocking operations are processed right away by the main thread (this is like normal network io, HTTP header handling, or routing logic), while file system access and database queries (blocking/time consuming stuff) is handled by a background thread pool managed by Node.js.  If all these threads are busy, the extra tasks are then going to go into the event queue until a thread becomes available (so they don't block the main thread).  This lets Node.js handle many concurrent requests without alot of overhead, using 1 thread for coordination and then a couple worker threads for heavier operations.

![[Node.js Web Server.png]]

#### \*Node.js doesn't make slow tasks faster, it just makes sure that they don't hold up everything else

## Event loop processing
The event loop itself is iterative and handles all of the callbacks.  Before it starts, Node.js executes **ALL** of our synchronous code (variable declarations, function calls, console.log, etc).  If the code contains [[Asynchronous JavaScript|async]] functions, then they get registered as they are encountered, but they don't get executed right now.

Once everything has been processed at the start, Node.js goes into the event loop, which is the cycle where it processes async operations by executing their callbacks whenever they are ready.  When the queue is empty and there aren't anymore pending tasks, Node.js quits.

There are two types of async tasks: microtasks and macrotasks.
- Microtasks include operations like promise.then(), catch, await, and queueMicrotask() and they get executed immediately after the synchronous code is done.  
- Macrotasks are things like setTimeout(), setInterval() and I/O callback functions.  They get processed in specific parts of the event loop and they only run once **ALL** of the microtasks are finished.

REPEAT {
Process all pending microtasks
Process ready timer callbacks (e.g., setTimeout)
Process pending I/0 callbacks (e.g., OS-level events)
Process new I/0 callbacks (e.g., file read done)
Process scheduled setImmediate () callbacks
Process "close" event callbacks
} UNTIL (there is no more work to do)

By default, node.js comes with 4 worker threads in the pool.  When a heavy task is triggered, it gets sent to one of these threads.  The first four tasks are assigned right away, but then since all of the threads are busy, anything else gets added to the event queue and have to wait for an available thread to start.  

## Module System of Node.js
There are three types of modules in Node.js:
1. Built-in modules (fs, http, path, cypto) (kind of like java.util)
2. File modules (like our own `.js` files)
3. External modules (express, react, lodash, etc)

We use the `require()` function to let Node.js that we need a particular module for our code.  It's like asking Node.js "go get this module and give me whatever its exporting".  This is like \#include <stdlib.h> in C.

We usually store the module in a variable something like: 
```typescript
const hhtp = require("http");
```

Node.js treats every single file like a module and behind the scenes it creates a *module* object for each file, with a special propery called exports, that lets everyone know what parts of the file should be exported/made accessible to other files.  Require function is synchronous and can be slow!!  But node.js caches modules after their are loaded for the first time so its chill.  Module.exports is passed by reference, so any changes made to the exported object from one part of the program will update it everywhere.

## Creating servers
We use the http module to create servers.  This module has a `createServer()` function that takes a callback function as a parameter.  This callback function should have two parameters, the first representing the request from the **client**, and the second representing the **response** to the client.

```javascript
const hhtp = require("http);
let server = http.createServer((request, response) => {
// code to handle the requests/gen the responses
});
```

Once we set this up, we can just tell the server to start listening to incoming requires by calling the `.listen()` function, passing in a port number. 

```javascript
const PORT = 3000;
server.listen(PORT);
console.log(`Server running at http://localhost:$(PORT)`);
```

We can just run this with node like 

```bash
node serverTemplate.js
```

And once the server is running we can open it in the browser and access it.  But right now it won't do anything since our server template doesn't have any code.

\*better way to do this:
```javascript
const http = require("http");
const PORT = 3000;

function requestListener(request, response) {
// code to handle
}

http.createServer(requestListener).listen(PORT);
```

### Response functions
- .writeHead() -> write the response header
- .write() -> write the response body
- .end() -> send the response

### Request functions
- .url -> path/file being requested from the client
