#sysnet #classnotes

Left off last [[SchoolNotesVault/Fall 2023/Sys & Net/Lectures/Lecture 1|Lecture]] talking about Early mainframe systems
These systems execute a single user programs a time
performs automatic job sequencing
![[EarlyMainframeSchedule.excalidraw]]
# Multi programmed batch sys
- Several jobs exist in memory
- CPU is multiplexed among them
- scheduler algorithm must be significantly more advanced to give each job adequate compute time
- [[context switching]]
- [[memory management]] (MMU) & memory protection is needed
- Requirements
	- IO routine must be provided by OS
	- [[memory management]]
	- [[CPU Scheduling]]
	- OPERATING SYSTEM must manage I/O devices

# Interactive Time-Sharing System
- CPU is multiplexed among several jobs
- Jobs may be swapped in and out of memory
- Interactive communication between user and system
	- One to many relationship between Mainframe and Terminals

## System control
- OS assigns CPU to the next job in memory
	- program uses IO devices during execution
	- Program exits or crashes out and gives back CPU 

Loss of control for OS

- What mechanisms exist for the OS to regain control of the CPU?
	- Software and hardware interrupts
- must enforce interrupts though a timer  at the hardware level

## Hardware and Software Interrupts
- Interrupt transfers control to interrupt service routine
	- [[Overview#Interrupts|interrupt vector]] vs. interrupt service routines
- When interrupt occurs:
	- save address of instruction being interrupted
	- disallow all or most interrupts
- Drivers are linked to the handler routine on the interrupt vector

### Dual mode protection
- System must ensure that malicious or incorrect code cannot cause other programs to malfunction
- Hardware Provides support for two modes of operation:
	- user mode - execution done on behalf of user
	- kernel mode - execution done on behalf of operating system
- When the software interrupt happens, we set the **mode bit** to 0 (kernel mode)
- When we return the **mode bit** is set to 1 (user mode)
- There is no instruction to set the mode bit, it happens in the interrupt

### I/O Protection
- All I/O ops are privileged instructions
### Memory Protection
- When more than one program lives in memory, memory protection is needed
- Two hardware registers specify range of legal address space for program:
	- **MMU (Memory Management Unit)**
- A program that accesses memory outside the legal address space causes an interrupt
	- Can be tested by creating an array (malloc or new) and checking how far out of bounds we can go before we get a segfault

### CPU Protection
- must be available to all programs for execution
- Timer generates interrupt to ensure operating system regains control
- Timer is used to implement Time-Sharing systems
### System calls
#### Types
- process control
- file ops
- device ops
- communication
- ...

#### examples
- exit()
- fork()
- allocate()/free()
- open()/close()/write()/read()

[[SchoolNotesVault/Fall 2023/Sys & Net/Lectures/project 1]]