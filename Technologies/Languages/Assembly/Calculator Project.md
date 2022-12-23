## Specifications
- program a simple calculator that takes in a string of only numbers and operators (not separated by spaces) and evaluates the expression and outputs the result on the console using MASM x86 

---

## Stage 1: Infex to postfex conversion

---

- infex to postfex conversion rules:
	1. print operands as they arrive
	2. if stack is (empty) or (top of stack = `(` ) then push the operator to the stack
	3. if incoming signal is `(` push it to the stack
	4. if incoming signal is `)` then pop the stack and print operators until `(` is found (then discard both `(` and `)`)
	5. if incoming signal is an operator with a higher precedence than the top of the stack then push it to the stack
	6. if incoming signal is an operator with a lower precedence than the top of the stack then pop the top and print it, then test the operator against the new top
	7. if incoming signal is an operator with an equal precedence to the top of the stack then pop the top and print it, then test the operator against the new top
	8. at the end of the expression, pop and print all operators in the stack

---

## Stage 2: final value evaluation

---
- evaluation rules
	1. for every element in the postfix string:
		1. if we encounter an operand then:
			1. push it to the stack
		2. else (operator) then:
			1. pop two elements from stack
			2. evaluate them
			3. push result to stack
	2. return the top of the stack as the final result

---
