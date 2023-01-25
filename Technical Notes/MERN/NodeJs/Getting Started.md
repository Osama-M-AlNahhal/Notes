# Install Dependencies

``` shell
npm install node express nodemon node-cron mongodb 
```

---

# Folder Structure

Server
	public
		style.css
	models
	views
		inc
			header
			footer
	controllers
	routes
	index.js

---

# Requirements
*inside index.js*

## [[ExpressJs|Express]]
```js
const Express = require('express');
const app = Express();

app.set('view engine', 'ejs');

//set the public folder (css files inside it)
app.use(express.static('folderName'));

//listen on this port
const port = process.env.PORT || 3000;
app.listen(port, ()=> {console.log(`listening on port ${port}...`)});

/*------------------------------------------------------------
						Middleware
-------------------------------------------------------------*/
// for parsing application/json
app.use(bodyParser.json());

// for parsing application/x-www-form-urlencoded
app.use(bodyParser.urlencoded({ extended: true }));

app.use((req, res, next) => {
	//proccess some stuff
	next();
})

/*------------------------------------------------------------
						Routing
-------------------------------------------------------------*/
app.get('/', (req, res) => {
	//handle request

	//send response
	res.render('file');
});

```


## [[MongoDb]]
```js
const mongodb = require('mongodb');

```


## [[Mongoose]]
```js

```


## [[ws|WebSocket]]
```js
const WebSocket = require('ws');
const server = new WebSocket.server({ port: 8080 });

server.on('connection', socket => {
    socket.on('message', message => {
        socket.send(`welcome to our shop mr. ${message.clientName}\nHow can i help you?`);
    })
})
```


## [[Socket.io]]
```js

```

