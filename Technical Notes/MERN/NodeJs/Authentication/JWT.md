# Dependencies

```shell
npm i express jsonwebtoken dotenv bcrypt
```

```shell
npm i --save-dev nodemon
```

*running scripts defined in the package.json file*
```shell
npm run start
```


---

# Code

```js
//loads variables from the .env file to `process.env` variables
require('dotenv').config();

const Express = require('express');
const app = Express();
const jwt = require('jsonwebtoken');
const bcrypt = require('bcrypt')



app.use(express.json());

let users = [];


app.get('/data', authenticateToken, (req, res) => {
	//after executing the `authenticateToken` middleware function, we now have access to the `user` object
	let relevantData = getDataFromDb(req.user);
	res.json(relevantData);
})

app.post('/login', async (req, res) => {
	//-------------Authenticate user----------------
	
	const user = getUserFromDb(req.body.name);
	if (user == null) {
		res.status(400).send('Cannot find user');
	}
	//compare the password from the request to the password from the database
	try {
		if (await bcrypt.compare(req.body.password, user.password)) {
			res.send('Success');
		} else {
			res.send('Not Allowed');
		}
	} catch {
		res.status(500).send();
	}

	//--------------JWT----------------
	user = {
		name: req.body.username
	}
	const accessToken = jwt.sign(user, process.env.ACCESS_TOKEN_SECRET);
	res.json({accessToken: accessToken});
})

app.post('/users', async (req,res)=>{
	try {
		const salt = await bcrypt.genSalt();
		const hashedPassword = await bcrypt.hash(req.body.password, salt);
		const user = { name: req.body.name, password: hashedPassword}
		users.push(user); //or push it to the database
		res.status(201).send();
	} catch {
		res.status(500).send();
	}
})



//middleware function to be used with each request to the server to authenticate the user's token
function authenticateToken(req, res, next) {
	//we get the token from the authorization field in the header, which is in the following form
	//`Bearer akhfiebfsdnflqehpih13iornon.io2rionoiadjhpfqh97\adf`
	const authHeader = req.header['authorization'];
	const token = authHeader && authHeader.split(' ')[1];
	if (token == null) {
		return res.sendStatus(401);
	}

	jwt.verify(token, process.env.ACCESS_TOKEN_SECRET, (err, user) => {
		if (err) {
			return res.sendStatus(403);
		}
		req.user = user;
		next();
	})
	
}


```

*generate 64-byte secret and store it in the `.env` file*
```shell
require('crypto').randomBytes(64).toString('hex')
```


