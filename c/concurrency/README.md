# Concurrency

\
Concurrency is the ability of a system to execute multiple tasks or processes simultaneously. These tasks may be independent or interrelated, and concurrency allows them to progress concurrently, potentially overlapping in time.

**Parallelism vs. Concurrency**: Not the same. Parallelism involves executing multiple tasks simultaneously using multiple processing units, while concurrency involves managing multiple tasks that may start, run, and complete in overlapping time periods, potentially on a single processing unit.

### Threads and Processes

Tasks are typically implemented as threads or processes. Threads are lightweight sequences of instructions within a process, sharing the same memory space, while processes are independent instances of a program, each with its own memory space.

* **Thread**: A thread is the smallest unit of execution within a process. Threads share the same memory space and resources allocated to the process. Each thread within a process has its own stack but shares the process's memory space, file descriptors, and other resources. Threads within the same process can communicate and share data more efficiently compared to processes, as they do not need to use inter-process communication mechanisms.
* **Process**: A process is an instance of a running program. It includes the program code, its data, and resources (like memory, open files, and network connections) allocated to it during execution. Each process has its own address space, which means processes are isolated from one another and cannot directly access each other's memory.
* **Thread Pool**: A thread pool manages a group of worker threads, reusing them to execute tasks from a task queue. This pattern reduces the overhead of creating and destroying threads for each task, improving performance and resource utilization.

