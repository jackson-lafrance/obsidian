---
date: 2026-02-26
tags:
  - frontend
  - backend
---
## Internet history
- First web pages were made using HTML, mostly just plain text and static
- Then CSS (Cascading Style Sheets) were invented to control appearance and layout separately
- JavaScript to add interactive features like buttons and forms

**Terms**
- Content is the text, images, videos, and interactive pieces displayed on a webpage for visitors to view or use
- A web resource is any item on the web with its own URL (address)
  - Webpages
  - Image files
  - Downloadable documents
  - APIs
- A Uniform Resource Locator (URL) is a web address we type into a browser to find a specific web resource (Like a home page)
- Website is a collection of pages all together and a web app is a program we can use in the browser

## Web programming
We are going to explore both front-end (everything the user sees and interacts with in their browser) and back-end (everything happening behind the scenes on the server). There are three main aspects of a web page that are combined together:

- Structure - the content of the webpage = HTML
  - Headings
  - Text
  - Buttons
- Presentation - the style and layout of the webpage = CSS
  - Colors
  - Fonts
  - Spacing
- Behaviour - how the webpage interacts with the user = JavaScript
  - Validating forms
  - Animations
  - Dynamic content

This leads to separation of concerns which is the process of organizing a program so that different parts handle distinct, independent aspects of functionality. This makes code easier to manage, understand, and maintain. At the core, almost everything we do on the web is a conversation between a client (browser/app) and a server (software/api that provides resources).

The request to the server uses one of four methods:
- Ask for a page, data, image or some other file
- Send new data to the server
- Update existing data
- Remove data

The server will then respond with a status code (like "everything is fine", "that doesn't exist", "help everything is broken") and often some content (webpage, code, image, etc). Everything else in this whole course is ultimately just part of making, handling, and responding to these requests.

If you keep this request in -> response out cycle in mind, everything we learn will fit together a lot easier. All the different tools we will learn just make our work easier. Build faster, organize things better, and add features.
