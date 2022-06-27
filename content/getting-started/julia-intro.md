+++
title = "Julia Intro"
author = ["Nick OBrien"]
draft = false
weight = 1003
+++

## Programming {#programming}

Computers only understand ones and zeros. When a computer runs a program, it's really reading something like this:

```text
01111111 01000101 01001100 01000110
00000010 00000001 00000001 00000000
00000000 00000000 00000000 00000000
00000000 00000000 00000000 00000000
```

Computers understand this just fine. Humans, on the other hand, have a difficult time writing and understanding instructions like these.

In order to make writing this easier, _programming languages_ were invented. Humans write code in a programming language, and that code is translated into ones and zeros that the computer can run.

Some programming languages involve giving bare-bones commands to the computer. Text written in these languages usually gets translated to a similar amount of ones and zeros. These are generally called _low level langauges_. The opposite of low level languages are _high level langauges_, where one simple command can translate to tons of ones and zeros.

Low level languages are useful for pushing a computer to its limits, but they are generally harder to write. High level languages allow humans to quickly write and understand code without having to worry about the low level details. Using a high level language is like ordering food at a restaurant whereas a low level language is like cooking a dish from scratch.

Consider a program that simply prints "Hello World" to the screen. Here is what that program would look like in various languages, roughly from low to high level.


### x86-64 Assembly (Linux) {#x86-64-assembly--linux}

```asm
global _start

section .text

_start:
  mov rax, 1
  mov rdi, 1
  mov rsi, msg
  mov rdx, msglen
  syscall

  mov rax, 60
  mov rdi, 0
  syscall

section .rodata
  msg: db "Hello, World!", 10
  msglen: equ $ - msg
```


### C {#c}

```c
#include <stdio.h>

int main(void) {
    printf("Hello, World!\n");
    return 0;
}
```


### Java {#java}

```java
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```


### Julia {#julia}

```julia
println("Hello, World!")
```


### Python {#python}

```python
print("Hello, World!")
```


### Lisp {#lisp}

```lisp
(print "Hello, World!")
```


## The Julia Language {#the-julia-language}

Julia is a relatively new programming language. Version 1.0 was released in August of 2018. It was designed with computational scientists in mind, but it is a general purpose language too.

Like most other languages, Julia code is executed from the top down. For example, the following code prints "ready", "set", and "go" in that order.

```julia
println("ready")
println("set")
println("go")
```
