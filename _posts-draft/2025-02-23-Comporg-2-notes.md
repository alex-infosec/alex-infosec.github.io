

# Comp Org

## Feb 10th
### Arm Procedures
Stack Frame and Procedure Calls:

Before calling a function, create a stack frame to save registers that will be overwritten:
Save x0, x1, x2, x29 (Frame Pointer), and x30 (Return Address).
Allocate 40 bytes on the stack (5 registers x 8 bytes each).
Return values should be stored in x0 by convention.
Branch and Link (BL) is used to call functions.
This overwrites x30 with the return address.
Return using Branch to Register `(BR X30)` or `RET` (syntactic sugar for BR X30).
Stack cleanup: After function execution, restore the stack pointer using ADD to free the allocated space.

__Debugging and Emulator Tips:__
Use GDB (GNU Debugger) for inspecting registers and memory.
Command examples:
x 8gx $sp: Display 8 chunks of 8 bytes from the stack pointer.
disassemble main: Disassemble the main function to see assembly instructions.
Step through code using n (next) and s (step into functions) to observe changes in registers and memory.

__Using GCC – Compiling and Running C__
gcc myprogram.c
* Produces an executable named a.out by default.
* Run it via ./a.out.

__gcc myprogram.s -o myprogram__
* Compiles/assembles myprogram.s and names the output executable myprogram.
* Run via ./myprogram.

__gcc myprogram.s -o myprogram -g__
* Same as above but also includes debugging information for the GNU Debugger.

__GNU Debugger (GDB)__
* gdb myprogram
* Load myprogram into the debugger; this requires that myprogram was compiled/assembled with -g.

__Useful GDB commands:__
* b – Set a breakpoint.
* r – Run.
* n – Execute the next line (step over function calls).
* s – Execute the next line (step into function calls).
* i r – Show info about registers.

### Copying Files to the Emulator
__To transfer to the emulator:__
`scp -P 3101 filename.s root@localhost:~`
__To transfer from the emulator:__
`scp -P 3101 root@localhost:~/filename.s filename.s`

### Anatomy of an ARM Program
__Data Section__
```bash
.section .data
welcome:    .asciz "Welcome! Please enter your name: "
greeting:   .asciz "Hello, %s! Hope you're having a fantastic day!\n"
input:      .asciz "%s"
name:       .space 8
```
`.asciz` is a null-terminated string.
`.space` 8 reserves 8 bytes (for storing a user-entered name, for example)

__Text Section__
```bash
.section .text
.global main
main:
    # Print the welcome message
    ldr x0, =welcome    # Load address of welcome string into x0
    bl printf           # Call printf
    ...

    # Read a string from user (scanf)
    ldr x0, =input      # Format specifier in x0: "%s"
    ldr x1, =name       # Pointer to 'name' buffer in x1
    bl scanf            # Call scanf

    # Print greeting
    ldr x0, =greeting   # Format string: "Hello, %s!..."
    ldr x1, =name       # String read by scanf
    bl printf           # Call printf

    # Exit gracefully
exit:
    mov x0, 0   # Return code 0 (success)
    mov x8, 93  # Syscall number for exit
    svc 0
    ret
```
### Arm Basics
`MNEMONIC   DESTINATION,   OPERAND1,   OPERAND2`
`ADD X3, X1, X2, SUB X3, X2, #5`
* ADD
* SUB
* LSL: Logical shift left
* LSR: Logical shift right
* AND
* OR
* NOT
* `MOV X3, X1` copies the contents of X1 into X3.
* `MOV X3, #12` loads the immediate value 12 into X3

### Arrays and Strings
C Pointer Operators
* (asterisk) when declaring a pointer variable indicates the variable holds an address.
* when used in an expression (dereferencing) gives the value stored at the pointer’s address.
* &alt; (ampersand) returns the address of a variable.

