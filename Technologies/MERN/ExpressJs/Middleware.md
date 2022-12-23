# Importing middleware
*this is done using the require method as follows* 
```js
const name = require('middleware.path');
```

# Useful Middlewares List

## morgan
[http request logger middleware for nodejs](https://www.npmjs.com/package/morgan)

**Use:**
```js
const morgan = require('morgan');

app.use(morgan('dev')); //div is an output format, other formats: tiny, 
```

#3rd-party #middleware 

---

## express.static
*choose a folder to make public and allow access to it from the client side*

**Use:**
```js
app.use(express.static('folderName'));
```

**IMPORTANT NOTE:** when we link/refer inside our code to something from the public folder, we don't need to use the path+file name, because express will automatically look inside the public folder


#native #middleware 

---

## express.urlencoded
*takes all the url parameters and creates an object that lets us access these parameters more easily*

**Use:**
```js
app.use(express.urlencoded({ extended: true }));

//then we use `req.body` to get an object which has all the parameters that were sent to us from a form on the front end or from the url
```

**IMPORTANT NOTE:** when we link/refer inside our code to something from the public folder, we don't need to use the path+file name, because express will automatically look inside the public folder


#native #middleware 