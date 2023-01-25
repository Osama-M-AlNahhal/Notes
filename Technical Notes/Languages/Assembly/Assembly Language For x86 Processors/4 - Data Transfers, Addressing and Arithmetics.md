
# Data Related Operators and Directives
| Operator/Directive | info                                                                   |
| ------------------ | ---------------------------------------------------------------------- |
| OFFSET             | distance of the variable from the beginning of the segment             |
| ALIGN              |                                                                        |
| PTR                | override the operand's defualt size                                    |
| TYPE               |                        size of a single element in the array   in bytes                                              |
| LENGTHOF           | number of elements in the array                                        |
| SIZEOF             | number of bytes used by an initializer<br>LENGTHOF x TYPE |
| LABEL              |                                       redefine the same variable with different size attributes                                 |


----
**TYPEDEF** : Create a user defined type to be used to declare variables
- defining a type must happen before the `.code` segment, near the very beginning of a program.

*defining a type that's a pointer to a byte*
```masm
PBYTE TYPEDEF PTR BYTE
```

---
**LOOP**

- loop destination must be within -128 to 127 bytes of the `LOOP` position.
- 2 steps:
	1. ECX--
	2. cmp ecx, 0

- for nested loops, store ECX for the outer loop in a variable