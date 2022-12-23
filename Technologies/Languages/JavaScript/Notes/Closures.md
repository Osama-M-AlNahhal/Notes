*A closure is just a function inside another function*
*what makes it special in JavaScript is that even if the outer function is done being executed and is popped off the call stack, its properties are still stored in the stack, and the inner function (if exposed) can still access them*
*this allows for object-oriented programming features (outer function is a class, inner functions are methods that can be called independently, and can access the class properties)*
