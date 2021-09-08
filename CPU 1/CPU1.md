# About CPU 1

A simple 8 bit cpu with some issues in the control logic.
It is recommended to use the v6 version if you want to use the 8 bit cpu.

# Instruction Set 

*Instructions take the value in the next memory address as a parameter. If they don't need a parameter, the next memory address will be the next instruction*

## General Instrucions
- NOP (0x00)  - Do nothing

- DLA (0x01)  - Load the specified value into the a register
- DLB (0x02)  - Load the specified value into the b register
- LDA (0x03)  - Load value at the specified address into the a register
- LDB (0x04)  - Load value at the specified address into the b register
- STA (0x05)  - Store the value of a at the specified address

- HLT (0x21) - Halts the execution of the program

- OUTa (0x22) - Display the contents of the a register on the Output
- OUT (0x23) - Display the contents of the specified memory address on the Output


## Arimetric Instructions

- ADD (0x06)  - Load value at the specified address to b and store a + b in a
- ADDI (0x07) - Load the specified value to b and store a + b in a
*Add instructions set the overflow flag appropiately.*

- SUB (0x08)  - Load value at the specified address to b and store a - b in a
- SUBI (0x09) - Load the specified value to b and store a - b in a
*Sub instructions set the Negative flag appropiately.*

- MUL (0x0A)  - Load value at the specified address to b and store the product in a
- MULI (0x0B) - Load the specified value to b and store product in a
*Mul instructions set the overflow flag appropiately.*

- DIV (0x0C)  - Load value at specified address to b and store a / b in a
- DIVI (0x0D) - Load the specified value to b and store a / b in a
*The result of a division is rounded down (17 / 5 = 3)*

- MOD (0x0E)  - Load value at specified address to b and store the a % b in a
- MODI (0x0F) - Load specified value to b and store a % b in a

## Logic Operation Instructions
- AND (0x10)  - Bitwise ANDs registers a and b and stores the result at the given memory address
- NAND (0x11) - Bitwise NANDs registers a and b and stores the result at the given memory address
- OR (0x12)   - Bitwise ORs registers a and b and stores the result at the given memory address
- NOR (0x13)  - Bitwise NORs registers a and b and stores the result at the given memory address
- XOR (0x14)  - Bitwise XORs registers a and b and stores the result at the given memory address
- XNOR (0x15) - Bitwise XNORs registers a and b and stores the result at the given memory address
- NOTA (0x16) - Bitwise NOTs the a register and stores the result at the given memory address
- NOTB (0x17) - Bitwise NOTs the b register and stores the result at the given memory address

## Jump instructions
- JMP (0x18)  - Unconditionally jumps to the specified memory address
- JAZ (0x19)  - Jumps if a is 0
- JANZ (0x1A) - Jumps if a is not 0
- JBZ (0x1B)  - Jumps if b is 0
- JBNZ (0x1C) - Jumps if b is not 0

- JN (0x1D)  - Jumps if the negative flag is set
- JNN (0x1E) - Jumps if the negative flag is not set
- JO (0x1F)  - Jumps if overflow flag is set
- JNO (0x20) - Jumps if the overflow flag is not set


# Control logic:

## ALU Control Words

- 0000 - Nothing (NO output)
- 0001 - Add
- 0010 - Subtract
- 0011 - Multiply
- 0100 - Divide
- 0101 - Remainder / Modulo

- 0110 - AND
- 0111 - NAND
- 1000 - OR
- 1001 - NOR
- 1010 - XOR
- 1011 - XNOR
- 1100 - NOT a
- 1101 - NOT b

## ALU Flags 
- 01 - Overflow flag (for addition and multiplication)
- 10 - Negative flag

## Register Zero flags (updates one clock cycle after write to register)
- 01 - A Register is 0
- 10 - B Register is 0
- 11 - Both registers are 0

## Jump control words

- 0000 - Nothing (dont jump)
- 0001 - Unconditonal

- 0010 - Jump if a is 0
- 0011 - Jump if a is not 0
- 0100 - Jump if b is 0
- 0101 - Jump if b is not 0 

- 0110 - Jump if negative flag is set
- 0111 - Jump if negative flag is not set
- 1000 - Jump if overflow flag is set
- 1001 - Jump if overflow flag is not set