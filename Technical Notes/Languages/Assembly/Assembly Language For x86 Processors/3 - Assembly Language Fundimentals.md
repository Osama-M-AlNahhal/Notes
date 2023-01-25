
- Constant Integer Expressions : evaluated only at assembly time.
- Directives: tell the assembler how to assemble the program.
- Attributes: provide size and usage info (BYTE, WORD, etc).
- Identifier's Rules:
	1. 1-247 characters long.
	2. not case sensitive.
	3. first char can't be a digit.
	4. can't be a reserved word.
- Labels: markers/pointers
	1. data label : in the `.data` segment, allows the referencing of specific memory locations.
	2. code label : in the `.code` segment, ends with a colon (:), used as a target for jumps.
- Instructions have 0-3 operands, which can be either:
	1. memory
	2. register
	3. integer expression
	4. I/O port
- instructions with n operands:
	0. STC
	1. INC
	2. MOV
	3. ADD

- NOP : instruction that only takes 1 byte of memory for alignment
- 
```masm
ExitProcess PROTO, dwExitCode:DWORD
```
- 
```masm
.model flat, stdcall
```

# The Assemble-Link-Execute Cycle
Assmebler : 
	.obj : contains machine language.
	.list : (optional) contains the following:
		1. copy of source code (with line numbers).
		2. address of each instruction.
		3. machine code bytes of each instruction (in hexa).
		4. symbol table.

Linker : reads the .obj file, if there's a call to a library procedure -> it copies the procedure into the .obj file and creates an executable file from it.

Loader : OS utility, loads the executable file into memory before execution

---

# Defining Data
## Size
| Type   | Size     | Usage                                                                         |
| ------ | -------- | ----------------------------------------------------------------------------- |
| DB     | 1 Byte   | legacy, signed or unsigned                                                    |
| DW     | 2 Bytes  | legacy, signed or unsigned                                                    |
| DD     | 4 Bytes  | legacy, signed or unsigned                                                    |
| FWORD  | 6 Bytes  | pointer in protected mode                                                     |
| TBYTE  | 10 Bytes |                                                                               |
| REAL4  | 4 Bytes  | IEEE Short Real (floating point, single precision) <br>significant digits = 6 |
| DD     |          | can also be used for short real                                               |
| REAL8  | 8 Bytes  | IEEE Long Real (floating point, double precision)<br>significant digits = 15  |
| DQ     |          | can also be used for long real                                                |
| REAL10 | 10 Bytes | IEEE Extended Real (extended precision)<br> significant digits = 19           |
| DT     |          | can also be used for extended percision                                                                              |

- all initializers are converted to binary by the assembler.
- Intel stores a packed binary coded decimal (BCD) integers in a 10-byte package. Each byte (except the highest) contains two decimal digits, highest Byte (left most byte in little endian) is 00 for positive and 80 for negative BCD integers.
- defining TBYTE must be in hexa, because the compiler doesn't convert from decimal when initializing a TBYTE.
- encoding a real number as a BCD:
	1. FLD instruction : loads it into the floating-point register stack.
	2. FBSTP instruction : convert it to BCD.

- `.Data?` :
	- this segment directive is used when declaring uninitialized variables to reduce the overall compiled program size.


# Symbolic Constants
*similar to variables but do not change at runtime and do not preserve memory space (compiler replaces them with their value at compile time)*

- make programs easier to read
- replace once, changes everywhere.
- created using `=` for integers, and `equ` or `TEXTEqu` for text

## `=` :
- constants defined with `=`  and `TEXTEQU` can be redefined in the same file, but `EQU` can't .

`$` : current location counter

### List/String's size
```masm
ListName WORD 1, 2, 3
ListSize = ($ - ListName)
```


## `EQU` :
> name EQU expression
name EQU symbol
name EQU \<text>


## `TEXTEQU` :
> name TEXTEQU \<text>
> name TEXTEQU textmacro
> name TEXTEQU %constExpr

	