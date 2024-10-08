### Detailed Lecture Notes: Pre-emptive and Non Pre-emptive Scheduling

---

### 1. **Introduction**
   - This lecture focuses on understanding **Pre-emptive** and **Non-Pre-emptive** scheduling—two different methods for managing CPU scheduling.
   - It’s important to note that **pre-emptive and non-pre-emptive scheduling** are not specific CPU scheduling algorithms; instead, they are approaches used by CPU scheduling algorithms.
   - The lecture aims to provide a comprehensive understanding of these two approaches.

### 2. **Key Concepts Before Diving Into Scheduling**
   - **CPU Scheduler**:
     - When the CPU is idle, the operating system selects one process from the **ready queue** to execute. 
     - The CPU scheduler, specifically the **short-term scheduler**, performs this selection.
     - The scheduler picks a process from the **ready state** and allocates the CPU for its execution.
     - This process is crucial as it determines which process will get the CPU next.
     - The scheduler essentially manages CPU resources by ensuring multiple processes are assigned CPU time.

   - **Dispatcher**:
     - The dispatcher is a module that hands over CPU control to the process selected by the short-term scheduler.
     - When a process is selected, the dispatcher quickly transfers CPU control to it.
     - Quick execution is essential for the dispatcher because frequent process switches occur in multitasking systems.
     - The time it takes for the dispatcher to stop one process and start another is called **dispatch latency**.
     - Minimal dispatch latency is critical for efficient computation and CPU utilization.

### 3. **Understanding Pre-emptive and Non-Pre-emptive Scheduling**
   - **CPU Scheduling Decisions** may occur under the following four circumstances:
     1. When a process switches from the **running state** to the **waiting state**.
     2. When a process switches from the **running state** to the **ready state** (e.g., due to an interrupt).
     3. When a process switches from the **waiting state** to the **ready state** (e.g., upon completion of an I/O request).
     4. When a process **terminates**.

   - Detailed Explanation of Circumstances:
     - **Running State**: The process currently holding the CPU and undergoing execution.
     - **Waiting State**: When a process is waiting for I/O operations to complete and is not using the CPU.
     - **Ready State**: When a process is ready to use the CPU but is waiting for its turn in the queue.

### 4. **Analysis of the Four Circumstances**
   - **Situation 1: Running to Waiting State**
     - When a process switches from running to waiting (e.g., waiting for an I/O operation), the CPU becomes available for another process.
     - A scheduling decision must be made to assign the CPU to another process in this scenario.

   - **Situation 2: Running to Ready State (Interrupt)**
     - The process is using the CPU but must halt due to an interrupt (e.g., a hardware interrupt).
     - The process transitions to the ready state, waiting for CPU availability again.
     - A decision must be made: should the CPU return to this process or be assigned to another process?

   - **Situation 3: Waiting to Ready State (Completion of I/O)**
     - After completing an I/O request, a process moves from the waiting state to the ready state.
     - A scheduling decision occurs: should this process be given the CPU next, or should it go to another process in the ready queue?

   - **Situation 4: Process Termination**
     - When a process terminates, the CPU is available for the next process in the queue. The scheduler must decide which process should be executed next.

### 5. **Understanding Pre-emptive Scheduling**
   - In **pre-emptive scheduling**, CPU control can be taken from a process even before it completes its execution or moves to the waiting state.
   - Examples:
     - When an interrupt occurs (situation 2), the system may decide to switch the CPU to another process with higher priority.
     - In situation 3, after a process completes an I/O request, the scheduler may choose to give the CPU to another process rather than resuming the interrupted one.
   - Pre-emptive scheduling is crucial for prioritizing high-priority tasks, but it can also lead to potential issues, such as reading inconsistent data from shared memory if processes are interrupted.

### 6. **Understanding Non-Pre-emptive (Cooperative) Scheduling**
   - In **non-pre-emptive scheduling**, the CPU is only reassigned when the current process:
     - Completes its execution.
     - Moves to the waiting state (situations 1 and 4).
   - The CPU remains with the process until one of these conditions occurs.
   - This approach ensures a process is not interrupted during its execution unless it voluntarily moves to a waiting state or completes.

### 7. **Comparison: Pre-emptive vs. Non-Pre-emptive Scheduling**
   - Both scheduling methods serve specific purposes and are required in different situations:
     - **Pre-emptive Scheduling**:
       - Necessary for responding to high-priority tasks promptly.
       - Useful when a process with a higher priority needs the CPU, even if it means interrupting a lower-priority process.
     - **Non-Pre-emptive Scheduling**:
       - Suitable when ensuring a process completes uninterrupted unless it voluntarily waits.
       - Reduces the complexity of managing shared resources like memory since a process is not pre-empted midway.
   - Trade-offs:
     - **Pre-emptive scheduling** may cause complications, such as inconsistencies when dealing with shared memory if a writing process is interrupted.
     - **Non-pre-emptive scheduling** provides stability but may delay high-priority tasks.

### 8. **Conclusion**
   - Both **pre-emptive** and **non-pre-emptive** scheduling have their place depending on the operating system and the specific scenarios.
   - Pre-emptive scheduling offers flexibility and responsiveness but at the cost of potential complexity.
   - Non-pre-emptive scheduling is straightforward and ensures stability but may not always be efficient for high-priority tasks.
   - Understanding these concepts is fundamental for studying CPU scheduling algorithms and related subjects in operating systems.
