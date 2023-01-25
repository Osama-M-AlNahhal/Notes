
# Server
the http module is a core nodejs module that is used to create servers and work with http requests

## Import module

```javascript
const http = require('http');
```

----

## Create a server

```javascript
const server = http.createServer((req, res) => {
	console.log('this function is called every time a request is made to the server');
});

server.listen(3000, 'localhost', () => {
	console.log('this fires only once to indicate that the server is now listening');
});
```

*this is just a code file, the server needs to run first for it to work, to run a server we use node to run the javascript file in the command line using `node fileName`

---

### req

```javascript
req.url
req.method
```

----

### res

#### setting a header
```javascript
res.setHeader('header-name', 'header-value');
```

#### adding data to the response
```javascript
res.write(data);
```

#### sending the response
```javascript
res.end();
```
*this can also be used to send data if there's only one thing to send in the response*
```javascript
res.end(data);
```

#### status codes

```javascript
res.statusCode = 404; //not found
res.statusCode = 301; //redirect
```


----

### Routing

```javascript
let path = 'path to views folder';
switch(req.url) {
case '/':
	path += 'index.html';
	res.statusCode = 200;
	break;
case '/about':
	path += 'about.html';
	res.statusCode = 200;
	break;
default:
	path += '404.html';
	res.statusCode = 404;
	break;
}
```

*using the `path` to select and send the appropriate html file from the views folder*
```javascript
fs.readFile(path, (err, data) => {
	if (err) {
		console.log(err);
	} else {
		res.end(data);
	}
})
```


#### redirects
*to redirect from one url to another, we set the `Location` header to the new url during routing*
```javascript
res.statusCode = 301;
res.setHeader('Location', '/new');
```

----
	
## Import module

```javascript
const http = require('http');
```

----
