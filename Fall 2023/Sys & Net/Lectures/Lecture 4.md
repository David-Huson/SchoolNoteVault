---
Course: Systems and Networks 1
tags: classnotes, sysnet
---

Continuing from where we left off in [[SchoolNotesVault/Fall 2023/Sys & Net/Lectures/Lecture 3|Lecture 3]]

# Inside the CPU
- General purpose registers
- Special purpose registers
	- IP.PC: instruction pointer/program counter
	- IR: instruction register
	- SP: stack pointer
# Fetch/Execute Cycle
1. Fetch instruction at address PC into IR
2. Increment PC (by 1, 2, 4, ?)
3. Decode instruction in IR
4. *Check for interrupts*
5. Go back to step 1
## Runtime Stack
- SP has address of top of runtime stack
- Runtime stack contains "activation records"
- Stack grows down
- Call to function
	- creates activation record for function
	- pushes AR onto stack
	- jumps to code for function
### Activation Record
- Contains:
	- parameters
	- local variables
	- return value
	- return address
	- other items
```c
int add(int x, int y) {
	int z;
	z = x + y;
	return z;
}

int main() {
	int val;
	val = add(2, 3);
	printf("%d\n", val)
	return 0;
}
```
## Function calls
1. Push args onto stack
2. push local vars onto stack
3. push ret address onto stack
4. push ret val onto stack
5. jump to user-defined code
Limited in what it can do
Only access to user-mode instructions 

### Execution Modes
### User-Mode
- add
- mult
- load
- stor
### Kernel-Mode
- in
- out
- port
- cmod

### CPU
has execution **mode** bit
- 0 - CPU is currently in kernel-mode
- 1 - CPU is currently in user-mode

`cmod` instruction changes mode _from kernel to user_ 
No instruction to move *from user to kernel*

## System Call
1. push args onto stack
2. push local vars onto stack
3. push RA onto stack
4. push return val onto stack
	1. created AR
5. switch to kernel
	1. trap instruction triggers interrupt
6. jump to system defined code
Access to all instructions

### Transitions to kernel mode
#### Software
- syscall
- called a "trap" into the kernel
- j to well-known function
- hardware switches to kernel mode
	- ex: `printf()` or `read()`
#### Exception
- Error state or debugging
- similar to syscall without return (error)
- Hardware switches to kernel mode
- Example: devision by zero or segfault
- Result: core dump

#### Hardware
- Called an "interrupt"
- Communication between kernel and devices
- **can occur between any two instructions**
- Similar to syscall without call
- J to well known function
	- interrupt handler routine in the interrupt vector
- Hardware switches to kernel mode
- Example: clock tick or I/O complete

### Executing instructions
- store PC and other values pertaining to the instruction execution gets stored in the Process control block

Review [[Context Switches]] in the [[Operating System Concepts.pdf|Textbook]]