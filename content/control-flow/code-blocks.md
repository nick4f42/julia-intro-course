+++
title = "Code Blocks"
author = ["Nick OBrien"]
draft = false
weight = 1003
+++

A code block in Julia is used to group code together. They usually start with a keyword and end with the word `end`. The most basic block is the `begin` block.


## Begin Block {#begin-block}

All the begin block does is group code together into a single expression. The last expression in the block is the blocks value. A begin block might look like this:

```julia
begin
    x = 2
    y = 1
    x + y
end
```

Typing this in the REPL, you will see that the value of the last expression `x + y` is outputted.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>begin
       x = 2
       y = 1
       x + y
       end
3
</pre>

Everything from `begin` to `end` is replaced with the value of the last expression. For example, you can assign the value to a variable:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>y = begin
           x = 2 + 2
           x * 5
       end
20

<font color="#98C379"><b>julia&gt; </b></font>y
20
</pre>

You will also notice that the variables defined in the block are also accessible outside.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x
4
</pre>

`begin` blocks are useful for running multiple lines of code in one REPL prompt. They are also when working with macros, which you will learn about in a later section.


## Function Block {#function-block}

You've already seen function blocks, but they are left here for completeness. They look like:

```julia
function name_of_function(args)
    # code
end
```

A function block is actually equivalent to an assignment-style function with a `begin` block:

```julia
name_of_function(args) = begin
    # code
end
```

It's usually better to just use a `function` block so it's clear you're defining a function.


## Let Block {#let-block}

A `let` block creates a new _local scope_ with the specified local variables.

```julia
# x doesn't exist here

let x = 1
    # x is 1
    println(x)
end

# x doesn't exist here
```

You can specify multiple variables in the let block header by separating the assignments with commas.

```julia
let x = 1, y = 2
    println(x + y)
end
```

Variables in the let block header replace outside variables for the duration of the block:

```julia
x = 5
# x is 5
# y doesn't exist here

let x = 1, y = 2
    # x is 1
    # y is 2
    println(x + y)
end

# x is 5
# y doesn't exist here
```


## Other Blocks {#other-blocks}

Conditional blocks like `if`, `else`, and `elseif` can choose code to run based on a `true=/=false` condition. They will be covered in the next section.

`while` and `for` loops can run the same code multiple times. They will be covered after conditional blocks.

There are also blocks like `do`, `quote`, and `macro`.
