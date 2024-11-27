
# Operating System
---
---
# **Introduction**

## What is OS
- Software abstracting hardware
- Interface between user and hardware
- Set of utilities to simplify application development/execution
Control program
- Acts like a government

## Services of Operating Systems
- User Interface
- Program Execution
- I/O Operation
- File-System Manipulation
- Communication (Inter-process Communication)
- Error Detection
- Resource Allocation
- Accounting
- Protection & Security

## Goals of Operating Systems
- Convenience - User-friendly
- Efficiency
- Portability
- Reliability
- Scalability - can increase the no of users
- Robustness - can handle unexpected errors

## Parts of OS
- **Kernel** - ALL Functionalities of OS
- **Shell** - Interdace - GUI or CLI

## System Call
A system call is a way for programs to interact with the operating system

## Dual Mode of Operations of OS
![](https://images.javatpoint.com/operating-system/images/dual-mode-operations-in-operating-system3.png)

## Types of Operating Systems
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

# **Process Management**

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


# **Threads & Multithreading**

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


# **Process Synchronization**

#### **Types of Processes**
1. **Independent** - None communication with any other process
2. **Cooperating/Coordinating/Communicating** - Can affect be other process or can be affected by other Can process.

#### **Problems without Synchronization:**
- Inconsistency
- Loss of Data
- Deadlock

#### **Critical Section**
The critical section is a code segment where the shared variables can be accessed

#### **Race Condition** 
A race condition is an undesirable situation, it occurs when the final result of concurrent processes depends on the sequence in which the processes complete their execution.


## Solution for Critical Section Problem

#### **Requirements of Critical Section problem solution**:
1. **Mutual Exclusion** - If one process use that critical section then other process can not use that critical section
2. **Progress** - of no process is in critical section and at least 1 process wants to enter or exess critical section then it should be allowed
3. **Bounded Waiting** - Waiting of processes should be Bounded

### **Using Lock**

<table>
<tr>
    <th>P0
    </th>
    <th>P1
    </th>
</tr>
<tr>
  <td>
  <pre>
while(lock);
lock = True;
CS;
lock = False;
</pre>

  </td>
  <td>
    <pre>
while(lock);
lock = True;
CS;
lock = False;
</pre>

  </td>
</tr>

</table>

- **Mutual Exclusion** - No 
- **Progress** - Yes

### **Using Turn**

<table>
<tr>
    <th>P0
    </th>
    <th>P1
    </th>
</tr>
<tr>
  <td>
  <pre>
while(turn == True);
CS;
turn = False;
</pre>

  </td>
  <td>
    <pre>
while(turn == False);
CS;
turn = True;
</pre>

  </td>
</tr>

</table>

- **Mutual Exclusion** - Yes 
- **Progress** - No
- **Bounded Waiting** - Yes


### **Peterson's Solution**
<table>
    <tr>
     <td colspan = 2>Flag[0] = False, Flag[1] = False</td>
    </tr>
    <tr>
        <th>
            P0
        </th>
        <th>
            P1
        </th>
    </tr>
    <tr>
        <td>
<pre>
Flag[0] = True;
turn = 1;
while(flag[1] && turn = 1);
CS;
Flag[0] = False;
</pre>
        </td>
        <td>
<pre>
Flag[1] = True;
turn = 0;
while(flag[0] && turn = 0);
CS;
Flag[1] = False;
</pre>
        </td>
    </tr>
</table>

- **Mutual Exclusion** - Yes 
- **Progress** - Yes
- **Bounded Waiting** - Yes

### **Synchronization Hardware**
### TestAnsSet()
- Return the current flag value and set it's value to True
```
bool TestAnsSet(bool* flag){
    bool temp = *flag;
    *flag = True;
    return temp;
}
```

<table>
<tr>
<td colspan = 2>Flag[0] = False, Flag[1] = False</td>
</tr>       
<tr>
<th>
P0
</th>
<th>
P1
</th>
</tr>
<tr>
<td>
<pre>
TestAnsSet(&flag);
CS;
Lock = false;
</pre>
</td>
<td>
<pre>
TestAnsSet(&flag);
CS;
Lock = false;
</pre>
</td>
</tr>
</table>



- **Mutual Exclusion** - Yes 
- **Progress** - Yes
- **Bounded Waiting** - Yes

### **Semaphore**

#### **Wait() & Signal()**
<table>
 <tr>
 <th>Wait()</th>
 <th>Signal()</th>
 </tr>
 <tr>
 <td>
<pre>
wait(S){
    while(S <= 0);
    S--;
}
</pre>
 </td>
 <td>
<pre>
Signal(S){
    S++;
}
</pre>
 </td>
 </tr>
</table>

|binary Semaphore|Counting Semaphore|
|----------------|------------------|
|Only 2 values-0/1|Any values       |
|It is used to implement the solution of critical section problems with multiple processes|It is used to control access to a resource that has multiple instances|

<table>
 <tr>
     <td colspan = 2>S = 1</td>
    </tr>
    <tr>
        <th>
            P0
        </th>
        <th>
            P1
        </th>
    </tr>
    <tr>
        <td>
<pre>
Wait(S);
CS;
Signal(S);
</pre>
        </td>
        <td>
<pre>
Wait(S);
CS;
Signal(S);
</pre>
        </td>
    </tr>
</table>

**Characteristics of Semaphores**
- Used to provide mutual exclusion → binary
- Used to control access to resources → couting
- Solution using semaphore can lead to have deadlock
- Solution using semaphore can lead to have starvation
- Solution using semaphore can be busy waiting solutions
- Semaphores may lead to a priority inversion
- Semaphores are machine-independent

---
---

# **Classical Problems on Synchronization**

## **Bounded Buffer**
![](https://www2.it.uu.se/education/course/homepage/os/vt20/images/module-4/bounded-buffer-medium-details.png?width=555px)
- Producers must block if the buffer is full
- Consumers must block if the buffer is empty

#### **Variables**:
- **Mutex**: Binary Semaphore to take lock on buffer (Mutual Exclusion)
- **Full**: Counting Semaphore to to denote the number of Foccupied slots in buffer
- **Empty**: Counting Semaphore to denote the number of empty slots in buffer

#### **Initialization**
**Mutex** = 1, **Full** = 0, **Empty** = N

<table>
<td>
<pre>
Producer(){
    Wait(empty)
    // Produce an item
    Wait(Mutex)
    // Add item to buffer
    Signal(Mutex)
    Signal(full)
}
</pre>
</td>
<td>
<pre>
Consumer(){
    Wait(full)
    Wait(Mutex)
    // Remove an item to buffer
    Signal(Mutex)
    // Consume an item
    Signal(empty)
}
</pre>
</td>
</table>

---

## **Reader-Writer Problem**
Consider a situation where we have a file shared between many people: 
- If one of the people tries editing the file, no other person should be reading or writing at the same time, otherwise changes will not be visible to him/her
- However, if some person is reading the file, then others may read it at the same time

#### **Variables**
- **mutex**: Binary Semaphore to provide Mutual Exclusion
- **wrt**: Binary Semaphore to restrict readers and writers if writing is going on
- **readcount**: Integer variable, denotes number of active readers

#### **Initialization**:
**mutex**: 1, **wrt**: 1, **readcount**: 0

<table>
<td>
<pre>
Writer(){
    Wait(wrt)
    // Preform writting
    Signal(wrt)
}
</pre>
</td>
<td>
<pre>
Reader(){
    Wait(mutex)
        readcount++;
        if(readcount == 1)
            Wait(wrt)
    signal(mutex)
    // Perform Reading
    Wait(mutex)
        readcount--;
        if(readcount == 0)
            signal(wrt)
    Signal(Mutex)
}
</pre>
</td>
</table>

===

## **Dining Philosopher**
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ4rExdMYrwSEnrW_7lgJIXAMQJTVwPrBlQHQ&s)
- K philosophers seated around a circular table
- There is one chopstick between each philosopher
- A philosopher may eat if he can pick up the two chopsticks adjacent to him
- One chopstick may be picked up by any one of its adjacent followers but not both

<table>
  <tr>
    <td>
      For 4 People
    </td>
    <td>
      For 1 People
    </td>
  </tr>
  <tr>
    <td>
    <pre>
    Wait(chopstick[i])
    Wait(chopstick[(i+1)%k])
    //eat
    Signal(chopstick[i])
    Signal(chopstick[(i+1)%k])
    </pre>
    </td>
    <td>
    <pre>
    Wait(chopstick[(i+1)%k])
    Wait(chopstick[i])
    //eat
    Signal(chopstick[i])
    Signal(chopstick[(i+1)%k])
    </pre>
    </td>
  </tr>
</table>

---
---

# **Deadlock**
- If two or more processes are waiting for such an event which is never going to occur


### **Necessary Conditions for Deadlock**:

Deadlock can occur only when all the following conditions are satisfied simultaneously:

1. **Mutual Exclusion**: If one process is using a resource, other processes cannot use it at the same time.
2. **Hold and Wait**:  A process must be holding at least one resource and waiting to acquire additional resources that are currently held by other processes.
3. **No Preemption**:  Resources cannot be forcibly taken away from a process.
4. **Circular Wait**:  A set of processes must exist such that each process is waiting for a resource held by the next process in the chain, forming a circular chain.

### **Recovery From Deadlock**
1. Make Sure that deadlock never occur:
    a) Prevent the system from deadlock
    b) avoid deadlock
