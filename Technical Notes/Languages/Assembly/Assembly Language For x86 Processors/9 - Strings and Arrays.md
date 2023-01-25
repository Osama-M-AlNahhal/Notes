# String Primative Instruction

## MOVSB, MOVSW, and MOVSD
*copy from memory addressed at ESI to EDI*

## CMPSB, CMPSW, and CMPSD
*compare the content of  memory addressed at ESI to EDI*

## SCASB, SCASW, and SCASD
*compare accumulator (EAX, AX, AL) to memory addressed at EDI*

## STOSB, STOSW, and STOSD
*store accumulator (EAX, AX, AL) to memory addressed at EDI*

## LODSB, LODSW, and LODSD
*load data from memory addressed by ESI to accumulator (EAX, AX, AL)*


- **We can also add (REP, REPZ, REPE, REPNZ, REPNE) before any of the previous instructions to repeat it until: `ECX <= 0`**
- Using ***REP*** automatically increments ESI and EDI after each execution, based on the direction flag (so we clear it beforehand using `CLD`)
	- CLD : forward
	- STD : reverse


---

# Selected String Procedures
*from the Irvine32 library*

## Str_compare Procedure
takes: addr str1, addr str2
returns: nothing (but zero and carry flags are affected).

## Str_length Procedure
takes: addr string
returns: EAX=length

## Str_copy Procedure
takes: addr src, addr dst
returns: nothing

## Str_trim Procedure
takes: addr string, trailing_character
returns: nothing

## Str_ucase Procedure
takes: addr string
returns: nothing


----

# Two-Dimentional Arrays
## Ordering of Rows and Columns

**two methods of arranging the rows and columns in memory** :
1. row-major order : ROW1 ROW2 ROW3 ...
2. column-major order : COL1 COL2 COL3 ...

**Two Operand Types :**
1. base-index : \[base + index\] both must be general purpose registers
2. base-index-displacement

## Base-Index Operands

## Base-Index-Displacement Operands

---

# Searching and Sorting Integer Arrays

## Bubble Sort


## Binary Search