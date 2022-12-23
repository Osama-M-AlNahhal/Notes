# 2 - Syntax Basics & Types
## array methods
### join
*joins all elements in the array into a string separated by the delimiter we choose*
```js
arrayName.join(',');
```

### indexOf
*find the zero-based index of the first occurance of a value in an array*
```js
arrayName.indexOf('value');
```

### concat
*create a new array and copy the elements both arrays into it then return it*
```js
array1.concat(array2);
```

### push
**destructive method**
*add a value to the end of the array, and return the new number of elements in the array*
```js
array1.push('value');
```

### pop
**destructive method**
*remove a value to the end of the array, and return that value*
```js
array1.pop('value');
```


### forEach
*takes a function and loops over each element of an array and executes this function*
```js
array1.forEach((element, index) => {
	
});
```

---

# 4 - Functions

## Function declaration vs expression
*function declarations are hoisted to the top of the file*
```js
function name() {

}
```
*function expressions always end with a semicolon, and are NOT hoisted to the top of our file*
```js
let name = function(){

};
```

*using arrow functions*
```js
let name = () => {

};
```


## default values
*by assigning a value in the function expression*
```js
let name = (x = 1, y = 'default value') => {

};
```


## Arrow functions vs normal functions
- in normal functions: `this` refers to the object that the function is in
- in array functions: `this` refers to the object that the function was called inside its scope, meaning if you call an array method from the global scope, `this` refers to the global object.


## shorthand syntax for methods
```js
let o = {
	attr1: "value",
	method1() {
	},
	method2() {
	}
}
```

---

# 5 - Objects
