+++
title = "Scripting Workflow"
author = ["Nick OBrien"]
draft = false
weight = 1005
+++

The following steps are often useful for working on code:

1.  Write some code
2.  Test the code interactively
3.  Repeat


## Script + REPL {#script-plus-repl}

For example, say you're working on some code in a file named `work.jl`

```julia
# work.jl

function foo(a, b, c)
    # lots of code
end

function bar(x, y)
    # lots of code
end
```

Now, you can start up a REPL and `include` the `work.jl` file.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>include("work.jl")
</pre>

You can now test the `foo` and `bar` functions in the REPL.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>foo(1, 2, 3)

<font color="#98C379"><b>julia&gt; </b></font>bar(64, 128)

</pre>


## Jupyter Notebook {#jupyter-notebook}

Since a text editor is integrated into a jupyter notebook, you can skip the `include` step and write your code directly into a cell. Note that you cannot include jupyter notebooks from other files. If you want to use your code elsewhere, you'll have to put it in a Julia file.
