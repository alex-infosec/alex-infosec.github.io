
run start 
run transfer
make sure the main file is in the wrkdirectory
learn how to access the work direct
make sure to recompile the gcc.o or main when you change the 
send gpt copy paste the register rather than the screeenshot
# The Buffer Overflow Lab
__Task 1 -Compile main.c__
```bash
# Task 1 - Compile main.c
Compile the program using the following command:
```bash
gcc -o main main.c -g
```

__Task 2 – Run main from the debugger, without causing buffer overflow__
Enter the debugger with: `gbd main`
Set breakpoints with `b get_input and b benign_function`
run the program with `r`
Disassemble the main function: `dissassemble main`

