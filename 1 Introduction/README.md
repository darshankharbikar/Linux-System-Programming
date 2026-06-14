# Linux
-------
1. Linux is a very secured OS compared to other OS like Windows
2. Linux is Open source, hence it is low cost maintainence OS.
3. Linux is highly stable, and it is very less prone to system crashes.
4. Linux runs on most modern Processor(hardware)
5. Linux systems provides a ease of customisation their product development.
6. Linux has a wide community of developers Globally, hence the support we get for 
   Linux is very good when compared to any other OS.
7. The Linux systems are used in wide variety of applications like
   Super computers, Smart watches, smart TV, Set-Top-Box, Servers, Infotainment industry, Smart Cars,
   IoT devices, Routers, Railway Signalling and many more. 

- Did you know - NASA also uses Linux in their Space station for better reliability.

# Linux Systems Programming
- This repository covers Linux Systems Programming from beginner to advanced level with extensive hands-on C programming examples and practical demonstrations.

---

## 1. Linux Programming Fundamentals

### Topics Covered

- Introduction to Linux System Programming
- Difference between System Calls and Library Functions
- GNU GCC Compilation Process
- File Operations
- Blocking vs Non-Blocking Calls
- Atomic Operations
- Race Conditions
- User Mode vs Kernel Mode

### Practical Examples

- File creation, reading, writing, and deletion
- Using `open()`, `read()`, `write()`, `close()`
- Understanding system call flow
- Building applications using GCC

---

## 2. Process Management

### Topics Covered

- Process Fundamentals
- Process Creation and Termination
- Parent and Child Processes
- `fork()` System Call
- Command-Line Arguments
- Process Memory Layout

### Practical Examples

- Creating child processes using `fork()`
- Process hierarchy
- Process IDs (PID and PPID)
- Process lifecycle management

### Key Concepts

```text
Process
├── Code Segment (.text)
├── Data Segment
├── Heap
└── Stack
```

---

## 3. Signals

### Topics Covered

- Linux Signals
- Signal Handlers
- Default Signal Actions
- Sending Signals Between Processes

### Practical Examples

- Handling `SIGINT`
- Handling `SIGTERM`
- Using `kill()`
- Custom signal handlers using `signal()` and `sigaction()`

### Common Signals

| Signal | Description |
|----------|------------|
| SIGINT | Interrupt (Ctrl+C) |
| SIGTERM | Termination Request |
| SIGKILL | Force Kill |
| SIGSEGV | Segmentation Fault |
| SIGALRM | Alarm Signal |

---

## 4. Memory Management

### Topics Covered

- Virtual Memory Concepts
- Process Address Space
- Memory Segments
- Dynamic Memory Allocation

### Memory Layout

```text
+------------------+
| Stack            |
+------------------+
|                  |
|                  |
|                  |
+------------------+
| Heap             |
+------------------+
| BSS              |
+------------------+
| Data Segment     |
+------------------+
| Code Segment     |
+------------------+
```

### Practical Examples

- Using `malloc()`
- Using `calloc()`
- Using `realloc()`
- Memory leak detection

---

## 5. POSIX Threads

### Topics Covered

- Multithreading Fundamentals
- Thread Creation
- Thread Termination
- Thread IDs
- Joinable Threads
- Detachable Threads

### Practical Examples

- Creating threads using `pthread_create()`
- Thread synchronization basics
- Thread lifecycle management

### Common APIs

```c
pthread_create()
pthread_join()
pthread_exit()
pthread_detach()
pthread_self()
```

---

## 6. Thread Synchronization

### Topics Covered

- Critical Sections
- Race Conditions
- Mutexes
- Condition Variables

### Practical Examples

- Producer-Consumer Problem
- Shared Resource Protection
- Thread-safe Programming

### Common APIs

```c
pthread_mutex_init()
pthread_mutex_lock()
pthread_mutex_unlock()

pthread_cond_wait()
pthread_cond_signal()
pthread_cond_broadcast()
```

---

## 7. Inter Process Communication (IPC)

### Topics Covered

- Pipes
- FIFO (Named Pipes)
- POSIX Message Queues
- POSIX Semaphores
- POSIX Shared Memory

### IPC Mechanisms Overview

| IPC Mechanism | Communication Type |
|--------------|-------------------|
| Pipe | Parent ↔ Child |
| FIFO | Unrelated Processes |
| POSIX Message Queue | Message-Based |
| POSIX Semaphore | Synchronization |
| POSIX Shared Memory | Fastest Data Sharing |

### Practical Examples

#### Pipe

```c
pipe()
read()
write()
```

#### FIFO

```c
mkfifo()
open()
```

#### POSIX Message Queue

```c
mq_open()
mq_send()
mq_receive()
mq_close()
```

#### POSIX Semaphore

```c
sem_open()
sem_wait()
sem_post()
```

#### POSIX Shared Memory

```c
shm_open()
mmap()
munmap()
```

---

## Skills Acquired

After completing this course, you will be able to:

- Develop Linux system-level applications in C
- Understand Linux process and memory management
- Create and manage POSIX threads
- Implement thread synchronization mechanisms
- Handle Linux signals effectively
- Use IPC mechanisms for process communication
- Debug race conditions and synchronization issues
- Write efficient and robust Linux applications

---

## Recommended Prerequisites

- Basic C Programming
- Linux Command Line Basics
- Understanding of Operating System Fundamentals

---

## Recommended Progression

```text
C Programming
      ↓
Linux Basics
      ↓
System Calls
      ↓
Process Management
      ↓
Signals
      ↓
Memory Management
      ↓
POSIX Threads
      ↓
Thread Synchronization
      ↓
IPC Mechanisms
      ↓
Advanced Linux System Programming
```


