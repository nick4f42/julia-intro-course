+++
title = "Scripting Tools"
author = ["Nick OBrien"]
draft = false
weight = 1006
+++

## Comments {#comments}

You can prevent part of your code from being executed by putting it after a `#`. This is called a "comment".

```julia
# this line is ignored
x = 1 # this text is ignored
```

You can comment multiple lines by starting them with `#=` and ending them with `=#`.

```julia
x = 1 # this line will run

#=
these lines will not run:
y = 2
z = 3
=#
```

Comments are also useful for annotating. When your code gets larger and more complicated, it becomes difficult to remember what it does and how it works. Adding comments helps you remember what your code does.


## Displaying Output {#displaying-output}


### Terminal Output {#terminal-output}

When you run Julia in the terminal, results can be showed to the _standard output stream_. You can think of this stream as someone typing on a keyboard. You can instruct this figurative keyboard to type anything you want with Julia.

In the following sections, `‸` will represent the current position of the caret. For example, the result of typing "hello", the enter key, and "world" would look like:

```text
hello
world‸
```


### Printing {#printing}


#### Print Line {#print-line}

The `println` (short for _print line_) function takes any amount of arguments, prints them one by one, then advances to the next output line (like pressing enter on the keyboard).

```julia
println("hello")

x = 19
y = 5
println("The value of x is ", x)
println("x + y = ", x + y)
```

After the first `println` function runs, the terminal output will look like:

```text
hello
‸
```

Notice the cursor is on the next line. After the next two print statements the total output will be:

```text
hello123
The value of x is 19
x + y = 24
‸
```


#### Print {#print}

The `print` function does the same thing as `println` without advancing to the next output line. A simple example:

```julia
print("hello ")
print("world")
```

After the first `print` runs, the output will look like:

```text
hello ‸
```

After the next `print`, the output will be

```text
hello world‸
```

Notice that the cursor is still on the same line. If you try to print something else, it will all be on the same line:

```julia
print("hello ")
print("world")
println("what's up")
```

```text
hello worldwhat's up
‸
```

There are a couple ways to fix this issue. Firstly, you could call `println()`. Since there are no arguments, it simply advances to the next line:

```julia
print("hello ")
print("world")
println()  # advances to next line of output
println("what's up")
```

```text
hello world
what's up
‸
```

Many programming languages have special characters that mimic things like enter and tab on the keyboard. To mimic the enter key, type the two characters `\n` inside a string. The `n` stands for _new line_.

```julia
print("hello ")
print("world\n")  # add \n to mimic the enter key
println("what's up")
```

```text
hello world
what's up
‸
```
