
# Installing an NPM Package
```shell
npm install name
```
- *this creates a folder called `node_modules` folder*.
- *add `-g` for global installation*.

# Requiring a Package
```js
const name = require('package-name');
```

---

# Package.json
*keeps meta data about the dependencies in our project*

## Create the package.json file
```shell
npm init
```
- *any new package that we install gets added to the list of dependencies inside the package.json file*.
- instead of sending the modules and dependencies, we send the package.json file and the client downloads the dependencies listed inside it.


## Install dependencies from the package.json file
```js
npm install
```

