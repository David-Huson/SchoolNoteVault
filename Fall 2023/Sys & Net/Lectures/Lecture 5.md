---
tags:
  - classnotes
  - sysnet
Course: Systems and Networks 1
Chapter:
---
The operating system needs to maintain information about processes in the Process Control blocks

This can be achieved using a hash table, a linked list, or an array.

linked list is advantageous because it has O(1) insertion at the beginning or end

- During boot, one process is created
	- PID = 1
	- usually named "init"
- All pother processes are *descendants* of init
- Processes form hierarchy:
	- parents. & children
	- all children have one parent
	- parents can have any number of children
- Address space
	- parent and children may share address space
	- create a new address space for child
- System call to create a new process: `fork()`
	- takes no parameters
	- makes a copy of the current process
	- new PCB, new memory, same parent
	- memory copy: old to new
		- copies on demand
	- PCB copy: old to new
	- new PID
		- parent knows children PID
		- child thinks its PID is 0
- Stack, code and data are all part of the address space
The operating system (scheduler) determines which process should execute first

File descriptor table -> list of open file descriptors

Parent and child will change the Program Counter as they execute

if(pid) returns true if pid != 0

- we can clone a process
- we can create a clone of myshell
- we want to create ls instead of myshell
	- try the exec() family of syscalls
	- execl(path, arg)
	- execlp(file, arg)
	- execle(path, arg, ..., envp[])
- the exec function family replaces the code in the current process image with the new process image
	- the file arg is the name of the program we want to execute
		- ex: ls, cat, grep ...
	- the path is the path to the program to be ran

# Project notes
use a fork syscall to run the commands (i.e. ls, cp, grep, etc.)

the fork call will copy the parent's address space, so we can load the current command into memory to let the child know what command it should issue.


call wait or waitPID to make parent wait for child to finish execution so the child does not become a zombie


make sure that we wait for the program to complete its execution before termination (exit)