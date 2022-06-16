## week 1

### GCC
```
The GNU Project was started in 1984 to create a complete Unix-like operating system as free software, in order to promote freedom and cooperation among computer 
users and programmers. Every Unix-like operating system needs a C compiler, and as there were no free compilers in existence at that time, the GNU Project had to 
develop one from scratch.

First of all, GCC is a portable compiler--it runs on most platforms available today, and can produce output for many types of processors. In addition to the 
processors used in personal computers, it also supports microcontrollers, DSPs and 64-bit CPUs.

GCC has multiple language frontends, for parsing different languages. Programs in each language can be compiled, or cross-compiled, for any architecture. 
For example, an ADA program can be compiled for a microcontroller, or a C program for a supercomputer.

```

### Compiling a simple program using GCC
The classic example program for the C language is Hello World. Here is the source code for our version of the program:
```
#include <stdio.h>

int
main (void)
{
  printf ("Hello, world!\n");
  return 0;
}
```
```
$ gcc -Wall hello.c -o hello
```
This compiles the source code in 'hello.c' to machine code and stores it in an executable file 'hello'. The output file for the machine code is specified using the -o option. 
This option is usually given as the last argument on the command line. If it is omitted, the output is written to a default file called 'a.out'.



To run the program, type the path name of the executable like this:

```
$ ./hello
Hello, world!
```
This loads the executable file into memory and causes the CPU to begin executing the instructions contained within it. The path ./ refers to the current directory,
so ./hello loads and runs the executable file 'hello' located in the current directory.


##### source
https://www.linuxtopia.org/online_books/an_introduction_to_gcc/index.html










