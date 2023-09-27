# OS
- An operating system is a program that manages a computer ’s hardware.
- It also provides a basis for application programs and acts as an intermediary between the computer user and the computer hardware.
- The hardware (CPU),the memory,and the input/output (I/O) devices —provides the basic computing resources for the system.

## Computer System (4 parts)
- Hardware
- Operating System
- Application Programs
- Users

### Moore Law
- In the 1960s, Moore’s Law predicted that the number of transistors on an integrated circuit would double every eighteen months, and that prediction has held true.
### Interrupt
- The occurrence of an event is usually signaled by an interrupt from either the hardware or the software.
-  Hardware may trigger an interrupt at any time by sending a signal to the CPU,usually by way of the system bus.
-  Software may trigger an interrupt by executing a special operation called a system call
#### How does Interrupt work 
- When the CPU interrupt is called-> The current excecution is paused and the CPU directly jumps to the fixed location from where the interrupt is being called.
-  The ﬁxed location usually contains the starting address where the service routine for the interrupt is located.
-  The interrupt service routine executes; on completion, the CPU resumes the interrupted computation. 

#### Von - Neumann Architecture 
-  Neumann architecture,ﬁrst fetches an instruction from memory and stores that instruction in the instruction register.
-  The instruction is then decoded and may cause operands to be fetched from memory and stored in some internal register.
-   After the instruction on the operands has been executed, the result may be stored back in memory. 
