+++
title = "Arithmetic"
author = ["Nick OBrien"]
draft = false
weight = 1002
+++

## Using Julia as a Calculator {#using-julia-as-a-calculator}

Julia supports all of the arithmetic operators you would expect to find on a calculator:

-   addition: `+`
-   subtraction: `-`
-   multiplication: `*`
-   division: `/`
-   exponentiation: `^`

Go ahead and try using these operators in the REPL. The result of these calculations is displayed on the next line.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>2 + 2
4

<font color="#98C379"><b>julia&gt; </b></font>5 - 3
2

<font color="#98C379"><b>julia&gt; </b></font>5 * 6
30

<font color="#98C379"><b>julia&gt; </b></font>5 / 2
2.5

<font color="#98C379"><b>julia&gt; </b></font>5 ^ 2
25
</pre>

You can use parentheses to change the order of evaluation:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>(2 + 6) * 3 / 4
6.0
</pre>

Julia comes with built-in mathematical functions like the square root:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>sqrt(9)
3.0
</pre>

The spaces between the numbers and operators are not mandatory, but adding a single space tends to make it easier to read. Any of the following examples are valid:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>2+2
4

<font color="#98C379"><b>julia&gt; </b></font>   2    +  2
4

<font color="#98C379"><b>julia&gt; </b></font>sqrt(  4    )
2.0
</pre>

Numbers can be written in scientific notation with `e`. For example, you can write {{< katex >}} 2.998 \times 10^8 {{< /katex >}} both as:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>2.998 * 10^8
2.998e8

<font color="#98C379"><b>julia&gt; </b></font>2.998e8
2.998e8
</pre>

Julia comes with some built-in mathematical constants like &pi;. You can refer to it with `pi`:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>pi^2 / 6
1.6449340668482264
</pre>

You can also insert the &pi; symbol in the REPL by typing `\pi` and pressing the `TAB` key.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>\pi
</pre>

After pressing `TAB` and entering the expression:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>π
π = 3.1415926535897...
</pre>


## Exercises {#exercises}


### Exercise 1 {#exercise-1}

If you took all the bacteria in the ocean and lined them up end to end, how far would they reach?

First, take a guess. Then, expand the section below and use the data to calculate an approximation.

{{< expand "Useful Data">}}

-   There is about 1.335×10<sup>21</sup> liters of water in the ocean
-   A single liter of seawater has about 100 million bacteria
-   The average bacteria is about 3 µm long (1 µm = 10<sup>-6</sup> m)
-   1 lightyear is about 9.461×10<sup>15</sup> m
-   For reference, the distance to the nearest galaxy (Andromeda) is about 2.537 million light years

{{< /expand >}}


### Exercise 2 {#exercise-2}

If you packed every human on earth into a mound, how high would it stand?

Again, take a guess. Then, use the data below to calculate an approximation.

{{< expand "Useful Data">}}

-   The average human takes up a volume of about 0.065 m<sup>3</sup>
-   You can assume that 5% of the mound's volume is empty space
-   You can also assume that the mound is a 45&deg; cone
-   The formula for the volume V of a 45&deg; cone in terms of its height h is:

{{<katex display>}}
V = \frac13 \pi h^3
{{</katex>}}

{{< /expand >}}
