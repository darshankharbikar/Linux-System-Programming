# Library Functions and System Calls
------------------------------------ 
- All programs explained in this course are written in C.
- Ubuntu PC is used to run the C programs. Any Linux distribution can be used.
- GCC compiler is used to compile the code.

## 1. Linux Library Functions
- Linux library functions are provided through the C Standard Library.
- The C Standard Library is also called libc.
- The C Standard Library provides header files that must be included in the user application program to use standard library function calls.
- Example:
```c
#include <stdio.h>
```
- `stdio.h` provides standard input/output library functions such as:
```c
printf();
scanf();
fgets();
fputs();
```
---
## 2. What is a Library Function?
- A library is a collection of pre-compiled code.
- A library contains multiple functions grouped together as a package. It helps reuse code and avoids writing the same logic repeatedly.
- Example:
- The standard C library provides the `stdio.h` header file.
- This header file must be included in the user program to use the library function `printf()`.
- Some library functions are implemented over system calls to provide additional functionality and abstraction.

## 3. Library Function Interface
![Library Function Interface](library_function_interface.png)
Flow
```text
Application Software
        ↓
C Standard Library
        ↓
System Calls
        ↓
Hardware
```
- Application software usually does not directly interact with hardware.
- It calls library functions.
- Library functions may internally call system calls when kernel service is required.
- System calls allow controlled access to hardware through the kernel.

## 4. Demo Program: Library Function
- File: `lib_ex.c`
```c
/* Sample program to use the standard library   */
/* stdio.h is the standard Input/output header file*/
```
#include <stdio.h>

void main(){

    printf("\n This is a demo to show how to call library function\n");
}
```
- `stdio.h` is the standard input/output header file.
- `printf()` is a C Standard Library function.
- The program prints a message on the terminal.
- The user code calls `printf()` directly.
- Internally, `printf()` may use the `write()` system call to send output to the terminal.

## 5. Compiling C Code Using GCC
- The open-source compiler used to compile the code is GCC.
- The terminal is used to compile the code.
- General Syntax
```bash
gcc source_file.c -o output_file
```
- Example: If the source code file is `lib_ex.c` and the required output executable is `lib_ex`, use:
 
```
gcc lib_ex.c -o lib_ex
```
- Running the Program
``` 
./lib_ex
```
Note on `-o`
- `-o` is used to specify the output executable name.
- Without `-o`, GCC creates the default executable named `a.out`.
- For GCC manual details:
``` 
man gcc
```
 
## 6. System Calls
- A system call is an interface through which user application code enters kernel mode.
- During system call execution, the CPU switches from user mode to kernel mode, and the kernel executes code on behalf of the user program.

## 7. Ways to Invoke System Calls
- System calls can be invoked from user application code in two ways:
### A. Directly calling the system call
- Example:
```c
write();
read();
open();
close();
```
### B. Calling a library function that internally calls a system call
Example:
```c
printf();
```
`printf()` is a library function, but internally it may call the `write()` system call when output must be written to the terminal.
 
## 8. Examples of System Calls
- Common system calls include:
```c
open();
close();
read();
write();
```
- Example Relation
``` 
printf()  →  write()
```
- Meaning:
`printf()` is a library function.
`write()` is a system call.
`printf()` may internally use `write()` to print data on the terminal.
 
## 9. Demo Program: System Call
- File: `sys_ex.c`
``` 
/* Demo to show the write() system call */

#include <stdio.h>
#include <unistd.h>
#include <string.h>

void main(){
    size_t len;
    int msg_len = 0;
    char buf[100];

    strncpy(buf,"This is writing to screen using write() system call instead of printf Library call\n",99);
    msg_len = strlen(buf);

    len = write(1, buf,msg_len);  

}
```
 
- `unistd.h` provides POSIX system call declarations such as `write()`.
- `string.h` provides string handling functions such as `strncpy()` and `strlen()`.
- `buf` stores the message to be printed.
- `strlen(buf)` calculates the message length.
- `write(1, buf, msg_len)` writes the buffer content to standard output.
- Meaning of `write()` Arguments
``` 
write(1, buf, msg_len);
```
Argument	Meaning
`1`	File descriptor for standard output / terminal
`buf`	Address of the buffer containing data
`msg_len`	Number of bytes to write
 
## 10. System Call Working
![System Call Working](system_call_working.png)

Step-by-Step Flow
- User code calls a function such as `write()`.
- The standard library wrapper prepares the system call.
- CPU enters kernel mode using a trap/software interrupt mechanism.
- Kernel trap handler starts execution.
- Kernel checks the system call number.
- Kernel uses the system call table to call the correct kernel function, such as `sys_write()`.
- Kernel performs the requested operation.
- Kernel returns the result to user mode.
- User program continues execution.
 
## 11. Library Function vs System Call
- Feature	Library Function	System Call
- Execution layer	User-space library	Kernel interface
- Example	`printf()`	`write()`
- Header example	`stdio.h`	`unistd.h`
- Mode switch	Usually no direct mode switch	Causes user mode to kernel mode transition
- Formatting support	Yes	No
- Buffering	Usually yes	No standard library buffering
- Portability	More portable	OS/POSIX specific
- Ease of use	Easier	Lower-level
- Performance overhead	May include formatting/buffering overhead	Direct kernel service request
 
## 12. `printf()` Flow
``` 
User Application
      ↓
printf()
      ↓
C Standard Library / libc
      ↓
write()
      ↓
Kernel
      ↓
Terminal / stdout
```
 
## 13. `write()` Flow
``` 
User Application
      ↓
write()
      ↓
System Call Interface
      ↓
Kernel
      ↓
Terminal / stdout
```
 
## 14. Important Headers
- Header File	Purpose
`stdio.h`	Standard input/output library functions such as `printf()`
`unistd.h`	POSIX API and system call wrappers such as `write()`
`string.h`	String handling functions such as `strlen()` and `strncpy()`
 
## 15. Important Terms
- User Mode: A restricted CPU mode where normal application programs run. User applications cannot directly access hardware or kernel memory.
- Kernel Mode: A privileged CPU mode where the operating system kernel runs. Kernel code can access hardware and protected system resources.
- libc / glibc
`libc` means C standard library.
`glibc` is the GNU implementation of the C library commonly used on Linux systems.
- System Call Table
A kernel table that maps system call numbers to kernel functions.
Example:
``` 
system call number for write → sys_write()
```
Trap Handler
Kernel code that handles the transition from user mode to kernel mode when a system call is made.
 
## 16. Key Takeaways
- A library function is part of a user-space library.
- A system call is the official entry point from user space into the kernel.
`printf()` is a library function.
`write()` is a system call.
- Library functions provide abstraction, formatting, and ease of use.
- System calls provide direct access to kernel services.
- Many library functions internally depend on system calls.
