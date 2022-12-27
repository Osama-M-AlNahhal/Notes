# Destructuring
*rather than writing multiple lines of code to extract the properties of an object and assign them into variables with the same name, **Destructuring** does this in a neater way*
```js
let o = {
	var1: "value1",
	var2: "value2",
	var3: "value3"
}
const {var1, var2, var3} = o;
```

---

# Spread
## Objects
*if we want to create an object that's similar to another object in all properties except a few, we can use the spread operator*
```js
let o1 = {
	var1: "value1",
	var2: "value2",
	var3: "value3"
}
let o2 = {...o1, var2: "newValue"}
```

## Arrays
*the spread operator in arrays creates a copy of an array but with extra elements inside it as follows:*
```js
let array1 = ["val1", "val2", "val3"];
let array2 = [...array1, "val4"]
```

---
# rest parameters
*when we want to take an unknown number of arguments into a function, and we care about the order of those arguments, we use the **rest parameters** syntax which stores/treats arguments as an array inside the function's body*

```js
function(...args) {

}
```




---

# .map( )
*this functions works with arrays, it takes a function as an argument and executes this function for each element in the array*
*when the function executes, it takes as input the value of the element in the array, as well as an error object if there's one*
```js
array1.map((element) => {
	//return something
})
```


---
# .filter( )
*this function works with arrays, it takes a special function as an argument, this special function performs some logic based on the input, and returns a boolean value, this boolean value determines if the current element stays in the array or gets deleted from the array*

```js
array1.filter(element => {
	//return a boolean value
})
```


---
# .reduce( )





