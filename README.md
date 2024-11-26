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

### Program 1
I designed this program to test the correctness of the implementation of all instructions in the Instruction Set of the SAP-1 computer and implicitly of the ISAP-1 computer.

The source code is in assembly language that uses instructions from the ISAP-1 computer syntax: \
LDA 4 \
ADD 1 \
SUB 0 \
30h \
44h \
50h \
60h \
70h \
80h \
90h \
A0h \
B0h \
C0h \
D0h \
OUT \
HLT

The execution of this program is:

| Address | Instruction | Hexa |Assembly |    Action    |      Rezult      |
|---------|-------------|------|---------|--------------|------------------|
|  0000	  |  0000 0010  |  04  |  LDA 4  | A <- [4]	    | A = 44           |
|  0001   |	 0001 0001  |  11  |  ADD 1  | A <- A + [1]	| A = 44 + 11 = 55 |
|  0002   |	 0010 0000  |  20  |  SUB 0  | A <- A – [0]	| A = 55 – 4 = 51  |
|  0003   |	 0011 0000  |  30  |  NOP	 |	    -		|       -	       |
|  0004   |	 0100 0100  |  44  |  NOP	 |	    -		|       -	       |
|  0005   |	 0101 0000  |  50  |  NOP	 |	    -		|       -	       |
|  0006   |	 0110 0000  |  60  |  NOP	 |	    -		|       -	       |
|  0007   |	 0111 0000  |  70  |  NOP	 |	    -		|       -	       |
|  0008   |	 1000 0000  |  80  |  NOP	 |	    -		|       -	       |
|  0009   |	 1001 0000  |  90  |  NOP	 |	    -		|       -	       |
|  000A   |	 1010 0000  |  A0  |  NOP	 |	    -		|       -	       |
|  000B   |	 1011 0000  |  B0  |  NOP	 |	    -		|       -	       |
|  000C   |	 1100 0000  |  C0  |  NOP	 |	    -		|       -	       |
|  000D   |	 1101 0000  |  D0  |  NOP	 |	    -		|       -	       |
|  000E   |	 1110 0000  |  E0  |  OUT	 | OUT <- A		| OUT = 51	       |
|  000F   |	 1111 0000  |  F0  |  HLT	 | HLT		    | HLT	           |

The ROM image used in the simulation in the Logisim program is:
[ ROM1 ](/ROMS/ROM1) 


