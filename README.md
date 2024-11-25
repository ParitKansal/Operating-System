
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
![](https://i.ibb.co/B2nYVwz/Process-structure.png)


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

## CPU Scheduling Algorithms

### **Scheduling Times**
1. **Arrival Time (AT):** The time at which the process arrives in the system.
2. **Burst Time (BT):** The amount of time for which the process runs on the CPU.
3. **Completion Time (CT):** The time at which the process completes (exit time).
4. **Turnaround Time (TAT):** Time from arrival to completion.**Formula:** $\text{TAT} = \text{CT} - \text{AT}$
5. **Waiting Time (WT):** The time the process spends waiting in the ready queue. **Formula:** $\text{WT} = \text{TAT} - \text{BT}$
6. **Response Time (RT):**  The amount of time from the arrival of a process until it gets the CPU for the first time.
7. **Scheduling Length (L):**  The total time required to complete all processes.  **Formula:**  $L = \max(\text{CT}) - \min(\text{AT})$
8. **Throughput:**  The number of processes executed per unit of time.

### **First Come First Serve (FCFS)**
- **Criteria** - Arrival Time
- **Tie reaker** - Smaller process id
- **Type** - Non-Preemptive

### **Sortest Job First (SJF)**
- **Criteria** - Burst Time
- **Tie reaker** - FCFS
- **Type** - Non-Preemptive

### **Sortest Remaining Time First (SRTF)**
- **Criteria** - Remaining Time
- **Tie reaker** - FCFS
- **Type** - Preemptive

### **Highest Response Ration Next**
- **Criteria** - Highest Response Ration = 1 + WT/BT
- **Tie reaker** - Burst Time
- **Type** - Non-Preemptive

### **Priority Based Scheduling**
- **Criteria** - Priority
- **Tie reaker** - FCFS
- **Type** - Preemptive and Non-Preemptive

### **Round-Robin Scheduling**
- Processes are queued in the ready queue in the order they arrive.- If multiple processes arrive simultaneously, the Process ID determines the order.
- The process at the front of the queue is executed for a fixed time quantum (*Q*).
- If the process isn’t completed within this time, it is re-queued at the back of the queue (after enqueuing any new arrivals).

### Quantum values in Round-Robin scheduling
- **Small $Q$:** Interactive
- **Very Large $Q$:** similarly to FCFS (First Come First Serve)
- **Large $Q$:** Less  Interactive
- **Very Small $Q$:** CPU spends more time in context switching than in actual execution, reducing CPU efficiency

### **Multilevel Queue Scheduling**
1. **Fixed Priority preemptive Scheduling method**- 

   ![](https://media.geeksforgeeks.org/wp-content/uploads/multilevel-queue-schedueling-1-300x217.png)
3. **Time Slicing**- (Q1, 60%) , (Q2, 30%) , (Q3, 10%) 

### **Multilevel Feedback Queue Scheduling**
![](https://media.geeksforgeeks.org/wp-content/uploads/Multilevel-Feedback-Queue-Scheduling-300x269.png)
- If a process do not get completed in one Q time it is moved to lower priority queue

---
---


# Threads & Multithreading

### Thread
- Component of process
- Lightweight Process
- Provide a way to improve application performance through parallelism

|Shared Among Threads   | Unique For Each Thread|
|-----------------------|-----------------------|
|Code Section           | Thread Id             |
|Data Section           | Register Set          |
|OS Resources           | Stack                 |
|Open Files & Signals   | Program Counter       |

![](https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/images/Chapter4/4_01_ThreadDiagram.jpg)

### Types of Threads
|User Threads|Kernel Thread|
|-|-|
|Multithreading in user process|Multithreading in kernel process|
|Created without kernel intervention|Kernel itself is multithreaded|
|Context switch is very fast|Context switch is slow|
|If one thread is blocked, OS blocks entire process|Individual thread can be blocked|
|Generic and can run on any OS|Specific to OS|
|Faster to create and manage|Slower to create and manage|

### Multi-threading Models in OS

![](https://i.ibb.co/P9LRFfW/multi-threading-models-in-os.png)

---
---

