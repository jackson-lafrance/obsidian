---
date: 2026-02-26
tags:
  - webdev
  - javascript
  - frontend
---
## The DOM (Document Object Model)
The DOM is a tree of all **HTML Nodes**. This includes:
- HTMLElement (\<p> etc)
- CharacterData (text or comments)
- Document object (the whole thing)
- Attr (attributes)

### The BOM (Browser Object Model)
This is a set of objects provided by the web browser that lets JS interact with the browser itself. They include:
- **window** (global object for the browser and parent of everything)
- **navigator** (provides information about the browser like platform and stuff)
- **screen** (screen width, height, and color depth)
- **location** (lets us get/set the URL of the current page)
- **history** (allows us to navigate the browser history (back/forward))
- **alert, confirm, prompt** (dialog boxes provided by the browser through the window object)
- **setTimeout, setInterval** (timing methods via window)

### Difference
DOM lets us interact with elements of an HTML page, the BOM gives us control over browser features outside the document.

The root node of the DOM tree is the document itself, we can access it by using the `document` variable and then we have access to all the elements that make up the page.

Another important thing is that with HTMLCollections, we can't actually access most list methods but with a NodeList we can.

### How to use the DOM
These are the ways to get elements in the webpage based on what "kind of thing" they are:

```javascript
getElementById(id)              // Finds one element by its id
getElementsByClassName(className) // Returns an HTMLCollection of all elements with class
getElementsByTagName(tag)        // All elements with a tag name
querySelector(selector)          // Finds the first element that matches a CSS selector
querySelectorAll(selector)       // Finds all elements that match a CSS selector
```

Since nodes are arranged in a tree, we have the usual parent/child relationship available to us. Once we have a node, we can access various attributes/properties for that node:

- **nodeName** - name of the node ("DIV", "#text", etc)
- **nodeType** - type of node (1 = Element, 3 = Text, etc)
- **nodeValue** - value of a text or comment node
- **textContent** - full text content of the node and its descendants
- **innerHTML** - HTML markup contained within the element
- **outerHTML** - HTML markup including the element itself

Once we get an element with something like:
```javascript
const aMenu = document.getElementById("menu")
```
We could then ask these from `aMenu`:
- **parentNode** - the node's immediate parent (or null if it has none)
- **childNodes** - the NodeList of all child nodes (including text nodes)
- **children** - live updating HTMLCollection of element children only
- **firstChild** - the first child node (text or element)
- **firstElementChild** - the first child element
- **lastChild** - same as firstChild but last
- **lastElementChild** - same as firstElementChild but last
- **nextSibling** - next sibling node (text or element)
- **nextElementSibling** - next sibling element
- **previousSibling** - previous sibling node (text or element)
- **previousElementSibling** - previous sibling element

### Tree modification
There are also lots of tree-modification methods:
- **.appendChild(node)** - adds a node to the end of a child list
- **.insertBefore(newNode, referenceNode)** - inserts a node before another one
- **.removeChild(node)** - removes a child node
- **.replaceChild(newNode, oldNode)** - replaces a child node
- **.cloneNode(deep)** - creates a copy of the node (deep = true copies all children too)

## Changing element contents and attributes
There are different things we can do to a document:
1. Changing text content
2. Changing html content
3. Clearing element content
4. Modifying attributes
5. Updating form values

We use `.textContent=`, `.innerHTML=`, `.src=`, `.alt=`, `.value=`, `.checked=`

The difference between `.innerHTML` and `.textContent` is that innerHTML lets us add tags in the text that we are supplying.

**setAttribute()** function lets us set a specific attribute like href or target to a new value.
