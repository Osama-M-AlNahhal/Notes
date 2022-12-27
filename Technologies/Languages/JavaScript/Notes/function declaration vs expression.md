# Function declaration
- *hoisted to the top*
```js
function name(input) {
	//do something
}
```

# Function expression
- *not hoisted to the top*
- uses anonymous functions 

```js
const name = function(input) {
	//do something
}
```
or 
```js
const name = (input) => {
	//do something
}
```