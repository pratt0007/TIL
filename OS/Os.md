# OS
- An operating system is a program that manages a computer ’s hardware.
- It also provides a basis for application programs and acts as an intermediary between the computer user and the computer hardware.
- The hardware (CPU),the memory,and the input/output (I/O) devices —provides the basic computing resources for the system.
### 3 basic work of OS-
  - An operating system is a program that manages a computer ’s hardware, interface between user and hardware.
  - Resource Manager - Manage system resources in an unbaised fashion both for hardware and software.
  - Platform for applications, all the application will interact with OS not with the hardware directly.

![image](https://github.com/pratt0007/TIL/assets/100209212/4dd69ed7-4f99-411e-946e-26cbbeff32f8)

### Goal of OS
- Primary Goal - convienece and user friendly.
- Secondary Gaol - efficiency

### Feature of Operating System 
- Process management
- memory management
- I/0 device management
- File management
- Network Management
- Security and protection

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

![Screenshot 2023-09-27 204116](https://github.com/pratt0007/TIL/assets/100209212/d0d0be73-4aa3-4ee7-b057-35d55aef80b9)


### How a mordern computer system works
![image](https://github.com/pratt0007/TIL/assets/100209212/d1ed55a4-514a-45e5-bb0f-4a8d5c2a570d)

### Process Management 
- Scheduling processes and threads on the CPUs
- Creating and deleting both user and system processes
- Suspending and resuming processes
- Providing mechanisms for process synchronization
- Providing mechanisms for process communication

### Memory Management 
- Keeping track of which parts of memory are currently being used and who is using them
- Deciding which processes (or parts of processes) and data to move into and out of memory
- Allocating and deallocating memory space as needed

### Storage  Management
  #### File Management
    - Creating and deleting ﬁles.
    - Creating and deleting directories to organize ﬁles
    - Supporting primitives for manipulating ﬁles and directories
    - Mapping ﬁles onto secondary storage
    - Backing up ﬁles on stable (nonvolatile) storage media
  #### Caching
  - Information is normally kept in some storage system (such as main memory).
  - As it is used, it is copied into a faster storage system — the cache — on atemporary basis.
  - When we need a particular piece of information, we ﬁrst check whether it is in the cache.
  #### I/O Systems
  - A memory-managementcomponent that includes buffering,caching,and spooling
  - Ageneraldevice-driverinterface
  - Drivers for speciﬁc hardware devices
## Types of OS
- Single Process OS
- Batch OS
- Multi programming
- Multi tasking
- Multi Processing
- Distributed
- Real Time OS
### 1. Batch OS
![image](https://github.com/pratt0007/TIL/assets/100209212/f7790f33-bbd3-4276-9ba4-fda19525d679)
#### JOB-
    - Program 
    - I/P Data
    - Control Instructions
#### Drawbacks of Batch Processing
- Speed mismatch between the I/P receiving and O/p generation leading to latency.
- No prioritization between Jobs

### 2. MULTI-PROGRAMMING
![image](https://github.com/pratt0007/TIL/assets/100209212/bf29261e-8c37-4848-9128-9f947a6084a0)
- In this, multiple programs are kept and the CPU switches its processing on different processes if one is not available or goes for to I/O,
- IMP - IN THIS AT A SINGLE TIME ONLY SINGLE PROCESS IS HANDLED NOT MULTIPLE.
### 3. Multi Tasking
![image](https://github.com/pratt0007/TIL/assets/100209212/db0b2480-cd7a-4c3b-94cb-fb486ff60ac7)
- In one time only one process can be taken care of by one cpu

### Virtual Memory Concept
#### Process State
![image](https://github.com/pratt0007/TIL/assets/100209212/f760fa80-4943-4e4f-b29d-23e5f66e2a0b)

 ![image](https://github.com/pratt0007/TIL/assets/100209212/afccf626-434c-4d23-ac1c-6b0a65e72780)
 - There are basic 5 block-
     - New - When we store a file in the secondary memeory. Just storing the code.
     - Ready - When we run the code the fetched from the secondary mem to primary (RAM) or The Ready Queue. 
     - Running - Running is the state when the process from the ready queue(RAM) is given to the CPU.
     - Wait Block- It is the waiting queue when the process goes for I/O  or Interrupt comes, or the process with higher priority comes.
     - Terminate - When the logic or code is excecuted.
- There is a suspended wait system attached to the wair block queue which is inside the ram only, if the wait block queue if full then some of the process go in Suspended wait which is present in th secondary memory
- Similar to this is on ready queue.

### Process Control Block(PCB)
- Each process is represented in the operating system by a process control block (PCB) —also called a task control block.
![image](https://github.com/pratt0007/TIL/assets/100209212/80334e57-8876-4572-9ab5-63bdc13855b4)
![image](https://github.com/pratt0007/TIL/assets/100209212/547ef16a-e2a7-4301-b1b1-225c2718a2cd)
![image](https://github.com/pratt0007/TIL/assets/100209212/fcd6971d-414d-4a46-86ab-9e4eaf041d7c)

### System Call
- File Related : access open , read, write , close , create etc
- Device Related system calls - Hard disk , monitor , pendrive
- Information Related system call
-  To acces all this we need to go in kernel mode.
-  In Linux we direct apply system call but in Windows and all we have APIs. We call function and then function calls the system.
-  system call invoke the kernel to do the job.

#### FORK System Call
- This call is made to create a child process. The child process will be clone of parent prcoess with only different ID.
- Child process does the job when the parent process if busy.
- If we fork any process, then simultaneously the parent and child prcoess works on different task.
- If we fork then child ID is 0 (If created) if ID = -1 then fork is not done. 
![image](https://github.com/pratt0007/TIL/assets/100209212/f5bd10b8-1427-4b66-90d3-44ccf2170895)
### User mode and Kernel Mode

