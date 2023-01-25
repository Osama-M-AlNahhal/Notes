
# Components

A component consists of:
1. Template : 
	`jsx` format, which looks identicle to `html` but with extra functionality like embedded javascrip code
2. Logic : 
   javascript code that dynamically computes the values we want to inject into the component.


what does a component look like?
- `jsx`  function that returns `html` , and is then exported at the end of the file.
- a compiler called ***babble*** renders the `jsx` code into valid `html` before displaying it on the browser screen.
```js
import './componentName.css'

function componenetName() {
	return (
		
	);
}

export default componenetName;
```
