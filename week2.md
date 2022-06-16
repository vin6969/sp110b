## week 2

### CPU0

CPU0 is a 32-bit processor, including R0..R15, IR, MAR, MDR and other temporary registers, and its structure is shown in the following figure.


![](img/cpu0.jpg)


Figure 1: Architecture of the CPU0 processor

The purpose of each of the scratchpads is as follows:

|  	    |                                               |
|-------|-----------------------------------------------|
|IR	    | instruction register                          |
|R0	    | Constant scratchpad, whose value is always 0. |
|R1~R11 |	General purpose register.                     |
|R12	  | Status Register (Status Word : SW)            |
|R13	  |Stack Pointer : SP                             |
|R14	  |Link Register : LR                             |
|R15	  |Program Counter (Program Counter : PC)         |
|MAR	  |Memory Address Register                        |
|MDR	  |Memory Data Register                           |


### Instruction set of CPU0

The instructions of CPU0 are divided into three types. The L type is usually a load and store instruction, the A type is mainly arithmetic instructions, and the J type is usually a jump instruction. 
The following figure shows the encoding format of these three types of instructions.

![](img/cpu0format.jpg)


Instruction List of CPU0


![](img/cpu0instructions.jpg)


CPU0_v2

|type	|   Format	|   instruction |	OP	| illustrate	| grammar |	semantics |
|-----|-----------|---------------|-----|-------------|---------|-----------|
|floating point operations|	A	|FADD	|41	|floating point addition|	FADD Ra, Rb, Rc|	Ra = Rb + Rc
|floating point operations|	A	|FSUB|	42|	floating point subtraction|	FSUB Ra, Rb, Rc|	Ra = Rb + Rc
|floating point operations|	A	|FMUL	|43|	floating point multiplication	|FMUL Ra, Rb, Rc	|Ra = Rb * Rc
|floating point operations|	A	|FADD	|44	|floating point division|	FDIV Ra, Rb, Rc	|Ra = Rb / Rc
|interrupt handling	|J	|IRET|	2D|	return from interrupt|	IRET	|PC = LR; INT 0


### state register

The status register of CPU0 contains N, Z, C, V status, and interrupt mode bits such as I, T. Its structure is shown in the figure below.

![](img/cpu0sw.jpg)

### When the CMP Ra, Rb instruction is executed, the status flag will change accordingly.

If Ra > Rb, state N=0, Z=0
will be set If Ra < Rb, state N=1, Z=0
will be set If Ra = Rb, state N=0, Z=1 will be set

So the JGT, JLT, JGE, JLE, JEQ, JNE and other instructions of conditional jump can jump according to the N, Z flags in the state register.


#### source
http://ccckmit.wikidot.com/ocs:cpu0


## Assembler

Assembler is a program for converting instructions written in low-level assembly code into relocatable machine code and generating along information for the loader.

Assembly language statement format:

```
[Label] [Opcode] [operand]

Example:  M  ADD  R1, ='3'
where, M - Label; ADD - symbolic opcode; 
R1 - symbolic register operand; (='3') - Literal

Assembly Program:
Label  Op-code   operand   LC value(Location counter)
JOHN   START     200
       MOVER     R1, ='3'    200
       MOVEM     R1, X       201
L1     MOVER     R2, ='2'    202
       LTORG                 203
X      DS        1           204
       END                   205
```

```
1.START: This instruction starts the execution of program from location 200 and label with START provides name for the program.(JOHN is name for program)
2.MOVER: It moves the content of literal(=’3′) into register operand R1.
3.MOVEM: It moves the content of register into memory operand(X).
4.MOVER: It again moves the content of literal(=’2′) into register operand R2 and its label is specified as L1.
5.LTORG: It assigns address to literals(current LC value).
6.DS(Data Space): It assigns a data space of 1 to Symbol X.
7.END: It finishes the program execution.
```


#### source
https://www.geeksforgeeks.org/introduction-of-assembler/#:~:text=Assembler%20is%20a%20program%20for,literals%20to%20produce%20machine%20code.
