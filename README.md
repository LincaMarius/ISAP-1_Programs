# Programs for the ISAP-1 Computer
Here are all the programs that can run on the ISAP-1 computer

These programs are designed by me or are taken from the authors of the SAP-1 computer in order to be able to verify compatibility with the original SAP-1 computer.

Programs taken from other authors will be mentioned in the source code and I will also include a shortcut to the location of the original code.

By: Lincă Marius Gheorghe.

Pitești, Argeș, România, Europe.

https://github.com/LincaMarius

## About the project, brief description
The goal of this project is to create a more efficient version of the SAP (Simple As Possible) computer, but with minimal changes so that the instruction format remains the same.

This project is part of a project made by me:
https://github.com/LincaMarius/ISAP-Computer

where I optimized the SAP-1 computer

## Programs for ISAP-1 version 1

### The format of the SAP-1 computer instructions is:

| 4 bits instruction code   | 4 bits operand (memory address)          |
|---------------------------|------------------------------------------|

We notice that the upper nibble is used to encode an instruction. 
So, any instruction is encoded on 4 bits. 
Thus, we can have a maximum of 2 ^ 4 = 16 instructions.

### The original instruction set of the SAP-1 computer is:

| Mnemonic | Opcode | Operation                                  |
|----------|--------|--------------------------------------------|
| LDA      | 0000   | Load RAM data into Accumulator             |
| ADD      | 0001   | Add RAM data to Accumulator                |
| SUB      | 0010   | Substract RAM data from accumulator        |
| OUT      | 1110   | Load Accumulator data into Output Register |
| HLT      | 1111   | Stop processing                            |

We can notice that the instructions 0011, 0100, 0101, 0110, 0111, 1000, 1001, 1010, 1011, 1100, 1101 are not used. So we can add 11 more new instructions.

In total, 5 out of 16 possible instructions are implemented.
