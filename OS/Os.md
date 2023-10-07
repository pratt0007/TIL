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
