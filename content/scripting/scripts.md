+++
title = "Scripts"
author = ["Nick OBrien"]
draft = false
weight = 1003
+++

## Script Structure {#script-structure}

A Julia script is simply a file with Julia code. When you run a script, the result is similar to running each line of code in the REPL from top to bottom. For example, consider the following script:

```julia
x = 2 + 2
y = 5x - 3
x * y
```

Running this script would be similar to the following REPL commands:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x = 2 + 2
4

<font color="#98C379"><b>julia&gt; </b></font>y = 5x - 3
17

<font color="#98C379"><b>julia&gt; </b></font>x * y
68
</pre>

However, the results of each expression are not shown automatically like in the REPL.


## First Script {#first-script}

Often the first program people learn to write is the ["Hello, World!"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) program. All it does is print `Hello, World!` to the screen. Open a file named `hello.jl` and write the following line of code:

```julia
println("Hello, World!")
```

There are a few ways to actually run this script now. First, open a terminal in the same directory as `hello.jl`. Then, type `julia hello.jl` and press enter. You should see the following output:

```txt
$ julia hello.jl
Hello, World!
```

You can execute a script from inside the REPL as well. Open the REPL with the `julia` command and type `include("hello.jl")`:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>include(&quot;hello.jl&quot;)
Hello, World!
</pre>

The `include` function executes a Julia file's contents as if they were typed in the REPL.
