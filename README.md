# Programs for the ISAP-1 Computer
Here are all the programs that can run on the ISAP-1 computer

These programs are designed by me or are taken from the authors of the SAP-1 computer in order to be able to verify compatibility with the original SAP-1 computer.

Programs taken from other authors will be mentioned in the source code and I will also include a shortcut to the location of the original code.

By: Lincă Marius Gheorghe.

Pitești, Argeș, Romania, Europe.

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
*LDA 4 \
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
HLT*

The assembly language source code is: \
*LDA [0x04]	; load 0x44 into Accumulator \
ADD [0x01]	; add 0x11 to Accumulator \
SUB [0x00]	; subtract 0x04 from Accumulator \
NOP \
. \
. \
NOP \
OUT	; output to Display content of Accumulator \
HLT	; end of program, halt computer*

The execution of this program is:

| Address | Instruction | Hexa |Assembly |    Action    |      Rezult       |
|---------|-------------|------|---------|--------------|-------------------|
|  0000	  |  0000 0100  |  04  |  LDA 4  | A <- [4]	    | A = 44h           |
|  0001   |	 0001 0001  |  11  |  ADD 1  | A <- A + [1]	| A = 44 + 11 = 55h |
|  0002   |	 0010 0000  |  20  |  SUB 0  | A <- A – [0]	| A = 55 – 4 = 51h  |
|  0003   |	 0011 0000  |  30  |  NOP	 |	    -		|       -	        |
|  0004   |	 0100 0100  |  44  |  NOP	 |	    -		|       -   	    |
|  0005   |	 0101 0000  |  50  |  NOP	 |	    -		|       -	        |
|  0006   |	 0110 0000  |  60  |  NOP	 |	    -		|       -	        |
|  0007   |	 0111 0000  |  70  |  NOP	 |	    -		|       -	        |
|  0008   |	 1000 0000  |  80  |  NOP	 |	    -		|       -	        |
|  0009   |	 1001 0000  |  90  |  NOP	 |	    -		|       -	        |
|  000A   |	 1010 0000  |  A0  |  NOP	 |	    -		|       -	        |
|  000B   |	 1011 0000  |  B0  |  NOP	 |	    -		|       -	        |
|  000C   |	 1100 0000  |  C0  |  NOP	 |	    -		|       -	        |
|  000D   |	 1101 0000  |  D0  |  NOP	 |	    -		|       -	        |
|  000E   |	 1110 0000  |  E0  |  OUT	 | OUT <- A		| OUT = 51h	        |
|  000F   |	 1111 0000  |  F0  |  HLT	 | HLT		    | HLT	            |

The ROM image used in the simulation in the Logisim program is:
[ ROM1 ](/ROMS/ROM1) 

### Program 2
This program is presented in the book and is the first program presented by the authors to explain the operation of the SAP-1 computer.

In the book this program is found in Example 10-1 on page 144.

The source code is in assembly language that uses instructions from the SAP-1 computer syntax and implicitly the ISAP-1 computer is: \
*LDA 9h \
ADD 0Ah \
ADD 0Bh \
SUB 0Ch \
OUT \
HLT \
FFh \
FFh \
FFh \
01h \
02h \
03h \
04h \
FFh \
FFh \
FFh*

The assembly language source code is: \
*LDA [0x09]	; load X = 0x01 into Accumulator \
ADD [0x0A]	; add Y = 0x02 to Accumulator \
ADD [0x0B]	; add Z = 0x03 to Accumulator \
SUB [0x0C]	; subtract W = 0x04 from Accumulator \
OUT	; output to Display content of Accumulator \
HLT	; end of program, halt computer*

The execution of this program is:

| Address | Instruction | Hexa |Assembly |    Action    |      Rezult      |
|---------|-------------|------|---------|--------------|------------------|
|  0000	  |  0000 1001  |  09  |  LDA 9h | A <- [9]	    | A = 1            |
|  0001   |	 0001 1010  |  1A  |  ADD Ah | A <- A + [A]	| A = 1 + 2 = 3    |
|  0002   |	 0001 1011  |  1B  |  ADD Bh | A <- A + [B]	| A = 3 + 3 = 6    |
|  0003   |	 0011 1100  |  2C  |  SUB Ch | A <- A - [C]	| A = 6 - 4 = 2    |
|  0004   |	 1110 0000  |  E0  |  OUT	 | OUT <- A		| OUT = 2	       |
|  0005   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  0007   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  0008   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  0009   |	 0000 0001  |  01  |  X  	 |	    -		|       -	       |
|  000A   |	 0000 0010  |  02  |  Y 	 |	    -		|       -	       |
|  000B   |	 0000 0011  |  03  |  Z 	 |	    -		|       -	       |
|  000C   |	 0000 0100  |  04  |  W 	 |	    -		|       -	       |
|  000D   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  000E   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  000F   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |

The ROM image used in the simulation in the Logisim program is:
[ ROM2 ](/ROMS/ROM2) 

### Program 3
This program is presented in the book and is the second program that is presented by the authors explaining the operation of the SAP-1 computer.

In the Book this program is found in Example 10-3 on page 145.

This program solves the arithmetic problem: 16 + 20 + 24 - 32. This equation can be written: X + Y + Z – W.

The source code is in assembly language that uses instructions from the SAP-1 computer syntax and implicitly the ISAP-1 computer is: \
*LDA 9h \
ADD Ah \
ADD Bh \
SUB Ch \
OUT \
HLT \
FFh \
FFh \
FFh \
10h \
14h \
18h \
20h \
FFh \
FFh \
FFh*

The assembly language source code is: \
*LDA [0x09]	; load X = 0x10 into Accumulator \
ADD [0x0A]	; add Y = 0x14 to Accumulator \
ADD [0x0B]	; add Z = 0x18 to Accumulator \
SUB [0x0C]	; subtract W = 0x20 from Accumulator \
OUT	; output to Display content of Accumulator \
HLT	; end of program, halt computer*

The execution of this program is:

| Address | Instruction | Hexa |Assembly |    Action    |      Rezult      |
|---------|-------------|------|---------|--------------|------------------|
|  0000	  |  0000 1001  |  09  |  LDA 9h | A <- [9]	    | A = 16           |
|  0001   |	 0001 1010  |  1A  |  ADD Ah | A <- A + [A]	| A = 16 + 20 = 36 |
|  0002   |	 0001 1011  |  1B  |  ADD Bh | A <- A + [B]	| A = 36 + 24 = 60 |
|  0003   |	 0011 1100  |  2C  |  SUB Ch | A <- A - [C]	| A = 60 - 32 = 28 |
|  0004   |	 1110 0000  |  E0  |  OUT	 | OUT <- A		| OUT = 28	       |
|  0005   |	 1111 0000  |  F0  |  HLT	 |	    -		|       -	       |
|  0006   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  0007   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  0008   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  0009   |	 0001 0000  |  10  |  X  	 |	    -		|       -	       |
|  000A   |	 0001 0100  |  14  |  Y 	 |	    -		|       -	       |
|  000B   |	 0001 1000  |  18  |  Z 	 |	    -		|       -	       |
|  000C   |	 0010 0000  |  20  |  W 	 |	    -		|       -	       |
|  000D   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  000E   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |
|  000F   |	 1111 1111  |  FF  |  HLT	 |	    -		|       -	       |

The ROM image used in the simulation in the Logisim program is:
[ ROM3 ](/ROMS/ROM3) 
