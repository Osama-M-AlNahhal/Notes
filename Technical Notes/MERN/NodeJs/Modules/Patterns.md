
# Requiring an Entire Directory
*require all JavaScript files from within a single directory*

1. Create a `index.js` file inside that directory.

2. in this `index.js` require each of the JavaScript files in the directory.
```js
const x = require('x.js');
```

3. create an object in the `index.js` file which contains all the imported modules.
```js
const forExport = {
	x: x,
	y: y
};
```

4. export this object
```js
module.exports = forExport;
```

5. import the folder into our file
```js
const name = require('./folderName');
```
*`./` means it's a folder, and NodeJs automatically looks for a file named `index.js` and requires it*

----
