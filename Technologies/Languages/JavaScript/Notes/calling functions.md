If we have a function defined, then there are more than one way to call it:
- the normal way:  add paranthesis after it to call it
- Another way: if we have a function that makes use of the `this` keyword and we want to call it on a specific object (but the function is not defined inside that object) then we can use the `.call()` function method ( #need-further-research ) as follows:

```js
//this is the same as if the `functionName` was defined inside the `ObjectName`
const results = functionName.call(objectName);
```
