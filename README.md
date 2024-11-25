
# Operating System
---
---
# Introduction

### What is OS
- Software abstracting hardware
- Interface between user and hardware
- Set of utilities to simplify application development/execution
Control program
- Acts like a government

### Services of Operating Systems
- User Interface
- Program Execution
- I/O Operation
- File-System Manipulation
- Communication (Inter-process Communication)
- Error Detection
- Resource Allocation
- Accounting
- Protection & Security

### Goals of Operating Systems
- Convenience - User-friendly
- Efficiency
- Portability
- Reliability
- Scalability - can increase the no of users
- Robustness - can handle unexpected errors

### Parts of OS
- **Kernel** - ALL Functionalities of OS
- **Shell** - Interdace - GUI or CLI

### System Call
A system call is a way for programs to interact with the operating system

### Dual Mode of Operations of OS
![](https://images.javatpoint.com/operating-system/images/dual-mode-operations-in-operating-system3.png)

### Types of Operating Systems
- **Uni-programming OS** - One single process reside in Main memory 
- **Multi-programming OS** - Multiple processes reside in Main memory
  - **Non-Preemtive** - A process runs in cpu till it wants to be
  - **Preemtive** - A process can be forcefully taken out of the CPU
- **Multi-tasking** - Extension of multi-programming OS in which processes execute in round-robin fashion.
- **Multi-Processing OS** - Multiple CPUs
  - **Tightly Coupled** - each CPU has a common Main Memory
  - **Distributed** - each CPU has its own Main Memory
- **Embedded OS** - specialized for Embedded Systems
- **Real-Time OS** - Used in environments where a large number of events, mostly external to the computer system, must be accepted and processed in a short time or within certain deadlines.
  - **Hard**
  - **Soft**

---
---

# Process Management

### What is the Process?
- Program under execution
- An instance of a program
- Schedulable/Dispatchable unit (CPU)
- Unit of execution (CPU)
- Locus of control (OS)

### Representaion of Process
![](https://icarus.cs.weber.edu/~dab/cs1410/textbook/4.Pointers/images/layout.png)

### Process Control Block
- Also Known as process descriptor
- **Attributes**:
  - PID (Process ID)
  - PC (Program Counter)
  - GPR (General-Purpose Registers)
  - List of Devices
  - Type of Process
  - Size of Process
  - Memory Limits
  - Priority
  - State of Process
  - List of Files

#### Context
- The content of PCB of a process are collectively know as 'Context' of that process

### Context Switch
**Context Switch** = Context save + Context Load
- stop a running proces & run another process

### Process States
![](https://i.ibb.co/WzSt5zm/Process-States-States.png)

### CPU vs IO Bound Process
- **CPU Bound**: If the process is intensive in terms of CPU operations
- **IO Bound**: If the process is intensive in terms of IO operations

### Scheduling Queues
- **Job Queue**:  
   - Contains all processes that are in the new state
- **Ready Queue**:  
   - Contains all processes that are in the ready state
- **Device Queue**:  
   - Contains all processes that are waiting for a specific I/O device to complete their request.  

### Types of Scheduler
- **Long-Term Scheduler**: New → Ready
- **Short-Term Scheduler**: Ready → Running
- **Medium-Term Scheduler**: Ready/Waiting ↔ Suspended


