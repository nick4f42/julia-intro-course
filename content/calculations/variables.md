+++
title = "Variables"
author = ["Nick OBrien"]
draft = false
weight = 1003
+++

## Assigning Variables {#assigning-variables}

Often times you want to store the results of calculations for later use. Instead of writing down numbers and typing them out again, you can assign a variable with `=` (the _assignment_ operator).

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x = sqrt(2)
1.4142135623730951
</pre>

Now, you can use `x` in place of `1.4142135623730951` in your future calculations.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x + 1
2.414213562373095
</pre>

You can also reassign `x` to another value if you change your mind:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x = 1.5
1.5

<font color="#98C379"><b>julia&gt; </b></font>x + 2
3.5
</pre>

{{< hint type=caution >}}

It is important to note that `=` in Julia is not like equality in math. It is called an _assignment_ operator because it _assigns_ the variable on the left side to the value on the right side.

{{< /hint >}}

Variable names don't have to be a single character. They can be multiple characters long and contain letters, underscores (i.e. `_`), numbers, and even emoji. They cannot start with a number, though.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>days_in_week = 7
7

<font color="#98C379"><b>julia&gt; </b></font>my_variable = 3 * days_in_week
21

<font color="#98C379"><b>julia&gt; </b></font>😂 = 5/7
0.7142857142857143
</pre>

You can't start a variable name with a number because Julia interprets a number before a variable as multiplication. For example:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x = 3
3

<font color="#98C379"><b>julia&gt; </b></font>5x
15
</pre>

If you want to see the value of a variable, you can just evaluate it by itself:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x = 12 * 21
252

<font color="#98C379"><b>julia&gt; </b></font>x
252
</pre>


## Changing Variables {#changing-variables}

It's often useful to change the value stored in a variable. For example, say you had a quantity stored in meters inside a variable called `distance` and you want to store it in centimeters instead.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>distance = 1.5
1.5
</pre>

The value in centimeters is `distance * 100`, so this value is stored back into `distance`.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>distance = distance * 100
150.0
</pre>

Remember, the left hand side of an assignment has the variables that are being stored. The right hand side is the value. When the code gets executed, the `distance` on the right side is substituted for its value:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>distance = 1.5 * 100
150.0
</pre>


## Exercises {#exercises}


### Exercise 1 {#exercise-1}

Using [NASA's planetary fact sheet](https://nssdc.gsfc.nasa.gov/planetary/factsheet/), make variables for the mass of each planet in the solar system, the moon, and Pluto. Also make a variable for the sun's mass using [NASA's sun fact sheet](https://nssdc.gsfc.nasa.gov/planetary/factsheet/sunfact.html).

Then, answer the following questions:

1.  What percent of the solar system's total mass does the sun take up? What about Earth? Jupiter?
2.  In kg, how much more mass does Jupiter have than Saturn? How many Earths worth of mass is this?
3.  How many more times massive is the moon than Pluto?


### Exercise 2 {#exercise-2}

Determine the mass in kg of a few everyday objects (like a car or banana) and make a variable for each one.

For each of these object, determine how many of them have the same mass as

1.  The solar system
2.  Jupiter
3.  Earth
4.  Pluto
