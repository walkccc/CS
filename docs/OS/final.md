# Previous Operating System Midterms at NTUCSIE

## [Spring 2011](https://www.ptt.cc/bbs/NTU-Exam/M.1340817215.A.742.html)

The exam is 150 minutes long. The total score is 112pts. Please read the questions carefully.

1. Terminologies (21pts).

    - Condition Variable (Hint: Monitor)

    - Stable Storage

    - 50-Percent Rule for the First-Fit Algorithm (Hint: Dynamic Partitioning)

    - Virtual Memory

    - Lazy Swapper

    - Network Information Service (NIS or Yellow Pages from SUN)

    - Scan (or Elevator) Algorithm (Hint: Disk Scheduling)


2. Please answer the following question on process synchronization: (18pts)

    - Synchronization hardware might make programming easier for process synchronization. Please explain why interrupt disabling works for uniprocessor environments to avoid the race condition. (6pts)

    - There are three requirements for a solution to critical section problem. Please tell me which requirement might not be satisfied for solutions based on semaphores with priority-waiting queues. You must provide your arguments. (6pts)

    - When the Two-Phase Locking protocol (2PL) is adopted for process synchronization, and there is only exclusive lock, can we have a deadlock? You must provide your arguments. (6pts)


3. Given the following snapshot of the system: Please determine whether there exists a safe sequence. (5pts)

4. With binding at the compiling time, is it appropriate to have Paging? With binding at the loading time, is it appropriate to have Paging? You must provide explanation. (6pts)

5. Given a computer system with 64-bit virtual address and 8 bytes per page entry, let the physical address be of 48 bits, and the system is byte-addressable. Assume that every page is of 4KB. Please answer the following questions: (20pts).

    - What is the maximum number of frames? (5pts)

    - Suppose that we have multi-level paging. How many levels do we have in multi-level paging? (5pts)

    - Suppose that TLB is adopted for paging, and multi-level page tables are all in the main memory. Let the memory access time and TLB access time be 100ns and 10ns, respectively. What the TLB hit ratio should be so that the effective memory access time would be no more than 120ns? (5pts)

    - Continued with the previous question, What is the maximum number of entries for an inverted page table? (5pts)

6. Please answer the following questions for demand paging: (20pts)

    - What is the maximum number of pages needed for the following instruction: Add (R1)+, -(R2), +(R3)  (4pts)

    - The effective access time is defined as (1 - p) * ma + p * pft, where p, ma, and pft are the probability of a page fault, the memory access time for paging, and the page fault time, respectively. Please give me two approaches to reduce the pft. Please give me two approaches to reduce p. (16pts)

7. Given the following reference string, which reference causes a page fault under the Second Chance (Clock) Algorithm. Please also show us which page is replaced when a page replacement occurs? Suppose that we have 3 available frames with 0, 1, and 3 as shown in the following graph, all reference bits are 0, and the selection pointer starts at Page 0. (10pts)

    $$1 \, 0 \, 3 \, 1 \, 4 \, 3 \, 2 \, 1 \, 3 \, 0 \, 2 \, 1 \, 5$$

8. Modern operating system often only recognize few file types. Please give two advantages why file types are usually supported by applications, instead of the operating system. (8pts)

9. Give me one reason when we need scheduling in I/O subsystem, beside performance improvement. (4pts)

## [Spring 2012](https://www.ptt.cc/bbs/NTU-Exam/M.1418545643.A.933.html)

1. Terminologies. (24pts)

    - **Deadlock**

        <span style="color:red">A set of process is in a deadlock state when every process in the set is waiting for an event that can be caused by only another process in the set.

    - **Segmentation**

        <span style="color:red">Segmentation is a memory management scheme that supports the user view of memory.

    - **Working Set** (Hint: Thrashing and Frame Allocation)
        
        <span style="color:red">The working set is an approximation of a program's locality.

    - **Optimal Algorithm for Page Replacement (OPT)**
        
        <span style="color:red">Replace the page that will not be used for the longest period of time.

    - **Hard Link** (Hint: Acyclic-Graph Directory)

        <span style="color:red">A hard link of a file name let its directory entry point to the i-node that describes the file's contents.

    - **Network-Attached Storage (NAS)**

        <span style="color:red">Clients access NAS via a remote procedure call interface such as NFS (for UNIX) or CIFS (for Windows) where NAS has a file system running on it.

    - **Raw Disk**
        
        <span style="color:red">Ans: A partition as a large sequential array of logical blocks.

    2. Please provide one advantage and one disadvantage of a deadlock avoidance algorithm (such as the Banker's Algorithm), compared to a deadlock
   prevention algorithm (such as the one without "Hold-and-Wait"). (6pts)

        - <span style="color:red">Advantage: Better resource utilization and/or better system throughput/performance.
        - <span style="color:red">Dsadvantage: Processes must claim maximum usages of each resource.

## [Spring 2013](https://www.ptt.cc/bbs/NTU-Exam/M.1403667958.A.FA7.html)

## [Spring 2014](https://www.ptt.cc/bbs/NTU-Exam/M.1437210714.A.B8A.html)

## [Spring 2015](https://www.ptt.cc/bbs/NTU-Exam/M.1472670507.A.427.html)