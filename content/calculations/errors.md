+++
title = "Errors"
author = ["Nick OBrien"]
draft = false
weight = 1005
+++

When Julia cannot understand or run a command, you will get an error. Being a good programmer is more about knowing how to interpret errors than never getting them. Let's go through a couple basic errors you might get when typing in the REPL.


## Syntax Errors {#syntax-errors}


### Extra Space {#extra-space}

Syntax errors occur when Julia can't understand your code. You might get one if you accidentally type a space where you shouldn't:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>12 3 + 1
<font color="#E06C75"><b>ERROR: </b></font>syntax: extra token &quot;3&quot; after end of expression
Stacktrace:
 [1] top-level scope
<font color="#777777">   @ </font><font color="#777777"><u style="text-decoration-style:single">none:1</u></font>
</pre>

Errors can sometimes look overwhelming, but most of the time all the information you need is on the first couple lines. In this case, all we need is the first line of the error message:

<pre class="julia-repl">
<font color="#E06C75"><b>ERROR: </b></font>syntax: extra token &quot;3&quot; after end of expression
</pre>

`ERROR: syntax` means that Julia couldn't understand the code you wrote. The text that follows tells you exactly what Julia couldn't understand. In this case, Julia read `12` as a full number and was expecting an operator like `+` or `*` to follow it. Since Julia got `3` and not an operator, it gave up and threw an error.

This line alone gives you enough information to change `12 3` to `123`. Right now, you don't need to worry about the `Stacktrace` that follows the first line. Later on, you'll learn how to use it to decipher more complex errors.


### Mismatched Brackets {#mismatched-brackets}

Another syntax error you get is caused by mismatched brackets. For example, if you add one two many closing parentheses:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>(1 + 2))
<font color="#E06C75"><b>ERROR: </b></font>syntax: extra token &quot;)&quot; after end of expression
Stacktrace:
 [1] top-level scope
<font color="#757379">   @ </font><font color="#757379"><u style="text-decoration-style:single">none:1</u></font>
</pre>


### Assigning to a Value {#assigning-to-a-value}

The statement `1 = 1` looks alright from a mathematical perspective. However, it doesn't work in Julia.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>1 = 1
<font color="#E06C75"><b>ERROR: </b></font>syntax: invalid assignment location &quot;1&quot; around REPL[1]:1
Stacktrace:
 [1] top-level scope
<font color="#5C6370">   @ </font><font color="#5C6370"><u style="text-decoration-style:single">REPL[1]:1</u></font>
</pre>

Remember that `=` is the _assignment_ operator in Julia. `1 = 1` translates to "assign `1` to the variable `1`." This doesn't work since `1` isn't a variable.


## Undefined Variable Errors {#undefined-variable-errors}

Another common error is trying to access a variable or function that doesn't exist. This can happen if you make a typo:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>sqrt(9)
3.0

<font color="#98C379"><b>julia&gt; </b></font>ssqrt(4)
<font color="#E06C75"><b>ERROR: </b></font>UndefVarError: ssqrt not defined
Stacktrace:
 [1] top-level scope
<font color="#757379">   @ </font><font color="#757379"><u style="text-decoration-style:single">REPL[3]:1</u></font>
</pre>

Again, the first line of the error tells you that `ssqrt not defined`.


## Exercises {#exercises}


### Exercise 1 {#exercise-1}

The following code has a couple mistakes. Find and remove them so that it runs without error.

```julia
sqrt(5 * sqrt(3 - 6/5 + 152.926))) / (5 * sqet(6.2))
```


### Exercise 2 {#exercise-2}

Consider a body with gravitational parameter {{<katex>}}\mu{{</katex>}} The force of gravity on a body with mass {{<katex>}}m{{</katex>}} at a position {{<katex>}}(x,y,z){{</katex>}} relative to the attracting body is:

{{< katex display >}}
    \vec{F} = \left(-F \frac{x}{r}, -F \frac{y}{r}, -F \frac{z}{r}\right)
{{< /katex >}}


Where {{<katex>}}F{{</katex>}} is the magnitude of the force (found with Newton's law of gravitation):

{{< katex display >}}
    F = \frac{\mu m}{r^2}
{{< /katex >}}

And where {{<katex>}}r{{</katex>}} is the distance between the bodies:

{{< katex display >}}
    r = \sqrt{x^2 + y^2 + z^2}
{{< /katex >}}

The following function is meant to return a tuple that represents  {{<katex>}}\vec{F}{{</katex>}}, but there are some errors. Fix the errors so that the function runs.

```text
function gravity_force(μ, m, x, y, z)
    r = sqrt (x^2 + y^2 + z^2)
    F = μm/R^2
    output (-F * x/r, -F * y/r, --F * z/r)
end
```

You can test your function with:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>gravity_force(1e9, 1e5, -3e5, 5e5, 2e4)
(151.05563385525724, -251.75938975876204, -10.070375590350482)

<font color="#98C379"><b>julia&gt; </b></font>gravity_force(1e10, 1e2, 1e5, 2e4, -8e4)
(-45.92361606014639, -9.184723212029278, 36.73889284811711)</pre>
</pre>