```bash
int *p;
p = (some address);

int x = 45;
int *Q;
Q = &x;       // Q now points to x
*Q = 34;      // modifies x to 34
```
X0 = base address of the array
X1 = size (number of elements)
We choose X9 for the pointer p, X10 for size * 8, X11 for &array[size], etc.
```bash
// X0 contains base address of array
// X1 contains size
// X9 will contain p
MOV X9, X0          // p = &array[0]
LSL X10, X1, #3     // X10 = size * 8
ADD X11, X0, X10    // X11 = &array[size]

LOOP:
    STR XZR, [X9, #0]    // *p = 0  (store zero into memory at X9)
    ADDI X9, X9, #8      // p = p + 8
    CMP X11, X9          // compare end pointer to p
    B.GT LOOP            // branch if X9 < X11
```
__Arrays in Arm__
Example:
X0 stores a variable x.
X1 stores the address of an integer array arr.
X2 stores an integer i.
Accessing arr[0]: load or store from [X1, #0].
Accessing arr[i]: typically do LDR Xreg, [X1, X2, LSL #2] if each element is 4 bytes, or LSL #3 if 8 bytes, etc.
```bash
// x in X0, y in X1
// i in X19

ADD X19, XZR, XZR   // i = 0

L1:
    ADD X10, X19, X1       // &y[i]
    LDRB W11, [X10]        // load y[i] into W11
    ADD X12, X19, X0       // &x[i]
    STRB W11, [X12]        // x[i] = y[i]

    CBZ X11, L2            // if y[i] == 0, branch to L2
    ADDI X19, X19, #1      // i++
    B L1

L2:
    // end of copy
```

### Arm Data Transfer Instruction
__Load Instructions__
`LDR Xd, [Xn]` Load a doubleword (8 bytes) from memory at the address in Xn into register Xd.
`LDR Xd, [Xn, #imm]` The final address = Xn + imm or Xn + Xm.
__Store Instructions__
`STR Xs, [Xn]` Store a doubleword (8 bytes) from register Xs to memory at the address in Xn. (Also has offset addressing)
* `LDRB / STRB`: Load/store a byte (1 byte).
* `LDRH / STRH`: Load/store a halfword (2 bytes).
* `LDRSW`: Load 4 bytes (a word) and sign-extend into a 64-bit register.
* `STRW`: Store only the low 32 bits to memory (if available in your assembler variant).
__Endianness__
* Big Endian: The most significant byte is stored at the lowest address.
* Little Endian: The least significant byte is stored at the lowest address.
* ARM typically can operate in little-endian mode by default on many systems.

### ARM Decisions And Loops
__Flow Control Instructions__
B label: Unconditional branch to label.
`CBZ / CBNZ Reg, label`:
CBZ: Branch if Reg == 0.
CBNZ: Branch if Reg != 0.
Labels are used to mark lines of code to jump to.
__If-Then-Else Example__
// if (i == j) f = g + h; else f = g - h;
```bash
SUB X9, X22, X23   // X9 = i - j
CBNZ X9, Else      // if X9 != 0, go to Else
ADD X19, X20, X21  // f = g + h
B Exit
Else:
SUB X19, X20, X21  // f = g - h
Exit:
```
__Compare and Branch Using Flags__
`CMP Xn, Xm` is effectively `SUBS XZR, Xn, Xm.` It sets flags (N, Z, C, V) without storing a result.
Then use a conditional branch:
* B.EQ label (branch if Z == 1),
* B.NE label (branch if Z == 0),
* B.LT label (branch if negative),
* B.GT label (branch if greater),
```bash
MOV X9, #0          // k = 0
Loop:
    CMP X9, #11      // if k == 11
    B.EQ Exit        // exit loop if so

    ADD X10, X10, #4 // x = x + 4
    SUB X11, X10, X9 // y = x - k
    ADD X9, X9, #1   // k++

    B Loop
Exit:
```

```bash
MOV X9, #0       // k=0
Loop:
    ADD X10, X10, #4   // x = x+4
    SUB X11, X10, X9   // y = x-k
    ADD X9, X9, #1     // k++
    CMP X9, #10
    B.LE Loop
Exit:
```
* BL label: Branch with link (used for function calls). Stores the return address in X30.
* BR X30 or RET: Return from function by branching to the address in X30.

## February 12th
__ARM Procedure Calls and Stack Management__
```bash
    // Example of Function Call and Return
    MOV X0, #10        // Argument in X0
    BL my_function     // Call Function
    MOV X9, X0         // Store Return Value
    RET                // Return from Function
```
__Stack Management__
Save necessary registers on the stack before a function call.
For example, X0, X1, X2, X30, X29.
Allocate 40 bytes on the stack (5 registers x 8 bytes each).
```bash
    SUB SP, SP, #40        // Allocate 40 bytes on the stack
    STP X29, X30, [SP, #32]// Save Frame Pointer and Return Address
    STP X0, X1, [SP, #16]  // Save X0, X1
    STR X2, [SP, #8]       // Save X2
```
Restore Stack Frame:
Add 40 to the stack pointer to release space.
```bash
    LDP X29, X30, [SP, #32]// Restore Frame Pointer and Return Address
    LDP X0, X1, [SP, #16]  // Restore X0, X1
    LDR X2, [SP, #8]       // Restore X2
    ADD SP, SP, #40        // Restore Stack Pointer
    RET                    // Return to Caller
```
Precautions:
Always restore the stack pointer after using it.
Segmentation faults can occur if the stack pointer goes out of bounds.

## February 17
### ARM Memory Model
Memory is a linear array of 2^47 bytes
* Text segment (stores machine code / instructions).
* Static Data segment (stores global/static variables).
* Heap (for dynamically allocated memory).
* Stack (for local variables, return addresses, etc.).
* Reserved areas (used by the OS).

A __stack frame__ is a block of data containing:
Local variables
Saved registers (like return addresses, frame pointer, etc.)
__Local variables__ are kept on the stack.
__wX vs xX Registers__
Each 64-bit register Xn has a corresponding 32-bit register Wn.
Writing to Wn zero-extends into the upper bits of Xn.
32-bit operations often use Wn, while 64-bit operations use Xn.

### Buffer Overflow Basics
A buffer overflow occurs when a process writes data beyond the boundary of a fixed-size buffer.
If a local array (char buffer) is overflowed, it can corrupt:
Adjacent variables in the stack frame.
The function’s return address, causing the program to jump to unintended code.

__Memory Segments__
1. Text Segment: Contains program instructions.
2. Static Data Segment: Holds global variables.
3. Heap: Dynamic memory allocation (grows upward).
4. Stack: Stores local variables, function parameters, and return addresses (grows downward).
```bash
+-----------------+ Higher Memory Address
|   Kernel Space  |
|      Text       |  <- Program Instructions
|  Static Data    |  <- Global Variables
|       Heap      |  <- Dynamic Memory Allocation (Grows Up)
|       Stack     |  <- Local Variables (Grows Down)
+-----------------+ Lower Memory Address
```
__What is a Stack Frame?__
A stack frame is the portion of the stack containing:
Local variables for a running procedure.
Saved registers such as return address (X30) and frame pointer (X29).
Return address for returning to the caller function.
```bash
+-----------------+
| Return Address  | <- Overwritten if Buffer Overflow Occurs
| Frame Pointer   |
| Local Variables |
| Arguments       |
+-----------------+
```
Stack grows downward, so a buffer overflow can overwrite:
Adjacent local variables
Frame pointer (X29)
Return address (X30)

__Buffer Overflow Exploits__
Safer Programming Languages
Rust: Prevents buffer overflow by design.
Memory safety features ensure no out-of-bound access.
Borrow checker prevents dangling pointers.

## Lab and Assignment Notes
Buffer Overflow Lab Instructions:
Download and Transfer main.c to your emulator.
Compile and Run the program 
```bash
gcc -o buffer main.c
./buffer
```
Use `GDB` to analyze the memory:
```bash
gdb buffer
x/8gx $sp     // View 8 words from the stack pointer
```
Lab Objectives:
Analyze Memory Layout:

Observe how local variables and return addresses are stored.
Identify potential overflow points.
Cause Buffer Overflow:

Input a carefully crafted string to overwrite the return address.
Redirect execution to a different function or code segment.
Answer Questions and Take Screenshots:

Record memory addresses and contents.
Fill in provided tables and answer questions in the lab document.

## February 19 & 21
### Floating Point
Motivation: Integer representation alone can’t handle very large or very small numbers, nor fractional parts, leading to the need for floating-point formats.
__Overflow and Underflow__
__Overflow:__ Occurs when the exponent is too large to fit in the field.
__Underflow:__ Occurs when the number is too close to zero and the exponent is too small to represent.
__Double Precision__
64 bits total:
* Sign bit (1 bit)
* Exponent (11 bits), bias = 1023
* Fraction (52 bits)
*Idk ill need to go over this more*

__Floating Point Format__
```bash
(-1)^sign * mantissa * 2^(exponent - bias)
```
__IEEE 754 Format__
Single Precision (32-bit)
```bash
+----+----------+---------------------+
|  1 |    8     |          23          |
+----+----------+---------------------+
|Sign| Exponent |      Fraction        |
+----+----------+---------------------+
```
Double Precision (64-bit)
```bash
+----+------------+-----------------------------+
|  1 |     11     |              52              |
+----+------------+-----------------------------+
|Sign|  Exponent  |           Fraction           |
+----+------------+-----------------------------+
```
__Special Cases__
* Zero: Exponent = 0, Fraction = 0
* Denormalized Numbers: Exponent = 0, Non-zero Fraction
* Infinity: Exponent = All 1s, Fraction = 0
* NaN (Not a Number): Exponent = All 1s, Non-zero Fraction
__Exponent Bias__
Single Precision: Bias = 127
Double Precision: Bias = 1023
`Actual Exponent = Stored Exponent - Bias`

Example Calculation
```bash
Binary Representation:
0 10000010 10100000000000000000000
```
    Exponent:
    Binary: 10000010
    Decimal: 130
    Actual Exponent = 130 - 127 = 3
#### Why is IEEE Floating Point Approximate?
__Finite Number of Bits:__
Only 23 bits for the fraction (single precision) or 52 bits (double precision).
These bits approximate the value but cannot exactly represent most real numbers.
Example: 0.4 in binary is infinite like 1/3 in decimal.
__Rational Approximation:__
Only numbers that can be represented as sums of powers of 2 can be exactly represented.
Example: 
1/10 cannot exactly be represented because 10 is not a power of 2
__Rounding Error:__
Truncation or rounding occurs because of limited bits.
This introduces small inaccuracies in calculations.
__​Implied Leading 1:__
IEEE format assumes a leading 1 in the mantissa (except for denormalized numbers).
This affects precision and the range of representable numbers.

### Integer Multiplication
Multiplying two N-bit integers can produce up to a 2N-bit result.
Hardware multiplication can be expensive in both area (circuit complexity) and time.
Multiplication is conceptually done via __shift__ and __add__
```bash
      0010  (2)
  ×   1011  (11)
  ----------
   =  0010 × 1 + (0010 << 1) × 1 + (0010 << 2) × 0 + (0010 << 3) × 1
```