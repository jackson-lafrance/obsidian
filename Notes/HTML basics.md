---
date: 2026-02-26
tags:
  - webdev
  - frontend
---
## The Basics
**HTML** stands for **H**yper**T**ext **M**arkup **L**anguage
- The word **hypertext** simply means "text with links". That means that hypertext can be clicked-on (link)
- The word **markup** refers to the symbols or tags used to annotate text so that the web browser can understand how to structure and display it. It's basically a way of labelling text with extra info for the browser to take note of so that it knows what to do with the content. These tags are not visible to the webpage, though we can view the source code of a webpage to see them.
- HTML is not a **programming** language it is a **markup** language. Language just means it follows a specific syntax and allows structured communication between the person and the browser.

The default filename most web servers look for when loading a website or folder is called index.html.

### Basic HTML file
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My Simple Webpage</title>
  </head>

  <body>
    <h1>Hello Everyone!</h1>
    <p>This is our first COMP 2406 webpage!</p>
  </body>
</html>
```

### Some tips
- There are six different header tags (h1-6)
- Use only `one` \<h1> per page
- Don't skip levels

Can force a line break with a **\<br>** tag and can force single spaces by using **\&nbsp** (non-breaking space). **THIS IS BAD PRACTICE USE CSS**.

Whenever we are structuring webpage content, it would be good to also use **\<section>** tags for accessibility. We will use a similar tag **\<div>** for styling later.

## Other Common HTML Tags
**\<table>** allows us to organize our content into rows and columns. With these tags, we can add a caption, header, and body to the table using their own wrapping tags (caption, thead, tbody). Then we use **\<tr>** to indicate each row of the table. For each cell of the table we can use **\<th>** to wrap information that goes in the cell of that table's header and **\<td>** to wrap information that goes in a cell of the body of the table.

At the beginning of the table we can use **cellpadding** and **cellspacing** to define the space all around the inside of the table cells and around the outside of cells respectively. We shouldn't use these though but instead use CSS.

Another useful set of tags we use are ones for creating lists. **\<ul>** creates unordered lists and **\<ol>** creates ordered lists (numbered). Then we wrap each list item in a **\<li>** tag to separate them.

## Images, Links, and Forms
We add images to our webpages with the self-closing **\<img>** tag which has this format:
```html
<img src="filename.fileextension" alt="alt text description">
```

The **src** indicates the name of the file, which includes the path to the file/URL. There are a few options for this:
- **Relative URL**
  - src="cake.jpg" if the file is in the same folder
  - src="images/cake.jpg" if the file is in a subfolder
  - src="./images/cake.jpg" same as above
  - src="../images/cake.jpg" go back up one folder then go into the images folder
  - src="../../images/cake.jpg" go back up two folders
- **Absolute URL** (full web address)
  - src="madeup-example.com/images/cake.jpg"
- **Local file system path** (not recommended)
  - src="C:/Users/Me/Pictures/cake.jpg"

In the header we can also tell the browser to display a **favicon** (The icon in the top left corner in the tab list). In the **\<head>** section of the webpage, just below the title tag we add this snippet:
```html
<link rel="icon" href="imageurl.jpg">
```
Here, the **rel=** attribute stands for the relationship between the current html document and the linked resource. In our case, we are specifying the icon we want to supply for the webpage. The **href=** attribute stands for **hypertext reference**. In the case of specifying an icon, we should supply the path to the image file. Icon images are either **.ico** (best option), **.png** (allows transparency), or **.svg** (scalable vector for newer browsers)

When using links with the **\<a>** tag, we need to specify more than just the href. By adding `target="_blank"`, this will make sure that the link will open in a new window (\_self is the default which opens the text in the same window)

The final tag that we will look at is the **\<form>** tag which is used for like email and password forms. In a form we must specify an **action** and a **method**. The action attribute lets us specify the URL where we want to send the form data to when the submit button is pressed. The method is either "get" or "post" (stay tuned).

The body of a form consists of **\<label>** and **\<input>** tags. Label is used to specify a title for inputs. The value of **for=** in the label should match the value of **id=** in the input so they can be connected. There are many options for the **\<input>** tag's **type** attribute:
- "text" - a regular text field
- "password" - a hidden text field
- "email" - email address text field
- "checkbox" - checkbox...
- "radio" - a radio button
- "submit" - submits the form
- "file" - a file upload

When we submit a form by pressing the submit button, three things happen. First the data in the field is collected. Then the browser sends the data to the server using the specified method (get or post). Then the server processes the data and returns a response. Below is an example form.

```html
<form action="https://example.com/apply" method="post">
  <label for="first">FirstName:</label>
  <input type="text" id="first" name="firstname">

  <label for="email">Email:</label>
  <input type="email" id="email" name="email">

  <input type="submit">
</form>
```
