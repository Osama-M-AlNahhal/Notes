# Shift & Rotate
*affect the overflow and carry flag*

## Instruction
| INSTRUCTION | INFO |
| ----------- | ---- |
| SHL + SHR + SAL + SAR   | bit is shifted out into the carry flag      |

Syntax:
```masm
SHL dst, count
```
- count can be *imm8* or *CL*, and must be between 0-255.
- same syntax for all shift and rotate operations.

**Overflow Flag** : 
- if the shifting/rotating is only one bit and flips the sign bit -> overflow = 1
- if we're shifting/rotating by more than one bit -> overflow = undefined.


***SHLD & SHRD*** :
- Syntax: `SHLD dst, src, count`
- src must be a register.


## Applications
### Shifting Multiple Doublewords
```masm
shr array[esi+2],1    ; high byte
rcr array[esi+1],1    ; middle byte, include Carry flag
rcr array[esi],1      ; low byte, include Carry flag
```

### Binary Multiplication
*change any number to sums of powers of 2*

### Displaying Binary Bits

### Extracting File Date Fields

---

# Multiplication & Division
- you can't multiply a 32-bit operand by a 16-bit operand or divide by it
- using `IMUL` preserves the sign by putting FFFFFFFF or 00000000 in EDX based on the sign of the result.

## MUL
![[Assembly MUL.png]]

## DIV
![[Assembly DIV.png]]

**Sign Division** :
- dividend is sign extended before the division.

`CBW` : Convert Byte to Word (Sign-Extend AL to AX). 
`CWD` : Convert Word to Doubleword (Sign-Extends AX to EAX).
`CDQ` : Convert Doubleword to Quadword (Sign-Extend EAX to EDX:EAX).
- used before doing a signed division (using `IDIV`).

## IDIV
- dividend must be sign extended before division.
- remainder has the same sign as the dividend



---

# Extended Addition & Subtraction
*using `ADC` and `SBB`*
DL:AL = output
EDX:EAX = output



---

# ASCII & Unpacked Decimal Arithmetic

`AAA`
```masm
mov ah,0
mov al,'8’    ; AX = 0038h
add al,'2’    ; AX = 006Ah
aaa           ; AX = 0100h (ASCII adjust result)
or ax,3030h   ; AX = 3130h = '10' (convert to ASCII)
```
`AAS`
`AAM`
`AAD`

Unpacked : highest 4 bits = 0
ASCII : highest 4 bits = 0011b



---

# Packed Decimal Arithmetic
*each decimal integer is stored in 4 bits, if odd number of diggits -> highest nybble = 0*

- advantages :
1. can have any number of significant digits, allowing for great accuracy
2. easy to convert between ASCII and Packed Decimal

## Instructions
1. DAA
2. DAS