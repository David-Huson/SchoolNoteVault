#sysnet
# Overview
## What is an operating system?
- a program which mediates hardware resources and the user
	- the **Kernel**, the one program running at all times
- resource allocator
- control program

## What is the purpose of an operating system
- Facilitate program execution
- support program development
- make sys easy to use
- uses resources efficiently

> **MMU** -> memory management unit

ways in which programs can get shutdown w/o user intervention:
 - segfault
	 - must keep programs from overwriting others
 - div/0
	 - ALU sends interrupt

![[Operating system diagram.excalidraw]]

In kernel mode you can execute any instructions, in user mode you cannot execute privileged instructions

The operating system is on the Disk, in memory, and in the cpu cache while being executed

## I/O operation
> Remind Dr. Reichherzer to bring in a disk drive to next class

- Devices are operated by a controller to allow it to operate concurrently with the CPU
	- Uses an interrupt to alert CPU
	- has a local buffer for data exchange
- CPU or DMA(Direct Memory Access) perform data exchange

## Multiprocessor system

- **Symmetric** - all processors execute all functions of the operating system
- **Asymmetric** - master processor controls system, all other processors execute assigned job
	- not as efficient because it allows for underuse of memory and cpu resources
	- creates a bottleneck
### Dual core systems
- Cores execute all sys functions
- Cores may share cache
- L1 cache is closest to registers
Registers -> L1 -> L2 -> L3 -> Main memory

