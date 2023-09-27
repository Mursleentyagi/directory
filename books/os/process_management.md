#Process magement

Process management is a fundamental aspect of modern operating systems that involves the creation, scheduling, execution, and termination of processes. A process is essentially a program in execution, and it is the unit of work in a computer system. Process management is crucial for efficient resource allocation and multitasking in a computer system. Here are the key components and activities involved in process management:

1. **Process Creation**:
    - When a user or application initiates a program, a new process is created.
    - The operating system allocates resources like memory, CPU time, and I/O devices to the process.

2. **Process Scheduling**:
    - The operating system manages a queue of ready-to-execute processes.
    - A scheduler decides which process to run next based on scheduling algorithms (e.g., Round Robin, Priority Scheduling).

3. **Process Execution**:
    - The selected process is loaded into the CPU and begins execution.
    - The process may move in and out of the CPU due to interrupts, I/O operations, or time-slicing (for multitasking).

4. **Process State**:
    - Processes can be in different states, including:
        - **Running**: The process is currently executing.
        - **Ready**: The process is ready to run but waiting for CPU time.
        - **Blocked**: The process is waiting for some event (e.g., I/O) to complete.
        - **Terminated**: The process has finished execution.

5. **Process Synchronization**:
    - Multiple processes often need to cooperate or communicate with each other.
    - Synchronization mechanisms like semaphores, mutexes, and condition variables are used to ensure safe concurrent access to shared resources.

6. **Process Communication**:
    - Processes may need to exchange data or information.
    - Interprocess communication (IPC) mechanisms like pipes, sockets, and message queues enable processes to communicate.

7. **Process Termination**:
    - When a process completes its execution or encounters an error, it is terminated.
    - The operating system releases the resources allocated to the process.

8. **Process Control Blocks (PCBs)**:
    - Each process is associated with a data structure known as a Process Control Block.
    - PCB stores information about the process, including its state, program counter, registers, and other relevant data.

9. **Context Switching**:
    - When the CPU switches from one process to another, a context switch occurs.
    - The CPU saves the context (state) of the currently running process and loads the context of the next process to run.

10. **Process Hierarchies**:
    - Many operating systems support the creation of parent and child processes.
    - Child processes can inherit resources and attributes from their parent.

11. **Process Prioritization**:
    - Processes may have different priorities, which can affect their scheduling and resource allocation.

12. **Process Monitoring and Debugging**:
    - Operating systems provide tools for monitoring and debugging processes, such as task managers and debugging utilities.

In summary, process management in an operating system involves the creation, scheduling, execution, and termination of processes, 
along with providing mechanisms for synchronization, communication, and resource allocation to ensure efficient and concurrent execution of multiple tasks on a computer system.

**Process**:
- A process is a program under execution.A program after it is compiled is stored on disk(secondary storage).
- A process is stored in the main memory(RAM) with resources allocated it.
- A single program could create multiple processes using fork() or spawn().
- A program is a passive entity as it is not being executed,it is sitting on the disk.While process is an 
active entity,because the process is being executed right now.
![Process](/os/img/process.png)

#Scheduling Algorithm
1. **FCFS Scheduling Algorithm**:
- The CPU scheduling algorithm First Come, First Served (FCFS), also known as First In, 
  First Out (FIFO), allocates the CPU to the processes in the order they are queued in the ready queue.
- FCFS uses non-preemptive scheduling, which means that once a CPU has been assigned to a process, 
  it stays assigned to that process until it is either not terminated or may be interrupted by an I/O interrupt.

![FCFS](/os/img/FCFS.jpg)
```
#include<stdio.h>
int main()
{
    int n,bt[30],wait_t[30],turn_ar_t[30],av_wt_t=0,avturn_ar_t=0,i,j;
    printf("Please enter the total number of processes(maximum 30):");  // the maximum process that be used to calculate is specified.
    scanf("%d",&n);
 
    printf("\nEnter The Process Burst Timen");
    for(i=0;i<n;i++)  // burst time for every process will be taken as input
    {
        printf("P[%d]:",i+1);
        scanf("%d",&bt[i]);
    }
 
    wait_t[0]=0;   
 
    for(i=1;i<n;i++)
    {
        wait_t[i]=0;
        for(j=0;j<i;j++)
            wait_t[i]+=bt[j];
    }
 
    printf("\nProcess\t\tBurst Time\tWaiting Time\tTurnaround Time");
 
    for(i=0;i<n;i++)
    {
        turn_ar_t[i]=bt[i]+wait_t[i];
        av_wt_t+=wait_t[i];
        avturn_ar_t+=turn_ar_t[i];
        printf("\nP[%d]\t\t%d\t\t\t%d\t\t\t\t%d",i+1,bt[i],wait_t[i],turn_ar_t[i]);
    }
 
    av_wt_t/=i;
    avturn_ar_t/=i;  // average calculation is done here
    printf("\nAverage Waiting Time:%d",av_wt_t);
    printf("\nAverage Turnaround Time:%d",avturn_ar_t);
 
    return 0;
}
```
