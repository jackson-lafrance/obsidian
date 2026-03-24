---
date: 2026-03-12
tags:
  - backend
  - javascript
---
## Intro
Express is a minimal and flexible Node.js framework that simplifies servers by handling routing, requests, and responses with less code and better strucutre.

It handles:
- **Routing** (can handle different **URL**s and **HTTP** methods very easily)
- **Request/Response Helpers** (makes it easy to send responses and access request data)
- **Middleware** (Allows us to add reusable functions that process requests)
- **Static file serving** (Makes it easy to serves CSS, images, and JavaScript files)
- **Modular Structure** (Allows us to break up projects and better separate concerns)

It is installed with npm
```bash
npm install express
```

and setup by creating a new **Express** application in our server.  This app object is our web server started.
```javascript
const express = require("express");
const app = express();
```

## Request Response cycle
Express follows a **Request-Response Cycle**.  Which is the full sequence of steps that occur whenever someone makes a request to the moment a response is sent back.

The cycle includes these main steps:
- Request comes in from the browser
- Optional middleware functions are evaluated (this is for parsing, logging, and authentication)
- A router calls the function that matches the path of the request, or sends 404 if none is found
- The matched handler callback function gets evaluated
- Router handler sends a response with either `res.send()` or `res.render()`

### The Router
The **Router** is an internal mechanism that basically matches an incoming request to a specific piece of code that handles it.

A **Route** is a specific URL path and HTTP request method that has a callback function assigned to it.

We define routes and their callback functions with the following syntax
```javascript
app.HTTP_METHOD(FILE_PATH, function(req, res) {
	//CALLBACK FUNCTION BODY
})
```

The method will be either **get**, **post**, **put**, or **delete**.  In the callback function, we can send plain text, JSON, or pre made HMTL strings with the `res.send("")` function.  Whereas if we have a pre-made HTML file we use 
```js
res.sendFile(__dirname + "rel_path.html")
```

Both of these send **200 OK** status by default.

For **POST**, **PUT**, and **DELETE** methods, they use a body which is the extra information that comes with the request.  
For a **POST** it might look like
```js
app.post("/profile", (req, res) => {
	const newUser = req.body;
	users.push(newUser);
	res.status(201).send("Successful user creation");// pick diff status
})
```

And a **PUT** could look like
```js
app.put("/profile/:id", (req, res) => {
	users[req.params.id] = req.body;
	res.send("Member updated") // status = 200 OK by default
	})
```

This gets annoying if we have to write hella gets for all of the html, css, and image files.  Express has a useful function to send only static pages.  It handles it in one line with:

```js
app.use(express.static(__dirname));
```

This tells Express we want to use some **MIDDLEWARE**.  `express.static()` is a built in middleware function that gives any static file.

The order of our **app** calls and other routing/middleware methods matters because Express processes requests in the order that the routes and middleware are defined.  So we have to be careful to put middleware definitions before we define our routes that will use them.

*Bonus note*: If we leave out the **path** parameter in app.get()/app.post()/etc, it matches **any** path for that HTTP method.  You can use it like middleware that runs for all URLs of that method.

## Middleware
In a middleware function, if it doesn't immediately end the request/response cycle, we have to call **next()**, to start the next middleware/route function.

There are three categories of middleware:
1. Bult-in (included with Express)
	1. **express.static()** (serves static files)
	2. **express.json()** (parses incoming JSON objects)
	3. **epxress.urlencode()** (parses URL encoded data (like forms))
2. Third-party (hundreds of options)
	1. **morgan** (logs HTTP request info)
	2. **cookie**-parser (self explanatory)
	3. **cors** (handles cross origin resource sharing)
	4. **helmet** (sets security related HTTP headers)
	5. **express**-session (manages user session data on the server)
	6. **errorHandler** (helps with debugging in dev)
	7. **csurf** (protects against cross site request forgery)
	8. **compress** (compresses response bodies)
3. Custom (functions we make ourselves)
	1. Add properties to the `req` or `res`
	2. Check auth
	3. Log
	4. Block certain ips, etc

```js
app.use(express.static("public`))
```

This is the meta since this just servers a relative file path right next to express.

Express also lets us define a **virtual path prefix**, which is a custom url prefix that doesn't actually exist but helps organize how static files are accessed.

If we want to do this we do
```js
app.use("/static", express.static("public));
```

When we want to send responses, there are three options:
1. `res.status(404).send("body");` choose a custom message for 404
2. `res.sendStatus(404);` no body
3. `res.status(404);` 404 but no body BAD

Express sets the content-type automatically depending on the type of the body variable:

- **string**: text/html
- **buffer**: application/octet-stream
- **object/array**: application/json

If we want a different content type we can select one with
```js
res.set("Content-Type", "text/plan or wtv");
```

However if we want to send a JSON object, then we should use the json() function instead of send() just like this
```js
res.status(200).json(body);
```

Also in express we don't need to url.parse to get query params we can just access them with
```js
res.query.data;
```

we can use the .route function to let us add all the .get, .post guys on the same `app.route("path")`

We can store all this stuff in separate files using
```js
const route = express.Router();

// bla bla bla

module.exports = router;
```

Then in our actual server file:
```js
const routerGuy = require("./routes/guy");

app.use("/guys", routerGuy);

// bla bla bla
```

When we want to get requests from different types of clients expecting different responses from the same route, we can use a function called **format()** to let us serve all versions from the same route.  Picking the right one from their **Accept** header.

Example:
```js
app.get("/products/:id/size/:sz", (req, res) => {
	const product = {
		id: req.params.id,
		name: "Neural Booster",
		size: req.params.sz,
	};
	
	res.format({
		"text/html": () => {
			res.send('html guy'); //website
		},
		"application/json": () => {
			res.json(product)'  //mobile app
		},
		"text/plain": () => {
			res.send(`${product.name} Id: ${product.id}`); // CLI
		},
		default: () => { res.status(406).send("Not acceptable"); }
	})
})
```

To use this with Pug bullshit you have to add some lines to the Express app object.  We need to tell it we will be using PUG as the view engine and where to find the views.

At the top after defining app add:
```js
const app = express();
app.set("view engine", "pug");
app.set("view", path.join(__dirname, "views"));
```

Then we just replace all our **`res.send()`** s that we used to serve html strings with a **`res.render()`** instead like this:
```js
app.get("about", (req, res) => {
	res.render("pages/about", { variables });
})
```