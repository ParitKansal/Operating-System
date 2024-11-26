# Operating System
---
---
# **Introduction**

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
