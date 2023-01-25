
[Official site](ejs.co)

----

## installation
```bash
npm install ejs
```


## Use
```js 
let ejs = require('ejs');
let people = ['geddy', 'neil', 'alex'];
let html = ejs.render('<%= people.join(", "); %>', {people: people});
```

----

## How it works
- *the view engine looks by default for the `views` folder for the `.ejs` files (similar to html).*

- *we can change this, if we want a specific folder for ejs views, but usually we don't and we just use `views*

- *instead of sending a file as a response, we `render()` the `.ejs` files which proccesses them then sends them as a response*

----

## Rendering and passing data
- *we pass data to the engine in the form of an object, which is used during the rendering proccess*
```js
res.render('ejsfile', {title: 'home'}); //no extension, ejsfile is inside the views folder
```
 
----

## Coding inside .ejs files
- *we use the ejs tags `<% %>` , `<%= %>` and `<%- %>`*

```js
<% const name = 'osama' %>
<%= name %>
```

----
#### difference between ejs tags:

`<% %>` : used to write javascript code inside
`<%= %>` : used to output a string into the file, escapes special characters.
`<%- %>` : doesn't escape special characters, used to include partials

---

### partials
- *parts of the code that are repeated in multiple pages, so its faster and more efficient to just have them in a separate file, and include them in each page, that way if we want to change something, we change it in one location instead of several*
- *create a subfolder inside the `views` folder called `partials` with `.ejs` files inside it (each file contains code we want to repeatedly use, ex: navbar)*
```js
<%- include('./partials/partial.ejs') %>
```
*note: relative path (relative to the current `.ejs` file)*.



