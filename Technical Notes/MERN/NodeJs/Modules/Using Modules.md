# Modules
- *code from a `.js` file that's exported, and can be imported and used in other `.js` files*


## CommonJs vs ES6 modules
### CommonJs 
`require` is just a function (evaluated at runtime, we don't know anything ab it before that)
`require` can be inside a function
`require` is only executed and evaluated when we reach it in the execution of the code, and not before that

### ES6
`import` is static, and is evaluated at compile time.
`import` must live only inside root (ex: can't use it inside an if statement).
`import` statements are hoisted to the top, so it doesn't matter where we write them in our code.

---

## CommonJs Modules
*in things like nodejs, exporting and importing is done as follows:*
```js
module.exports = functionName; //for exporting a single function
```

```js
//for exporting multiple functions
module.exports = {
	function1,
	function2,
	function3
}
```

*and importing is done as follows:*
```js
const functionName = require('path');
```

---

## ES6 Export & Import Types

### Named
```js
export const A = 'value'; //named export
```

```js
import {A} from 'path.js'; //named import
```
---

### Default
```js
export default 'value'; //default export
```

```js
import anyName from 'path.js'; //default import
```
---

### Rename in export
```js
export {x as y}; //rename in export
```

```js
import {y} from 'path.js'; //import
```

---

### Rename in export & import
```js
export {name1, x as y}; //named export
```

```js
import {y, name1 as z} from 'path.js'; //named import
```
