# dlsu-kogananki-assembler

Kougan Anki (鋼金暗器) Theoretical Assember

Kougan Anki is a 20bit fixed-length assembler for a simple conceptual robot 
with a theoretical Turing-complete instruction set.

## Machine code syntax:

20 bit per line, grouped by 5 bits.

00000 00000 00000 00000

### Legend:

i - bit for instruction code

r - bit for register

m - bit for memory location

x - ignored

Depending on the instruction code, machine code syntax can vary as follows:

#### Robot-navigation instructions:

5 bits instruction

iiiii xxxxx xxxxx xxxxx

#### Sensory instruction:

5 bits instruction, 2 bits register, 13 bits memory

iiiii rrmmm mmmmm mmmmm

#### Jump (goto) command:

5 bits instruction, 13 bits ignored, 2 bits register:

iiiii xxxxx xxxxx xxxrr

#### Jump (goto) command w/ conditionals:

5 bits instruction, 2 bits register, 13 bits jump in memory address:

iiiii rrmmm mmmmm mmmmm

#### Arithmetic:

5 bits instruction, 2 bits register A, 2 bits register B, 2 bits register C

iiiii rrrrr rxxxx xxxxx

#### io Memory:

5 bits instruction, 2 bits register, 13 bits memory address

iiiii rrmmm mmmmm mmmmm

#### Constant Assignment:

5 bits instruction, 2 bits register, 13 bits constant
iiiii rrmmm mmmmm mmmmm

## Instruction Codes 
by Prof. Solomon See (DLSU, CCS)

0: halt = forces the system to stop

1: moveForward = moves the robot forward in the current direction it is facing

2: rotateLeft = rotate left the direction where the robot is facing

3: rotateRight = rotate left the direction where the robot is facing

4: sense = sense what is in front of the robot where it is currently facing. The remainder 15 bits tells the robot which register to store the data.

5: jump = jump to a code line number. The remainder 15 bits identifies which line number to jump to.

6: jumpeq = jump to a code line number if the value of a register is equal to zero. The first 2 bits after the opcode determines which register to check against. The remainder 13 bits identifies which line number to jump to.		

7: jumpne = jump to a code line number if the value of a register is not equal to zero. The first 2 bits after the opcode determines which register to check against. The remainder 13 bits identifies which line number to jump to.

8: jumpgt = jump to a code line number if the value of a register is greater than zero. The first 2 bits after the opcode determines which register to check against. The remainder 13 bits identifies which line number to jump to.

9: jumplt = jump to a code line number if the value of a register is less than zero. The first 2 bits after the opcode determines which register to check against. The remainder 13 bits identifies which line number to jump to.

10: jumpgte = jump to a code line number if the value of a register is greater than or equal to zero. The first 2 bits after the opcode determines which register to check against. The remainder 13 bits identifies which line number to jump to.

11: jumplte = jump to a code line number if the value of a register is less than or equal to zero. The first 2 bits after the opcode determines which register to check against. The remainder 13 bits identifies which line number to jump to.

12: add = adds the values of the first and second register and stores it on the third register. The first 2 bits after the opcode represents the first register, the next 2 bits is for the second register and the next 2 bits for the third register. The remainder of the bits are ignored.

13: sub = subtracts the values of the first register to the second register and stores it on the third register. The first 2 bits after the opcode represents the first register, the next 2 bits is for the second register and the next 2 bits for the third register. The remainder of the bits are ignored.

14: mult = multiplies the values of the first and second register and stores it on the third register. The first 2 bits after the opcode represents the first register, the next 2 bits is for the second register and the next 2 bits for the third register. The remainder of the bits are ignored.

15: readmem = reads the value of the memory location and stores it to a register. The first 2 bits after the opcode represents the register, the remaining bits are used to specify the memory address.

16: writemem = writes to the memory location the value of a register. The first 2 bits after the opcode represents the register, the remaining bits are used to specify the memory address.

17: setreg = sets the value of a register to a constant value. The first 2 bits after the opcode represents the register, the remaining bits represent the constant value that will be stored.

