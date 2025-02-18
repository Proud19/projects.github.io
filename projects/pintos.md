# PintosOS Project Report

## Overview

The **PintosOS** project is an implementation of an operating system (OS) framework for the **10x86 architecture**, developed as part of my coursework in operating systems. The project aimed to simulate the core components of an OS, including process management, kernel threads, and basic file system functionality. The goal was to provide a hands-on learning experience in OS design and implementation, focusing on understanding the interactions between software and hardware.

The project was structured in stages, with increasing complexity, ultimately resulting in a functioning OS capable of running simple user programs, managing processes, and performing I/O operations. This README serves as a detailed overview of the design, implementation, and key features of the PintosOS.

## Project Objectives

The main objectives of the PintosOS project were:
- Implement basic **process management**, including thread creation, execution, and scheduling.
- Develop a simple **kernel** that can execute user programs.
- Create a **file system** to manage files and directories.
- Gain a deep understanding of how operating systems handle concurrency, synchronization, and memory management.

## Key Features Implemented

### 1. **Thread Management**
One of the core features of PintosOS was implementing thread management, which involved creating a basic threading model to allow concurrent execution of multiple programs. The key tasks involved:
- **Thread creation and scheduling**: Implemented `thread_create()` and a basic round-robin scheduler to manage the execution of threads.
- **Thread synchronization**: Used semaphores and locks to prevent race conditions and ensure proper synchronization across threads.
- **Thread lifecycle**: Handled the thread lifecycle, including thread termination and joining.

### 2. **User Program Execution**
PintosOS was designed to load and execute user programs. This required implementing a system to load executable binaries into memory and run them in a user process context. Key components:
- **System calls**: Implemented basic system calls, including `exit()`, `write()`, and `wait()`, to interact with the OS and perform basic operations.
- **Memory management**: Utilized virtual memory and implemented a simple **user process memory model** to handle the loading and execution of programs without interfering with other processes.

### 3. **File System**
The file system component of PintosOS involved creating a simple file system to manage files and directories. Key features included:
- **File operations**: Implemented basic file system operations like `create()`, `open()`, `read()`, `write()`, and `close()`.
- **Directory structure**: Allowed users to create and manage directories as part of the file system.
- **Persistent storage**: Implemented the storage backend to ensure data persistence between program executions.

### 4. **Synchronization and Concurrency**
Concurrency and synchronization were essential for ensuring correct execution of multiple threads. We implemented mechanisms such as:
- **Locks**: Used locks to prevent race conditions when accessing shared resources.
- **Semaphores**: Utilized semaphores to coordinate the execution of threads.
- **Condition variables**: Implemented condition variables to manage thread wait/wake functionality.

### 5. **Interrupt Handling**
PintosOS also included basic interrupt handling to allow interaction with external devices, such as handling timer interrupts and managing process scheduling during these interrupts.

## System Architecture

The system was designed around a **monolithic kernel**, where all essential OS functionalities (e.g., scheduling, memory management, file system) were implemented in a single kernel space. Key components included:

- **Kernel Threads**: Managed by the OS to ensure execution of user-level programs.
- **User Processes**: Executed in user mode and managed by the kernel.
- **File System**: The implementation allowed interaction with files stored on disk.
- **Interrupts and Scheduling**: The kernel handled interrupts and performed process scheduling to ensure fair execution.

## Code Highlights

### 1. **Thread Creation and Scheduling**

```c
void thread_create (const char *name, int priority) {
    struct thread *t = malloc(sizeof(struct thread));
    t->name = name;
    t->priority = priority;
    thread_enqueue(t); // Adds the thread to the ready queue
}
```


### 2. **File System Operations**
```c
bool filesys_create (const char *name, off_t initial_size) {
    struct file *f = open_file(name);
    if (f == NULL) {
        return false; // File creation failed
    }
    return true; // File created successfully
}
```

### 3. **Thread Synchronization**
```c
void lock_acquire (struct lock *lock) {
    while (lock->holder != NULL) {
        thread_sleep(lock); // Block the current thread
    }
    lock->holder = current_thread;
}
```

## Challenges Faced
Thread Synchronization: One of the primary challenges was ensuring that multiple threads could safely interact with shared resources without causing data corruption or race conditions.
System Call Handling: Implementing system calls required a deep understanding of how user-level programs interact with kernel-level functionality, which was more complex than anticipated.
Memory Management: Managing memory for both user and kernel spaces required careful consideration to avoid memory leaks and corruption.
Conclusion
The PintosOS project was an excellent exercise in understanding the core principles of operating systems. By implementing fundamental features such as thread management, user program execution, and file system operations, I gained a solid understanding of how operating systems function at a low level. The project also provided insight into the challenges faced by operating system developers, such as synchronization, memory management, and resource allocation.

## Future Improvements
Multithreading: Add support for more advanced thread synchronization primitives like barriers and condition variables.
Virtual Memory: Implement a more robust virtual memory system that supports paging and segmentation.
Advanced Scheduling: Integrate more complex scheduling algorithms such as priority-based scheduling or multi-level feedback queues.
References

## References 
- [Pintos Project](https://www.scs.stanford.edu/24wi-cs212/labs/project.html)


