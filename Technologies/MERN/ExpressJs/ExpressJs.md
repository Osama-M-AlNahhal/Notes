*using express inside our project:*
```js
const express = require('express');
const app = express();
```

*registering our [[Template Engines]]*
```js
app.set('view engine', 'ejs');
```

*listening for requests*
```js
const port = process.env.PORT || 3000;
app.listen(port, ()=> {console.log(`listening on port ${port}...`)});s
```

*listening for a get request*
```js
app.get('/', (req, res) => {
	//handle request

	//send response
	res.send('something');
});
```

## Routing
```js
app.get('/', (req, res) => {
	//handle request
	//send response
	res.send('something');
});
app.get('/about', (req, res) => {
	//handle request
	//send response
	res.send('something');
});
```

*listening for a specific file in the url*
```js
const { ObjectId } = require('mongodb')

if (ObjectId.isValid(req.params.id)) {
	db.collection('books')
	.findOne({_id: new ObjectId(req.params.id)})
	.then(doc => {
		res.status(200).json(doc)
	})
	.catch(err => {
		res.status(500).json({error: 'Could not fetch the document'})
	})
} else {
	res.status(500).json({error: 'Could not fetch the document'})
	}
});
```
## Sending responses
### entire file
```js
res.sendFile('./views/file.extension', { root: __dirname});
```

### specific data 
```js
res.send('something');
```

### json 
```js
res.json(jsonObject);
```

## Redirects
```js
res.redirect('/file'); //no extension
```

----

## [[Middleware]]

- *middle ware is code that's executed on the server between the time the request comes in and the response is sent out*
- *routing code with `app.get()` is executed sequentially in order, until the response is sent back, then it stops*
- *we can use `app.use()` fires for every single request, but only if it's reached inside the code, then execution hanges at its end, and we need to decide what to do next*
- to go to the next Middleware, we use `next()`

![[Middleware visualization.png]]

### app.use() and next()
- *after the first middleware is executed, the flow is halted, and we have to explicitely tell the program to continue executing the code, this is done by taking the `next` function and executing it
```js
app.use((req, res, next) => {
	//proccess some stuff
	next();
})
```

----

### 404 Page
*at the very end of the routing code, we add this:*
```js
app.use((req, res) => {
	res.status(404).sendFile('./views/404.html', {root:__dirname});
});
```


---

## [[Template Engines]]

---

## [[Mongosh]]

***its best practice to keep all database connection related code in a module (separate `.js` file) called db.js***
	
### Exporting the MongoDB code inside an express application:

- *we first need to get the mongoClient object which will allow us to connect to our MongoDB database*
```js
const { MongoClient } = require('mongodb');
```

- *then we prepare to export the connection to the database so that we can use it somewhere else in our application*
```js
module.exports = {
	connectToDb: () => {
		MongoClient.connect('mongodb://localhost:27017/databaseName')
		.then((client) => {
			dbConnection = client.db();
			return cb(); //callback function
		})
		.catch (err => {
			console.log(err);
			return cb(err);
		});
	},
	getDb: () => dbConnection
}
```

***inside our `app.js` file, we import the exported data from our `db.js` file as follows:
```js
	const {connectToDb, getDb} = require('./db');
```

***inside our `app.js` file, we first connect to the database using `connectToDb()` then check for errors during the connection, if the connection is successful then start listening for requests***
```js
let db;
connectToDb((err) => {
	if (!err) {
		app.listen(3000, () => {
			console.log('started listening to port 3000');
		});
		db = getDb();
	}
})
```


### Proccessing data
```js
	let items = [];
	db.collection('collectionName')
	.find() //returns cursor
	.sort({ key: val}) //returns cursor
	.forEach(item => {
		//asyncronous method to handle items one at a time
		items.push(item);
	})
	.then(() => {
		res.status(200).json(items);
	})
	.catch(() => {
		res.status(500).json({error: 'could not fetch the documents'});
	});
```

#### how the find() method works
- the find method returns a curser that points to a group of collections
- the cursor allows us to handle collections uisng `toArray()` an `forEach()` 
- the `find()` method returns batches, one batch at a time, default size of a batch is 101 documents



---
## Indexing
![[Indexes visualization.png]]

---

## Operations on the db
### Insert

```js
app.use(express.json()); //this is needed to get the body of the request

app.post('/items', (req, res) => {
	const item = req.body; //get the item from the body of the response
	
	db.collection('items')
	.insertOne(item) //insertion takes time so its an asyncronous function
	.then(result => {
		res.status(201).json(result)
	})
	.catch(err => {
		res.status(500).json({err: 'Could not create new document'})
	});
});
```


### Delete
```js
app.delete('/items/:id', (req, res) => {
	if (ObjectId.isValid(req.params.id)) {
		db.collection('items')
		.deleteOne({ _id: new ObjectId(req.params.id) })
		.then(result => {
			res.status(200).json(result);
		})
		.catch(err => {
			res.status(500).json({error: 'Could not delete document'});
		})
	} else {
		res.status(500).json({error: 'Could not delete document - Invalid id'});
	}
});
```

### Patch (update)
```js
app.use(express.json()); //this is needed to get the body of the request

app.patch('/items/:id', (req, res) => {
	const updates = req.body;
	
	if (ObjectId.isValid(req.params.id)) {
		db.collection('items')
		.updateOne({ _id: new ObjectId(req.params.id) }, {$set: updates})
		.then(result => {
			res.status(200).json(result)
		})
		.catch(err => {
			res.status(500).json({error: 'Could not update document'})
		})
	} else {
		res.status(500).json({error: 'Could not update document - Invalid id'})
	}
})
```

### Routing (getting data batches from db and sending them to user)
```js
app.get('/items', (req, res) => {
	// current page
	const page = req.query.p || 0 //to get the ?p=... from the url
	const booksPerPage = 3
	let books = []
	
	db.collection('items')
	.find()
	.sort({author: 1})
	.skip(page * booksPerPage)
	.limit(booksPerPage)
	.forEach(book => books.push(book)) //needs some time, so its an async. function
	.then(() => {
		res.status(200).json(books)
	})
	.catch(() => {
		res.status(500).json({error: 'Could not fetch the documents'})
	})
})
```


---

## Express router
*a built-in express [[Middleware]] that allows us to take out all the routing code from our main `.js` file into a separate file, and then inside this new `.js` file we connect all routing code into the router, then export the router and use it as middleware inside our original code, making it cleaner and easier to manage*

### Use
1. create a new `routes` folder, and add a `nameRoutes.js` file inside it
2. inside this file:
	1. require express, and the database handler from inside the `models` folder
	2. `const router = express.Router();`
	3. add all the routing code and replace the `app.get()` with `router.get()`
	4. at the very end we add `module.exports = router;`
3. inside our original `app.js` we require the `nameRoutes.js` file into a variable (say: nameRouter )
4. we then use 'nameRouter' this as middleware (`app.use(nameRouter);`)
5. to take this a step further, we can use MVC as follows:


### MVC
