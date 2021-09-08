# About CPU 2

*A 16 bit machine with better sorted opcodes and generally improved components.*

# Instructions

## General Instructions
- NOP    0000 - Do nothing
- DLOAD  0001 - Load the specified value into the a register
- LOAD   0002 - Load the contents at the specified adress into the a register
- STORE  0003 - Load the contents of the a register into the specified adress

- DOUT   0004 - Directly output the a register
- OUT    0005 - Output the contents of the given memory address
- HALT   0006 - Halt the execution of the program


## Arimetric instructions
*All ALU instructions set their ALU flags appropiately*
- ADD    0010 - Add the contents of the specified address to the a register
- ADDI   0011 - Add the specified value to the a register

- SUB    0012 - Subtract the contents of the specified address from the a register
- SUBI   0013 - Subtract the specified value from the a register

- MUL    0014 - Multiply the contents at the specified address with the a register
- MULI   0015 - Multiply the specified value with the a register

- DIV    0016 - Divide the a register over value at the specified address 
- DIVI   0017 - Divide the a register over the specified address

- MOD    0018 - Calculate the remainder of the contents at the specified address and the a register (a % b)
- MODI   0019 - Calculate the remainder of the specified value and the a register


## Jump Instructions
- JMP    0020 - Unconditionally jump to the specified memory address

- JZ     0021 - Jump if the zero flag is set (a is 0)
- JNZ    0022 - Jump if the zero flag is not set

- JN     0023 - Jump if the ALU negative flag is set
- JNN    0024 - Jump if the ALU negative flag is not set
- JO     0025 - Jump if the ALU overflow flag is set
- JNO    0026 - Jump if the ALU overflow flag is not set


# Control logic:

## ALU Control Words

- 0000 - Nothing (NO output)
- 0001 - Add
- 0010 - Subtract
- 0011 - Multiply
- 0100 - Divide
- 0101 - Remainder / Modulo

## ALU Flags 
- 01 - Overflow flag (for addition and multiplication)
- 10 - Negative flag

## Register Zero flag (updates one clock cycle after write to register)
- 1 - A Register is 0

## Jump control words

- 0000 - Nothing (dont jump)
- 0001 - Unconditonal

- 0010 - Jump if a is 0
- 0011 - Jump if a is not 0

- 0100 - Jump if negative flag is set
- 0101 - Jump if negative flag is not set
- 0110 - Jump if overflow flag is set
- 0111 - Jump if overflow flag is not set

