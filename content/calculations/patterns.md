+++
title = "Patterns"
author = ["Nick OBrien"]
draft = false
weight = 1006
+++

## Assigning Variables {#assigning-variables}

Consider the following assignment:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>a = 4
4
</pre>

The `=` operator can actually do bit more than assigning a value to a variable. You can actually thing of the left side as a _pattern_ that is matching the right side.

A variable name is a pattern that matches anything, including tuples for example.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>b = (1, 2)
(1, 2)

<font color="#98C379"><b>julia&gt; </b></font>b
(1, 2)
</pre>

What if we want to assign values in a tuple to separate variables? That is where pattern matching comes in handy:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x, y = b
(1, 2)

<font color="#98C379"><b>julia&gt; </b></font>x
1

<font color="#98C379"><b>julia&gt; </b></font>y
2
</pre>

`x, y` is a _pattern_ that represents a list of 2 numbers. Since `b` is a tuple of 2 numbers `(1, 2)`, it matches that pattern. The corresponding values are assigned to `x` and `y`.

The left side of an assignment is the _pattern_ and the right side is the _value_. Variables on the ride side are expanded to their actual values, and variables on the left side are assigned to their corresponding value on the right.

You can surround the pattern with parentheses if you'd like:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>(x, y) = b
(1, 2)
</pre>

Although it looks like a tuple, `(x, y)` is not a tuple. The left side of an assignment is always a _pattern_.

Here is another example:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>(hours, minutes, seconds) = (5, 3, 32)
(5, 3, 32)

<font color="#98C379"><b>julia&gt; </b></font>hours
5

<font color="#98C379"><b>julia&gt; </b></font>minutes
3

<font color="#98C379"><b>julia&gt; </b></font>seconds
32
</pre>

The pattern `x, y` actually matches any list with at least 2 elements. For example:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x, y = (1, 2, 3)
(1, 2, 3)

<font color="#98C379"><b>julia&gt; </b></font>x
1

<font color="#98C379"><b>julia&gt; </b></font>y
2
</pre>

If the pattern in an assignment doesn't match, you get an error:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x, y, z = (1, 2)
<font color="#E06C75"><b>ERROR: </b></font>BoundsError: attempt to access Tuple{Int64, Int64} at index [3]
Stacktrace:
 [1] <b>indexed_iterate(</b><font color="#5C6370">t</font>::Tuple<font color="#5C6370">{Int64, Int64}</font>, <font color="#5C6370">i</font>::Int64, <font color="#5C6370">state</font>::Int64<b>)</b>
<font color="#5C6370">   @ Base</font> <font color="#5C6370">./</font><font color="#5C6370"><u style="text-decoration-style:single">tuple.jl:89</u></font>
 [2] top-level scope
<font color="#5C6370">   @ </font><font color="#5C6370"><u style="text-decoration-style:single">REPL[7]:1</u></font>
</pre>

You can even match lists inside lists. For example:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>a = (1, (2, 3))
(1, (2, 3))

<font color="#98C379"><b>julia&gt; </b></font>x, (y, z) = a
(1, (2, 3))

<font color="#98C379"><b>julia&gt; </b></font>(x, y, z)
(1, 2, 3)</pre>


## Assigning Functions {#assigning-functions}

Assigning a function is like a delayed pattern match. Consider the function `f`:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>f(x) = x^2
f (generic function with 1 method)
</pre>

`f(3)` matches the pattern `f(x)` and therefore is replaced with `3^2`. This is just like how after the assignment `y = 3`, `y` is replaced with `3`.

The same works with multiple parameters:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>g(a, b) = a - b
g (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>g(5, 3)
2
</pre>

Each parameter is a pattern just like in the left side of an assignment. For example, you could do:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>h(a, (x, y)) = a + x + y
h (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>h(1, (2, 3))
6

<font color="#98C379"><b>julia&gt; </b></font>h(1, (2, 3, 10000))
6
</pre>

For example, calling `h(1, (2, 3))` makes the following assignments inside `h`:

```julia
a = 1
(x, y) = (2, 3)
```
