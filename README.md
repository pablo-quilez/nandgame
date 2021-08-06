# Content

My solutions to the [nandgame.com](https://nandgame.com/). Thanks for the game, Olav Junker Kjær!
- Logic as pictures
- Assembler as text files

# Quick view

## Logic Gates

### Nand

![Nand](01-logic-gates/01-nand.png)

### Inverter

![Inverter](01-logic-gates/02-inverter.png)

### And

![And](01-logic-gates/03-and.png)

## Or

![Or](01-logic-gates/04-or.png)

## Xor

![Xor](01-logic-gates/05-xor.png)

## Arithmetics

### Half Adder

![Half Adder](02-arithmetics/01-half-adder.png)

### Full Adder

![Full Adder](02-arithmetics/02-full-adder.png)

### Multi-bit Adder

![Multi-bit Adder](02-arithmetics/03-multi-bit-adder.png)

### Increment

![Increment](02-arithmetics/04-increment.png)

### Subtraction

![Subtraction](02-arithmetics/05-subtraction.png)

### Equal to Zero

![Equal to Zero](02-arithmetics/06-equal-to-zero.png)

### Less than Zero

![Less than Zero](02-arithmetics/07-less-than-zero.png)

## Plumbing

### Selector

![Selector](03-plumbing/01-selector.png)

### Switch

![Selector](03-plumbing/02-switch.png)

## Memory

### Latch

![Latch](04-memory/01-latch.png)

### Data Flip-Flop

![Data Flip-Flop](04-memory/02-data-flip-flop.png)

### Register

![Register](04-memory/03-register.png)

### Counter

![Counter](04-memory/04-counter.png)

### RAM

![RAM](04-memory/05-ram.png)

## Arithmetic Logic Unit

### Unary ALU

![Unary ALU](05-arithmetic-logic-unit/01-unary-alu.png)

### ALU

![ALU](05-arithmetic-logic-unit/02-alu.png)

### Opcodes

![Opcodes](05-arithmetic-logic-unit/03-opcodes.png)

### Condition

![Condition](05-arithmetic-logic-unit/04-condition.png)

## Processor

### Combined Memory

![Combined Memory](06-processor/01-combined-memory.png)

### Instruction Decoder

![Instruction Decoder](06-processor/02-instruction-decoder.png)

### Control Unit

![Control Unit](06-processor/03-control-unit.png)

### Computer

![Computer](06-processor/04-computer.png)

### Input and Output

![Input and Output](06-processor/05-input-and-output.png)

## Programming

### Machine code

```
1000100000010000	D = 0
0000000000000010	A = 2
1000011111010000	D = D + 1
1000000000000111	JMP
```

### Assembler

```
# Cleaner version
LOOP:
A = 0b01
D = A
A = 0x7FFF
*A = D
A = 0b10
D = A
A = 0x7FFF
*A = D
A = LOOP
JMP
```

### Escape Labyrinth

```
#------------------------------
# Wait until movement finishes
#------------------------------
WAITSTOPPED:
# Turning
A = 0b01000000000 
D = A
A = 0X7FFF
D = D & *A
A = WAITSTOPPED
D; JNE
# Moving forward
A = 0b10000000000 
D = A
A = 0X7FFF
D = D & *A
A = WAITSTOPPED
D; JNE
#------------------------------
# Advance if no obstacle
#------------------------------
ADVANCE:
# Obstacle on front
A = 0b00100000000
D = A
A = 0X7FFF
D = D & *A
A = ROTATELEFT
D; JNE
# Move forward
A = 0b00000000100
D = A
A = 0X7FFF
D = D | *A
*A = D
A = WAITSTOPPED
JMP
#------------------------------
ROTATELEFT:
A = 0b00000001000
D = A
A = 0X7FFF
D = D | *A
*A = D
A = WAITSTOPPED
JMP
```
