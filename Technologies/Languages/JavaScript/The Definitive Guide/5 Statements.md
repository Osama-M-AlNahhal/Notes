# Loops
## for
```js
for (initializer; test; increment) {

}
```

## for/in
```js
for (property in object) {

}
```
- *this is evaluated each time as property=value*
- *can be used to create an array of properties*
- not all object properties are enumerated/counted
| enumerable | non-enumerable |
| ---------- | -------------- |
| user defined properties           |       built-in methods (ex: toString properties)         |

### enumeration order
- **simple object:** oldest defined first 
- **complex (w/ inheritence):** complex (and quite irrelevent tbh)

---
# Jumps
## Labled statements
- *only meaningful when we label something with a body (like a loop)*
- labels have a different namespace than variables (a label and a variable can have the same name but still be different).
```js
Label: statement {

}
```

## break
- *must be used inside a loop/switch, otherwise we get an _error_ ( #need-further-research )*
- breaks out of the inner most loop

### break label;
```js
break label;
```
- *breaks out of the block that the label starts*
- *if no label is found -> syntax error ( #need-further-research )*
- can be put inside any block with a label at it start

- **NOTE:** *you can't label the start of a function then use `break label;` to break out of the function entirely*


## return 
- *a function without a return statement automatically returns `undefined`*
- a function with a return statement but without a value also returns `undefined`


## throw exception
```js
throw exception;
```
- `exception`: evaluates to a value of any type (string, boolean, int, etc)

### Error class
```js
throw new Error(message);
```
- **name:** *type of error*
- **message:** *string that gets passed to constructor*

### try, catch, finally
- *if catch isn't found in the current scope, we move up a level **(all the way up and no catch -> error is shown to user)**
- `catch(e)`: 
	- `e` : has a block scope, not a function scope

```js
try {
	//code that throws an exception
} catch(e) {
	//code that handles exceptions
} finally {
	//code that always runs after the exception handling and before the exception is escelated (looking for a catch in a higher scope)
}
```

---
# Special Behaviar
1. any jump in the `finally` clause *(break, continue, return, throw)* causes the current error to be ignored/canceled and the new jump destination is handled instead.

```js
try {
	//code that throws exception1
} catch(e) {
	//code that checks for exception1 then throws exception2
} finally {
	//1. code that throws exception3
	//2. code with a switch/loop with `break;`, 'continue;' inside
	//3. code that calls a function that throws exception4
}
```
*in this case, exception2 will get ingored immedietly after being thrown*

---

# Miscellaneous statements
## 1. With
 #deprecated
 
**Remember:**
1. [scope chain]
2. [variable name resolution] #need-further-research 

- `with`: termporarely extends the scope chain 
```js
with (object) {
	//statements
}
```
*here `object` gets temporarely added to the front of the block chain*

* **Note:** 
1. this is forbidden (and deprecated) in strict mode
2. this is just for knowledge

---
## 2. debugger
#ES5 #implementation-dependant
- `debugger`: causes the execution of the program to stop if a debugger program (like the ***firebug debugging*** extension for firefox) was running, otherwise it doesn't do anything.

#need-further-research 

---

## 3. "use strict"
#ES5 
- *a ***directive*** (special string literals that let interpreters that support this (ES5+) do some special things, use no key words)
- ***strict mode***: restricted subset of JavaScript with important fixes to language defencies and provides stronger error checking

### Differences in strict mode
1. `with` is forbidden
2. all variables MUST be declared (can't add properties to the global object)
3. normal functions (non-methods) have `this` = `undefined` instead of the global object
4. temporary scope for `eval()` rather than using the calling function's scope
5. `arguments` object (array-like object) holds a *static copy* of the values passed to the function (rather than refer to it directly).
6. `delete 'non-property'` now throws a syntaxError rather than returning `false`.
7. `delete 'non-configurable-property'` now throws a TypeError rather than returning `false`.
8. naming two properties the same name inside an object -> error.
9. function declaration with 2 parameters with the sme name -> error.
10. octal number literals are not allowed.
11. `eval` and `arguments` are treated like keywords.
12. can't examine the call stack (`arguments.caller` and `arguments.callee` throw TypeError).

### Checking for "strict mode" support:
```js
var hasStrictMode = (function(){
	"use strict";
	return this === undefined
})();
```