2. Allow deadlock, detect and recover
3. Pretend that there is no any deadlock

### **Deadlock Prevention**
Prevent any of four necessary conditions to occur
- **Mutual Exclusion**
    - Have enough resources to provide simultaneous execution: require more no of resources
    - Make all processes independent: practically not possible 
- **Hold & Wait**
    - all (process resources are available then acquire or else just wait for all. may suffer from starvation.)
    - If process is trying to acquire a resource which is not available, while holding holding some resources; then process will release the allocated resources.
- **No Preemption**
    - Preempt one or more resources from processes
- **Circular Wait**
    - All resources have unique sequence numbers, `R1`, `R2`, `R3`, ... `Rn`.
    - A process holding resource `Ri` can only request another resource `Rj` if **`j > i`**.
    - If a process holding `Ri` wants `Rj` where `j < i`, it must:
        - Release `Ri`.
        - Acquire `Rj` before reacquiring `Ri`.

### **Deadlock Avoidance**
- In deadlock avoidance, the OS tries to keep system in safe state
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709957662333/f47a6292-169c-4183-9b21-ded4936213ec.png?auto=compress,format&format=webp)
  
### Banker's Algorithm Steps

```
1.  Let Work and Finish be vectors of length m and n, respectively.Initialize Work = Available and Finish[i] = false for i = 0,1,2,...,n-1.
2.  Find an indec i such that both
     a. Finish[i] == false
     b. Need_i <= Work
    If ni such i exits, go to step 4.
3.  Work += Allocation_i
    Finish[i] = true
    Go to step 2.
4.  If finish[i] == true for all i, then the system is in a safe state
```

