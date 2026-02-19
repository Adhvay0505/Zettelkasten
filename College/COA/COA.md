# Follow this book: *Computer System Architecture* by Morris M. Mano

Computer organization describes how different parts of computer systems are arranged and connected to work together.  
It focuses on how hardware components interact to perform tasks. It includes the basic set of instructions that a computer can execute.

---

## Instructions

Instructions are commands that tell a computer how to perform specific tasks. These instructions may be of three types:

### 1. Data Transfer Instructions
- Used to move data from one location to another within a computer system.  
- This includes transferring information between memory, CPU registers, etc.  
- **Common data transfer instructions:**
  - **Load:** Copies data from memory into a CPU register for processing.  
  - **Store:** Transfers data from a CPU register back to memory.  
  - **Move:** Transfers data from one register to another within the CPU.  

### 2. Arithmetic and Logic Instructions
- Perform mathematical and logical operations.  
- **Examples of arithmetic operations:** Add, Subtract, Multiply, Divide  
- **Examples of logical operations:** AND, OR, NOT, XOR  

### 3. Control Instructions
- Determine the flow of execution in a program.  
- **Examples:** Jump, Conditional Branch (Branch if 0, Branch if not 0), Call, Return  

---

## Instruction Set

- A basic computer uses a **16-bit instruction register (IR)**.  
- An instruction can be classified as **Memory Reference**, **Register Reference**, or **I/O Instruction** based on specific bits in the instruction format.

---
### Memory Reference Instruction
- These instructions use a **memory address** as the operand while the other operand is always the **accumulator**.  
- Consists of:
  - 12-bit **address**
  - 3-bit **opcode**
  - 1-bit **addressing mode** for direct or indirect addressing  
- These instructions operate on data stored in memory.

15  14     12  11      0
|-----------------------|
| 1 | opcode | Memory   |
|   |        | Address  |
|-----------------------|

register reference instructions perform operations directly on CPU registers rather than from memory locations. 
If IR(opcode) = 111, distinguishes register reference instructions from memory reference instructions
If IR(opcode) = 0, it indsinguishes them from IO instructions
Remaining 12 bits are used to specify register operations to be performed


---

### Register Reference Instructions
- Perform operations directly on **CPU registers** rather than memory locations.  
- **IR(opcode) = 111** distinguishes register reference instructions from memory reference instructions.  
- **IR(opcode) = 0** distinguishes them from I/O instructions.  
- Remaining 12 bits specify the register operation to be performed.

**Format:**

15  14  12  11        0
|-----------------------|
| 0 | 111 | Register    |
|   |     | Operation   |
|-----------------------|



---

### I/O Instructions
- Perform input/output operations.  
- **IR(12-14) = 111** distinguishes I/O instructions from memory reference instructions.  
- **IR(15) = 1** distinguishes them from register reference instructions.  
- Remaining 12 bits specify the I/O operation.

**Format:**

15  14  12  11        0
|-------------------------|
| 1 | 111 | IO Operation  |
|-------------------------|

IR (12-14) value = 111 distinguishes IO instructions from memory reference instructions
IR (15) = 1 distinguishes them from register reference instructions
remainging 12 bits are used to specify IO operations


--- 

### Types of arithmetic instructions

1.  Addition instructions
- It is used to add two operands
- ADD, ADC (Add with carry) or INCE (increment by 1)

2. Subtraction instructions
- SUB, SBB (subtract with borrow), DEC (decrement by 1)

3. Multiplication instructions
- MUL (unsigned multiplication), IMUL (signed multiplication)

4. Division Instructions
- DIV (unsigned), IDIV (signed)

5. Compare instructions: Performs subtraction internally but does not store the result
- CMP

6. Decimal Arithmetic instruction: It is architecture dependant instruction used in BCD Operations.
- Eg DAA (Decimal adjust after addition), DAS (decimal adjust after subtraction)

---

## Types of logical instructions

- These instructions are operations that work on binary numbers
- Eg; AND OR NOT XOR XNOR NAND NOR etc

---

## Types of program control instructions

- Program control instructions control the flow of execution of program instead of performing calculations

1. Unconditional jump instructions: Eg JMP