+++
title = "Functions"
author = ["Nick OBrien"]
draft = false
weight = 1004
+++

## Assignment-Style Functions {#assignment-style-functions}

In the same sense that variables can help you use the same value multiple times, functions can help you use the same expression multiple times. Say you're working with the following quadratic polynomial:

{{< katex display >}}
f(x) = 3x^2 - 5x + 6
{{< /katex >}}

The `=` operator can assign an expression to a function. In this case, we want `f(x)` to represent the expression `3x^2 - 5x + 6`:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>f(x) = 3x^2 - 5x + 6
f (generic function with 1 method)
</pre>

The `x` inside this function is not accessible from outside. Variables that are only accessible from the inside are called _local variables_. Note that the name `x` is not special here. We could also do:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>f(num) = 3num^2 - 5num + 6
f (generic function with 1 method)
</pre>

Now, we can evaluate the polynomial at `x=1` without typing the expression:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>f(1)
4
</pre>

Functions can be named like variables:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>triple(x) = 3x
triple (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>triple(5)
15
</pre>

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>raise_to_itself(x) = x ^ x
raise_to_itself (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>raise_to_itself(3)
27
</pre>

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>add4(x) = x + 4
add4 (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>add4(2)
6
</pre>


## Multi-line Functions {#multi-line-functions}

If the code you want to wrap in a function requires multiple expressions, it's best to put it in a `function` block. This is what `f` would look like if we defined it this way:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>function f(x)
           3x^2 - 5x + 6
       end
</pre>

The first line `function f(x)` specifies that we are defining a function named `f` that takes an argument called `x`. When you type this in the REPL, Julia recognizes that you are in the middle of typing a function and creates a new line when you press `enter`.

The next line has the expression that we wish to compute just as in the one line version. Before typing this part, press `tab` to indent a level. The indentation isn't required, but it makes it a lot easier to tell which code belongs to a function.

The final line just has `end`, telling Julia that you are done defining the function.

The value of the last expression in a function is the output. We typically call this the function's _return value_. If you provide `f` some input `y` like `f(y)`, it is replaced with the return value (in this case, `3y^2 - 5y + 6`).

You can explicitly specify an output by prefixing it with `return`.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>function f(x)
           return 3x^2 - 5x + 6
       end
</pre>

Since the code in function is executed from the top down, nothing after the `return` statement is executed. For example:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>function g(x)
           return 2x
           return 9000
       end
g (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>g(5)
10
</pre>


### Example: Cost of a Flight {#example-cost-of-a-flight}

Say you were making a function to calculate the total cost of an airplane ride given the distance `d` it travels. You might consider several sources of cost:

- Fuel costs $200 for taxi/takeof/landing and $100 per km the plane travels
- Personnel costs $40 per km
- Servicing the plane before takeoff and after landing costs $1000

Your function might look like:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>cost(d) = 200 + 100d + 40d + 1000</pre>

What if later you find out that fuel now costs $110 per km? In this example, it's pretty simple to find the `100d` and change it to `110d`, but as your code gets more complex  this becomes unfeasible. One way to address this is to make variabes _inside_ the function:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>function cost(d)
           fuel = 200 + 100d
           personnel = 40d
           service = 1000
           fuel + personnel + service
       end</pre>

The last expression (`fuel + personnel + service`) is returned. It's good practice to explicitly state what statement you're returning if a function has multiple lines of code, but you don't need to. If you did, the function would look like:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>function cost(d)
           fuel = 200 + 100d
           personnel = 40d
           service = 1000
           return fuel + personnel + service
       end</pre>


## Multiple Parameters {#multiple-parameters}

The `x` in a function like `f(x) = x^2` is called the function's _parameter_. In mathematics, functions can have multiple parameters. For example,

{{< katex display >}}
f(x, y) = x + y
{{< /katex >}}

{{<katex>}}x{{</katex>}} and {{<katex>}}y{{</katex>}} are the function's _parameters_. Just like a one-parameter function, you can evaluate the function by substituting the variables:

{{< katex display >}}
f(1, 2) = 1 + 2
{{< /katex >}}

1 and 2 are the _arguments_ in this case.

{{< hint type=note >}}
_Parameters_ and _arguments_ are technically not the same. _Parameters_ are the variables that receive the input values and _arguments_ are the expressions that are assigned to the parameters.
{{< /hint >}}

Functions in Julia can have multiple parameters as well. For example, you could create an `add` function that adds two numbers:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>add(x, y) = x + y
add (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>add(1, 2)
3
</pre>

That is not very impressive though. A function `cone_volume` that computes the volume of a cone might be more useful:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>function cone_volume(radius, height)
           base_area = pi * radius^2
           return 1/3 * height * base_area
       end
cone_volume (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>cone_volume(1, 3)
3.141592653589793
</pre>

Functions can also have _no_ arguments. Mathematically, a function without arguments would always have the same output. Functions in Julia can depend on the external state of the world, so they are not pure mathematical functions. For example, the `time()` function returns the number of seconds since January 1, 1970.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>time()
1.656337427111429e9</pre>

We can use this value to find the current year:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>1970 + time() / (365.25 * 24 * 60^2)
2022.486167415259
</pre>

We can also subtract two times to measure duration:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>t1 = time()
1.656337287725287e9

<font color="#98C379"><b>julia&gt; </b></font>t2 = time()
1.656337292604609e9

<font color="#98C379"><b>julia&gt; </b></font>t2 - t1
4.879322052001953</pre>


## Returning Multiple Values {#returning-multiple-values}

Functions can only return a single value. If you want to return multiple values, you'll have to wrap them inside a single value. One way to do this is with a _tuple_.

A _tuple_ is an ordered list of fixed size. The most common tuple you've probably seen are coordinates on a plane. For example, the point with {{<katex>}}x=3{{</katex>}} and {{<katex>}}y=4{{</katex>}} has coordinates {{<katex>}}(3, 4){{</katex>}}, a tuple of two numbers. In Julia, you write tuples in the same way: `(3, 4)`. A tuple of three numbers might look like `(1, 2, 3)`.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>(1, 2, 3)
(1, 2, 3)

<font color="#98C379"><b>julia&gt; </b></font>x = 5
5

<font color="#98C379"><b>julia&gt; </b></font>y = 10
10

<font color="#98C379"><b>julia&gt; </b></font>point = (x, y)
(5, 10)
</pre>

The parentheses around a tuple are actually optional in some cases, but I recommend that you always use them so it is clearly a tuple.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x = 1, 2
(1, 2)
</pre>


### Example: Hours, Minutes, Seconds {#example-hours-minutes-seconds}

Consider a function that converts total seconds to hours, minutes and seconds. For example, 90 seconds should be 0 hours, 1 minute, and 30 seconds.

Since this function needs to return multiple values, you can return them as a tuple `(hours, minutes, seconds)`.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>function seconds_to_HMS(secs)
           hours = secs ÷ 3600
           minutes = (secs - 3600 * hours) ÷ 60
           seconds = secs - 3600 * hours - 60 * minutes

           return (hours, minutes, seconds)
       end
seconds_to_HMS (generic function with 1 method)
</pre>

{{< expand "Explanation">}}

`secs / 3600` gives the total number of hours (including a fractional part in general). In order to get a whole number of hours, we will use `div` instead.

`div(x, y)` returns the result of `x / y` after rounding towards zero. For example, `div(5, 2)` is `2`. There is an operator for this function `÷` which you can type in the REPL by typing `\div` and pressing tab. Then, `div(x, y)` is the same as `x ÷ y`.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>7 ÷ 4
1

<font color="#98C379"><b>julia&gt; </b></font>div(7, 4)
1

<font color="#98C379"><b>julia&gt; </b></font>8 ÷ 4
2
</pre>

`hours` is then `secs ÷ 3600`.

`minutes` is then `(secs - 3600 * hours) ÷ 60` since `3600 * hours` seconds were already accounted for.

`seconds` is the total seconds minus those account for in `hours` and `minutes`: `secs - 3600 * hours - 60 * minutes`.

Then, we return a tuple containing these 3 values: `(hours, minutes, seconds)`.

{{< /expand >}}

Testing this function out gives the expected results:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>seconds_to_HMS(35)
(0, 0, 35)

<font color="#98C379"><b>julia&gt; </b></font>seconds_to_HMS(90)
(0, 1, 30)

<font color="#98C379"><b>julia&gt; </b></font>seconds_to_HMS(3723)
(1, 2, 3)
</pre>


## Methods {#methods}

Up until now, we've ignored the message `generic function with 1 method` that you get after defining a function. To understand it, you'll need to know the difference between a function and a method.


### Function vs Method {#function-vs-method}

You can think of a method as a function and a specific pattern of parameters. It's easier to understand with an example, though. Consider the `add` function from the previous section.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>add(x, y) = x + y
add (generic function with 1 method)
</pre>

The above code defines a _method_ for the `add` function with parameters `(x, y)`. Functions in Julia can have multiple methods. For example, you could define a method of `add` with 3 parameters:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>add(x, y, z) = x + y + z
add (generic function with 2 methods)
</pre>

Notice that the `add` function now has 2 methods. One method takes `(x, y)` and the other takes `(x, y, z)`.

{{< hint type=note >}}

You can redefine methods, but you cannot delete them. If you wish to clear all the methods from a function, you must restart the REPL.

{{< /hint >}}


### Multiple Dispatch {#multiple-dispatch}

When you call a function, Julia has to decide which method to use. It does this by finding a method with matching parameters. For example, take the `add` function and the 2 methods we defined previously:

```julia
add(x, y)    = x + y
add(x, y, z) = x + y + z
```

Say you call the function with `add(5, 10)`. That fits the pattern specified by the first method `add(x, y)` since there are 2 arguments. Therefore, the code `5 + 10` is executed. If you called the function with `add(1, 2, 3)`, it would match the second method `add(x, y, z)`.

You can call other methods from the same function:

```julia
add(a, b, c, d) = add(a, b) + add(c, d)
```

Be careful that your methods don't call each other in an infinite loop.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>f(x) = f(x, 0)
f (generic function with 1 method)

<font color="#98C379"><b>julia&gt; </b></font>f(x, y) = f(x + y)
f (generic function with 2 methods)
</pre>

Calling `f(1)` calls `f(1, 0)` which calls `f(1)` which calls `f(1, 0)` and so on forever. In reality, your computer will give up after a short while:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>f(1)
<font color="#E06C75"><b>ERROR: </b></font>StackOverflowError:
Stacktrace:
     [1] <b>f(</b><font color="#5C6370">x</font>::Int64<b>)</b>
<font color="#5C6370">       @ </font><font color="#C678DD">Main</font> <font color="#5C6370">./</font><font color="#5C6370"><u style="text-decoration-style:single">REPL[1]:1</u></font>
     [2] <b>f(</b><font color="#5C6370">x</font>::Int64, <font color="#5C6370">y</font>::Int64<b>)</b>
<font color="#5C6370">       @ </font><font color="#C678DD">Main</font> <font color="#5C6370">./</font><font color="#5C6370"><u style="text-decoration-style:single">REPL[2]:1</u></font>
<font color="#5C6370">--- the last 2 lines are repeated 39990 more times ---</font>
 [79983] <b>f(</b><font color="#5C6370">x</font>::Int64<b>)</b>
<font color="#5C6370">       @ </font><font color="#C678DD">Main</font> <font color="#5C6370">./</font><font color="#5C6370"><u style="text-decoration-style:single">REPL[1]:1</u></font>
</pre>

There are more ways to specify argument patterns other than the number of arguments. You will learn more about these in a later section.


## Exercises {#exercises}


### Exercise 1 {#exercise-1}

Make a function `feet_to_cm` that converts a quantity in feet to centimeters. It should have two methods:

-   `feet_to_cm(feet)`
-   `feet_to_cm(feet, inches)`

For example:

-   6 feet = 182.88 cm
-   5 feet 11 inches = 180.34 cm

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>feet_to_cm(6)
182.88

<font color="#98C379"><b>julia&gt; </b></font>feet_to_cm(5, 11)
180.34
</pre>


### Exercise 2 {#exercise-2}

Write a function `quadratic_roots(a, b, c)` that returns the roots of a quadratic polynomial with coefficients `a`, `b`, and `c`:

{{< katex display >}}
ax^2 + bx + c
{{< /katex >}}

For example,

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>quadratic_roots(2, -4, -16)
(-2.0, 4.0)
</pre>
