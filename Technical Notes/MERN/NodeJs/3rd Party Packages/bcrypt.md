*a package that provides asyncronous cryptographic functions for nodejs*

```shell
npm i bcrypt
```

```js
const bcrypt = require('bcrypt');
```

# Hashing
*for passwords*

**Note :**
- These functions are all asyncronous, meaning that the function we're calling bcrypt must be asyncrnous (add `async`).

*generate salt then hash the password with the salt*
```js
const salt = bcrypt.genSalt(); //optional: genSalt(numberOfRounds)
const hashedPassword = await bcrypt.hash(password, salt);
```

*doing both in one step*
```js
const numberOfRounds = 10;
const hashedPassword = await bcrypt.hash(password, numberOfRounds);
```

**Note :**
- bcrypt store both the unique salt and the hashed password into the `hashedPassword` variable separated by `.`, which looks like this: `jiqeonf=031hf1i3nfiefjqow.iqjwkfnadga867gae9as2hjf`
- bcrypty then uses this salt to decrypt the password.


---

# Compare
*password from user with hashed password from database*

```js
if (await bcrypt.compare(userPassword, hashedPassword)) {
	//success
} else {
	//failure
}
```
- this method authomatically prevents replay attacks.