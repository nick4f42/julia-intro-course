+++
title = "REPL Intro"
author = ["Nick OBrien"]
draft = false
weight = 1004
+++

When you type `julia` in the command line, you should get an output like this:

<pre class="julia-repl"><font color="#C678DD">$</font> <font color="#98C379">julia</font>
               <font color="#98C379"><b>_</b></font>
   <font color="#61AFEF"><b>_</b></font>       _ <font color="#E06C75"><b>_</b></font><font color="#98C379"><b>(_)</b></font><font color="#C678DD"><b>_</b></font>     |  Documentation: https://docs.julialang.org
  <font color="#61AFEF"><b>(_)</b></font>     | <font color="#E06C75"><b>(_)</b></font> <font color="#C678DD"><b>(_)</b></font>    |
   _ _   _| |_  __ _   |  Type &quot;?&quot; for help, &quot;]?&quot; for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.7.3 (2022-05-06)
 _/ |\__&apos;_|_|_|\__&apos;_|  |  Official https://julialang.org/ release
|__/                   |

<font color="#98C379"><b>julia&gt; </b></font>
</pre>

This is called the Julia REPL (short for read-eval-print-loop). The REPL allows you to write code interactively instead of saving it in a file. In its most basic form, the REPL acts like a calculator. Type an expression like `2 + 2` and press enter. You should see the result on the next line:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>2 + 2
4

<font color="#98C379"><b>julia&gt; </b></font>7 * 8
56
</pre>

To exit the REPL, press `CTRL-d` or type `exit()` and press enter.
