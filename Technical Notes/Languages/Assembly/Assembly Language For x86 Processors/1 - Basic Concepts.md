
- Intel (RISC = Reduced Instruction Set Computer).
- AMD (CISC = Complex Instruction Set Computer).

**Assembler:** converts source code (`.asm`) to machine language.
**Linker:** combines individual files created by the assmebler into an executable program.
**Debugger:** lets you step through a program.


# Types of assemblers
1. Microsoft Macro Assembler (known as MASM).
2. MASM32 (a variant of MASM).
3. TASM (Turbo Assembler).
4. NASM (Netwide Assembler).
5. GAS (GNU assembler).


# Types of programs created using MASM
1. 64-bit mode.
3. 32-bit Protected mode.
4. 16-bit Real-Address mode.


- Assembly language has a one-to-one relationship with machine language.
- High-level languages have a one-to-many relationship with assembly language and machine language.
- Assembly language is **Not Portable**, because it is designed for a specific processor family.

----

# Virtual Machine Concept
- Two ways to convert L1 to L0
| Interpretation                        | Translation                                       |
| ------------------------------------- | ------------------------------------------------- |
| decode and execute one line at a time | entire program is converted then executed at once |

**Virtual Machines:** a software program that emulates the functions of some other physical or virtual computer.

L4: High-Level Languages
L3: Assembly (Translated, not Interpreted).
L2: ISA (Instruction Set Architecture) - Machine Language.
L1: Computer Logic Hardware. 

---

# Data Representation

## Binary

### Unsigned Binary -> Decimal
- multiply by weight.
`00101001b` = `41d` 

### Unsigned Decimal -> Binary
- divide by 2, remainder (bottom to top = left to right).
`37d` = `100101b`

### Binary Addition & Subtraction
- bitwise

### Signed Binary
- sign bit
- 2's comp.

### Signed Binary -> Decimal
- if negative: 2's comp. to get the value, then add a negative sign.

### Signed Decimal -> Signed Binary
- if negative: 
  1. convert the absolute value normally.
  2. find 2's comp.

---

## Hexadecimal
- 1 hexadecimal integer = 4 bits.
- 2 hexadecimal integers = byte.
- `00` to `FF` = 0 to 255

### Unsigned Hexa -> Decimal
- multiply by weight.

### Unsigned Decimal -> Hexa
- divide by 16, remainder (bottom to top = left to right).

### Hexadecimal Addition & Subtraction
- bitwise, similar to binary addition & subtraction.


### Signed Hexa -> Decimal
- if negative: 2's comp. then convert as if it's unsigned, then add a negative sign to the decimal value.
- negative means MSB >= 8.

### Signed Decimal -> Hexa
- if negative: convert the absolute value as if it's unsigned, then find the 2's compliment.

---

## Representing Negative Values
1. Sign and Magnitude.
2. 1's compliment.
3. 2's compliment.

---

## Characters
### ASCII
- 7-bits
- extra bit for creating a custom set

### ANSI
- 8-bits (256 Characters).

### Unicode
- varying sizes.
- universal, like *UTF-8*, *UTF-16*, *UTF-32*.
- `41h` = A
- `61h` = a

---

# Sizes
| Size            | Number of Bytes |
| --------------- | --------------- |
| Byte            | 1               |
| Word            | 2               |
| Doubleword      | 4               |
| Quadword        | 8               |
| Double Quadword | 16              |
| Kilobyte        | 2^10            |
| Yottabyte       | 2^80                |


---

# Terminology
1. Binary Integer: Stored in it's raw form (ready to be used in calculations).
2. Digit String: ASCII string which represents a number (can be binary digit string, decimal digit string, etc.).