**Question**

 ![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2016/01/safety.png)

### **Deadlock Detection**
#### **Wait For Graph**
![https://scanftree.com/operating-system/images/Resource-Allocation-and-Wait-for.jpg](https://scanftree.com/operating-system/images/Resource-Allocation-and-Wait-for.jpg)
- If all resource categories contains only one instance for each, then the presence of a cycle in the resource-allocation graph indicates the guarantee of a deadlock. 
- If a resource category contains more than one instance, then the presence of a cycle in the resource-allocation graph indicates the possibility of a deadlock, but does not guarantee one.

#### **Deadlock Detection Algorithm**
```
1.  Let Work and Finish be vectors of length m and n respectively
    Initialize Work= Available. For i=0, 1, ...., n-1, if Request_i = 0, then Finish[i] = true; 
    otherwise, Finish[i]= false.
2.  Find an index i such that both
    a) Finish[i] == false
    b) Request; <= Work
    If no such i exists go to step 4.
3.  Work Work+ Allocation
    Finish[i]= true
    Go to Step 2.
4.  If Finish[i]== false for some i, 0<=i<n,
    then the system is in a deadlocked state.
    Moreover, if Finish[i]==false the process P, is deadlocked
```
**Detection-Algorithm Usage**
1. Do deadlock detection after every resource allocation
2. Do deadlock detection only when there is some clue

### **Recovery From Deadlock**
There are three basic approaches to recovery from deadlock:
- Inform the system operator and allow him/her to take manual intervention
- Terminate one or more processes involved in the deadlock
- Preempt resources.

### Process Terminatio
- Terminate all processes involved in the deadlock
- Terminate processes one by one until the deadlock is broken

Many factors that can go into deciding which processes to terminate next:
- Process priorities.
- How long the process has been running, and how close it is to finishing.
- How many and what type of resources is the process holding
- How many more resources does the process need to complete
- How many processes will need to be terminated
- Whether the process is interactive or batch

### Resource Preemption
Important issues to be addressed when preempting resources to relieve deadlock:
- Selecting a victim
- Rollback
- Starvation

---
---
# **Memory Management**

### Functions of Memory Management
- Memory allocation
- Memory deallocation
- Memory protection

### Goals of Memory Management
- Maximum Utilization of space
- Ability to run larger programs with limited space

## **Techniques of Memory Management**
- **Contiguous**: Entire process should be stored on consecutive memory locations
    - **Fixed Partition**: The main memory is devided into fixed no. of partitions and each partition can be used to accomodate  max. one process.
    - **Variable Partition**
- **Non Contiguous**
    - **Paging**
    - **Segmentation**

## **Fixed Partition**
### **Partition Allocation Policy**
- **First Fit**: Allocates the first available memory block that is large enough for the process.
- **Best Fit**: Allocates the smallest available memory block that is large enough for the process.
- **Worst Fit**: Allocates the largest available memory block to leave the largest possible leftover space.
- **Next Fit**: Similar to First Fit but starts searching from the last allocated position instead of the beginning of the memory.

**Internal Fragmentation:** Occurs when a memory block allocated to a process is larger than the process's actual requirement, leaving unused space within the block.
 
## **Variable Partition**
The main memory is not pre-divided into fixed-sized partitions. When a process arrives, a partition is dynamically created with a size equal to the process's size.

**No Internal Fragmentation**: Since the partition size matches the process size, no extra space is wasted within the allocated block.

**External Fragmentation**: External fragmentation occurs when there is enough total memory space to satisfy a process's requirements, but the available memory is not contiguous (i.e., it is scattered in small, non-adjacent blocks).

**Compaction**: Compaction is a memory management technique used to collect all allocated processes to one side of memory, creating a single large block of free space on the other side.

## **Paging**
- Process is divided in equal size of pages
- Physical memory is divided in same equal size of frames
- Pages are scattered in frames

![](https://i.ibb.co/Kh6PYyV/PAging.png)

- Bits for page no  =   log(No of Pages in Process)
- Bits for byte no  =   log(Page Size)
- Bits for frame no =   log(No of frames in Pysical Memory)
- No of enteries in the page table = No of pages in process
- Size of Page table = No of enteries in the page table * 1 entry size = No of pages in process * 1 entry size

### **Time Required in Paging**

$\text{Effective Memory acess Time} = \text{Page table acess time} + \text{Main Memory acess Time}$

**If Page Table in Main Memory**
- $\text{Effective Memory acess Time} = 2 \times \text{Main Memory Access Time}$

**If Page Table in Register**
- $\text{Effective Memory acess Time} = \text{Main Memory Access Time}$

**If TLB is Present**
- $\text{Effective Memory acess Time} = H \times (\text{TLB Access Time} + \text{Main Memory Access Time}) + (1 - H) \times (\text{Page Table Access Time} + \text{Main Memory Access Time})$

### Translation Lookaside Buffer (TLB)

A Translation Lookaside Buffer (TLB) is a hardware component used to reduce the time required to access a user memory location. It stores a small number of page table entries that the CPU accesses frequently, allowing for faster translation of virtual addresses to physical addresses and enabling quicker memory access.

#### Types of Mapping
- Direct Mapping
- Set associative Mapping
- Fully associative Mapping

 
<table>
  <tr>
    <td colspan = 3>
      Logical address
    </td>
  </tr>
  <tr>
    <td colspan = 2>
      Page Number
    </td>
    <td>
      Byte Number
    </td>
  </tr>
  <tr>
    <td>
      Tag
    </td>
    <td>
      TLB Set Number
    </td>
    <td>
      Byte Number
    </td>
  </tr>
</table>


- Bits For Logical Address = Bits for page no + Bits for Byte no
- Bits for page no = Bits for Tag + Bits for TLB Set Number
- Bits for page no = log(No of Pages in Process)
- Bits for byte no = log(Page Size)
- Bits for TLB Set Number = log(Number of Sets in TLB)
- Number of sets in TLB = No of Entries in TLB / K 
- Total Tag Directory Size = Number of Entries in TLB * Tag Size = Number of Sets in TLB * k * Tag SizeBits for page no = log(No of Pages in Process)
- Bits for frame no = log(No of frames in Pysical Memory)
- No of enteries in the page table = No of pages in process
- Size of Page table = No of enteries in the page table * 1 entry size = No of pages in process * 1 entry size

### Multi Level Paging
![](https://i.ibb.co/jygvPG5/Multi-Level-Paging.png)

## Segmentation
- Divide Process in logically related partitions (Segments)
- Segments are scattered in physical memory
- Segments Can be of Variable sizes
    ![](https://media.geeksforgeeks.org/wp-content/uploads/20230703104323/ezgifcom-gif-maker-(15).webp)

---
---
# Virtual Memory
- Feature of OS
- Enables to run larger process with smaller available memory

### **Demand Paging**

- Pages are brought into memory only when the CPU demands them.
- When the CPU demands a page that is not in main memory, a **page fault** occurs.
- **Page Fault Handling**:
    - The operating system identifies the missing page in secondary memory.
    - The page is brought from secondary memory to main memory.
    - If there is no free space in main memory: A page replacement algorithm is used to remove an existing page.
    - The page table is updated to reflect the change.
    - The CPU resumes its execution.


- Extra bits in Entry in Page table contains-
    - Valid bits
    - Modified bit

## Page Replacement Algorithm
- **First In First Out**: replace that page which brought to memory first.
- **Last In First Out**
- **Optimal Policy**: replace page which is not (never) going to be refered in near future
- **Least Recently Used**
- **Least Frequently Used**: replace page which has been used minimum number of times
- **Most Frequently Used**: replace page which has been used maximum number of times
- **Second Chance Replacement**:
    - When we bring a new page into main memory (MM), **R = 0** (indicating the page has not been used yet).  
    - When the page is accessed (referred), **R = 1**.  
    - Pages are replaced using the **FIFO** algorithm, but only if **R == 0** (i.e., the page has not been recently used).  
    - If a page is given a **second chance** or **page fault** taken place, its **R value is reset to 0**.

### **Types of Page Tables**
- **Hierarchical**: 
- **Inverted**
    ![](https://www.baeldung.com/wp-content/uploads/sites/4/2022/12/Inverted-pagetable.drawio-2.png)
- **Hashed**    
    ![](https://i.ibb.co/G3N8cyz/Hashed-Page-Table.png)


## Segmented Paging
- Pure segmentation is not very popular and not being used in many of the operating systems.
- Segmentation can be combined with Paging to get the best features out of both the techniques.
  ![](https://images.javatpoint.com/operating-system/images/os-segmented-paging2.png)

---
---


# File System

**File**: A file is a named collection of related information that is recorded on secondary storage.

**File Attributes**: Name, Extension, Size, Date, Author, Created, Modified, Accessed etc

### File System
Module of OS which manages, controls and organizes files and related structures

**Types of File Systems**
- FAT32 → windows
- NTFS → windows
- HFS+ → MAC
- Ext2/Ext3/Ext4 → Linux
- Swap → used for swap in & swap out

### File Directory Structure
![](https://i.ibb.co/HNWk47t/Directory-Types.png)

## Disk Partiotioning
- **Low Level(Physical)** - Tracks and sectors
- **High Level(Logical)** - Blocks
    - **Primary** - Used to store OS and User files
    - **Extended** - Used to store User files only

### Free space Management
- Free List - Linked List of free blocks
- Bitmap Methos - make an hash array of 0/1 to store if the block is free or not

## File Allocation Methods 
- ### **Contiguous Allocation**
    |File Name|Start Block Number|Number Of Blocks|
    |---------|------------------|----------------|
    |...|...|...|
    |...|...|...|
- ### **Linked Allocation**
    |File Name|Start Block Number|Last Block Number|
    |---------|------------------|-----------------|
    |...|...|...|
    |...|...|...|

- ### **Indexed Allocation**
    |File Name|Index Block Number|
    |---------|------------------|
    |...|...|
    |...|...| 
    - **Single Level Indexed Allocation**
    - **Two Level Indexed Allocation**

### Master Boot Record
A master boot record (MBR) is a special type of boot sector at the very beginning of partitioned computer mass storage devices.
- Contains the information regarding how and where the OS is located in the hard disk so that it can be booted in the RAM.

## Disk Scheduling
- Done by operating systems to schedule I/O requests arriving for the disk
- using this we will try to Save seek limp

### Disk Scheduling Algorithms
![](https://i.ibb.co/D8LWrWk/example.png)

- **FCFS (First Come First Serve)**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/20200608201201/fcfs3.jpg)
  
- **SSTF (Shortest Seek Time First)**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/20200608201702/sstf1.jpg)
  
- **Scan**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/20200608202008/scan4.jpg)
  
- **C-Scan (Circular-Scan)**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/20200608202230/cscan1.jpg)
  
- **Look**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/20200608202613/look1.jpg)
  
- **C-Look (Circular-Look)**

  ![](https://media.geeksforgeeks.org/wp-content/uploads/20200608202846/clook1.jpg)
