# Comparison Instructions
## AND
- resets carry and overflow flags.
- modifies sign, zero and parity flags.
- useful for **MASKING**, **Set Intersection**.

## TEST
*similar to and but doesn't affect the destination operand*

## OR
- resets carry and overflow flags.
- modifies sign, zero and parity flags.
- useful for **Setting a specific bit**, **Set Union**.

## NOT
- doesn't affect any flags.

## XOR
- resets carry and overflow flags.
- modifies sign, zero and parity flags.
- a XOR 0 = a
- a XOR 1 = a'
- (a XOR b) XOR b = a 
	- *Two XORs cancel each other.*
- useful for **Checking Parity** (by XORing with 0) or (XORing ah with al);


## CMP
*performs an implied subtraction and changes all the flags accordingly*

1. Unsigned operands
| CMP Results | ZF  | CF  |
| ----------- | --- | --- |
| dst > src   | 0   | 0   |
| dst < src   | 0   | 1   |
| dst = src   | 1   | 0    |

2. Signed operands
| CMP Results | Flags    |
| ----------- | -------- |
| dst > src   | SF = OF  |
| dst < src   | SF != OF |
| dst = src   | ZF = 1         |

----

# Manipulating Flags

| Flag          | set                | clear               |
| ------------- | ------------------ | ------------------- |
| Zero Flag     | AND/TEST 0         | OR 1                |
| Sign Flag     | OR (highest bit) 1 | AND (highest bit) 0 |
| Carry Flag    | STC                | CLC                 |
| Overflow Flag | 7F + 1 (pos + pos = neg)                   | OR 0                |

---

# Conditional Jumps
## Unsigned operands
*Above and Below*

## Signed operands
*Greater and Less than*

---

# Conditional Loops
## LOOPZ & LOOPE
*don't affect any flags in 32-bit mode*

## LOOPNZ & LOOPNE
*have the same opcode (equivalent)*

---

# Conditional Control Flow Directives

| Directive          | Description                                           |
| ------------------ | ----------------------------------------------------- |
| .BREAK             | Generates code to terminate a .WHILE or .REPEAT block |
| .CONTINUE          |       Generates code to jump to the top of a .WHILE or .REPEAT block                                                |
| .ELSE              |             Begins block of statements to execute when the .IF condition is false                                           |
| .ELSEIF    *condition*        | condition Generates code that tests condition and executes statements that follow, until an .ENDIF directive or another .ELSEIF directive is found                                                      |
| .ENDIF             |   Terminates a block of statements following an .IF, .ELSE, or .ELSEIF directive                                                    |
| .ENDW              | Terminates a block of statements following a .WHILE directive                                                       |
| .IF *condition*    |       Generates code that executes the block of statements if condition is true.                                                |
| .REPEAT            | Generates code that repeats execution of the block of statements until condition becomes true                                                      |
| .UNTIL *condition* |    Generates code that repeats the block of statements between .REPEAT and .UNTIL until condition becomes true                                                   |
| .UNTILCXZ          |  Generates code that repeats the block of statements between .REPEAT and .UNTILCXZ until CX equals 0                                                     |
| .WHILE *condition*                   |   condition Generates code that executes the block of statements between .WHILE and .ENDW as long as condition is true                                                    |

- *conditions* : similar syntax to Java and C++

