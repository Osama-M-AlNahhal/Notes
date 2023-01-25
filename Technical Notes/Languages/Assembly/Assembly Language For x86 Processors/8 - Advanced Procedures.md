# Stack Frame
## Calling Conventions
### Old 
*fastcall* : passing arguments to subroutines through registers.
- fast but limited.

### New
- *C-calling* : 
	- When a program calls a subroutine, it follows the CALL instruction with a statement that adds a value to the stack pointer (ESP) equal to the combined sizes of the subroutine parameters 

- *STDCALL* :
	- we supply an integer parameter to the RET instruction, which in turn adds 8 to ESP after returning to the calling procedure. The integer must equal the number of bytes of stack space consumed by the procedure’s parameters.

----

## LEA instead of OFFSET
- Can't use `OFFSET [EBP + 1]` because this is calculated at runtime, and offset works at assembling time.
- instead we use `LEA` which works at runtime too.

---

## ENTER & LEAVE
*save us time by automatically creating a stack frame for the procedure and storing EBP on the stack*

### ENTER
`ENTER numBytes, nestingLevel` does 3 things:
1. `push ebp`
2. `mov ebp, esp`
3. `sub esp, numBytes`

- *numBytes* : rounded up to multiples of 4.
- *nestingLevel* : determines the number of stack frame pointers copied into the current stack frame from the stack frame of the calling procedure.


### LEAVE
`LEAVE` does 2 things:
1. `mov esp, ebp`
2. `pop ebp`


### LOCAL
*must be directly after the PROC directive*

`LOCAL label:type, label:type, label:type, ...`
- reserves space for local variables


---

# Recursion
## Recursively Calculating a Sum

## Calculating a Factorial


---

# INVOKE, ADDR, PROC, and PROTO

## INVOKE Directive
*only available in 32-bit mode*

- instead of using `CALL` we can use `INVOKE` and pass a comma-separated list of parameters in reverse order after the procedure's name (rather than pushing them on the stack manually).

**Parameters that can be passed after `INVOKE`**:
![[Assembly Invoke directive parameter types.png]]


## ADDR Operator
*used to pass a pointer argument when calling a procedure using INVOKE*

- The argument passed to ADDR must be an assembly time constant.
- Can ONLY be used with *INVOKE*.


## PROC Directive

```MASM
label PROC [attributes] [USES reglist], parameter_list
```

1. \[attributes] : 
![[Assembly PROC attributes.png]]

2. parameter_list :
*comma-separated local-scope parameters in the form of **paramName:Type***
- **Qualified type** : may be a pointer to an existing type. `PTR BYTE`


## PROTO Directive
*same syntax as the PROC but without the \[USES regs] part*
- creates a prototype of a procedure allowing us to use the procedure's name before it's created
- used to verify the parameters passed to the procedure
- every procedure that we want to call with INVOKE must have a PROTO statement at the start of the code


## Detected & Undetected Errors:
**Detected :**
1. an argument exceeds the size of a declared parameter.
2. too few or too many arguments.

**Undetected :**
1. If an argument’s type is smaller than a declared parameter, MASM does not detect an error.



## Debugging Tips
1. Argument Size Mismatch
2. Passing the Wrong Type of Pointer:
	- the assembler does not validate the type of pointer you pass to a procedure.
```masm
INVOKE Swap, ADDR [ByteArray + 0], ADDR [ByteArray + 1] ;error not detected (expects DWORDArray)
```
3. Passing Immediate Values during Invokation when the procedure expects a pointer
	- this assembles correctly but can cause a runtime error.


----

# Creating Multimodule Programs