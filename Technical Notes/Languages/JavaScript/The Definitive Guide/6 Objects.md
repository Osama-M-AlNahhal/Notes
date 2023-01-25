----

- Objects are mutable.
- Object properties are strings.
- every property has attributes

----

# Property Attributes

| property      | meaning                                                  |
| ------------- | -------------------------------------------------------- |
| writable   | *whether the value of the property can be set*           |
| enumerable | *whether the property name is returned by a for/in loop* |
|         configurable      |   *whether the property can be deleted or altered*                                                       |

- **Before ES5:** all user-created properties are writable, enumerable and configurable.
- **After ES5:** we can choose if we want our properties to be writable, enumerable, configurable or not.

- each property is associated with a ***Property descriptor*** object, which contains:
	A. in data properties:
	1. value
	2. writable
	3. configurable
	4. enumerable

	B. in accessor properties:
	1. set
	2. get
	3. configurable
	4. enumerable

## Accessing Property Descriptor

1. ***own-property***'s property descriptor:
```js
Object.getOwnPropertyDescriptor(objectName, "propertyName");
```

2. modified-properties:
```js
Object.defineProperty(objectName, "propertyName", {
	value:"val",
	writable:true,
	configurable:false,
	enumerable:true
});
```

---

# Object attributes

| Attribute       | meaning                                                             |
| --------------- | ------------------------------------------------------------------- |
| prototype       | *references to an object which our object inherits properties from* |
| class           | *a string specifying the object's type.*                            |
| extinsible flag | *specifies whether new properties can be added to an object.*                                                                    |


---

# Object classifications
## nativ objects
- *objects that are defined by the ECMAScript specification.*

## host objects
- *objects that are defined by the host environment.*

## user-defined objects
- *objects defined by the user*

---

# Properties classifications
## own-properties
- *defined by the object itself.*

## inherited-properties
- *defined by the prototype of the object*

---

# Creating objects
- To use spaces, hyphens or reserve words in an object property: -> use " "

- property values are evaluate every time the object is called (so if there's an increment operation accessing a global variable, it will be executed every time the object is accessed).

- All objects that are created using object literals ( #need-further-research ) have the same associated-object (`Object.prototype`).

- Objects created with `new constructor()` inherit the prototype of the constructor function
```js
new Array() // inherits -> Array.prototype
new Date() // inherits -> Date.prototype
```
- All prototype objects have a prototype associated with them except `Object.prototype` which creates the prototype chain

```js
Object.create(prototype, [properties]);
// prototype = null ==> the object inherits NOTHING, not even toString()
//this is ES5+
```

---
# Associated Arrays
- *Arrays indexed by strings rather than numbers*
- *also known as hash, map, dictionary, etc.*
- *objects in JS are associted arrays*
- *property look up goes up the prototype chain until either the property is found or an object with `prototype=null` is reached.*
	- what happens when the property isn't found? -> `undefined` is returned.
	- attempting to set a property on `null` or `undefined` causes a `TypeError`.

- property assignment either changes the value (if the object has the property) or creates the property and hides the similarly named properties in the prototype chain (unless our object inherits a *read-only*) property with the same name
	- **Exception: 
		1. property is an accessor property (with a setter method) then instead of creating a new property, the setter is called on the object.
		2. attempting to set a property that is *read-only* to a new value fails silently.
		3. attempting to add a property with the extinible flag set to `off`/`0` fails silently.
		4. The prototype properties of built in constructors and methods are *read-only*
		```js
		Object.prototype = 0 //fails silently
```
		5. in ***ES5***'s strict mode: 
			1. any failed attempt to set a property causes a type error instead of failing silently


---

# Deleting properties
```js
delete propertyName;
```
- deleting a non-existent property returns `true`
- deleting a property of an object successfuly returns `true`
- `delete non-property` returns `true`
- `delete non-configurable-property` returns `false`

---

# Testing existance of properties
- `for/in`
- `o.hasOwnProperty("propertyName")`
- `o.propertyIsEnumerable("propertyName")`
- `o.property !== undefined`

---

# Enumerating properties
- `for/in`
- `Object.keys(o)` returns an array of the names of (enumerable & own) properties of `o`
- `Object.getOwnPropertyNames(o)` returns an array of the names of (own) properties of `o` 


---

# Property Getters & Setters
* Properties with value=`setter` or `getter`  (methods) are called `accessor` properties (compared to the normal `data` properties).
```js
let o = {
	"property":"val",
	get accessorPropertyName(){
		//return property
	},
	set accessorPropertyName(value) {
		//set the object's property value
	}
}
```

* setters & getters create *write-only* & *read-only* properties (or both) inside objects.
* `this` inside getters and setters refers to the object they're in

---

