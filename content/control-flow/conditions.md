+++
title = "Conditions"
author = ["Nick OBrien"]
draft = false
weight = 1002
+++

When you're writing a script, you will often want to run different code based on different conditions. Conditions can come in many forms, but they are typically reduced to either `true` or `false`. A value that is either `true` or `false` is called a _boolean_ (named after the logician George Boole).

Julia has boolean constants `true` and `false`:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>true
true

<font color="#98C379"><b>julia&gt; </b></font>false
false
</pre>

Let's look at how to turn a condition into a boolean.


## Numeric Comparisons {#numeric-comparisons}

There are many different conditions on numbers in mathematics. For example,

{{< katex display >}}
\begin{align*}
x &= 5 \\
x &\ne 10 \\
x &> 2 \\
\end{align*}
{{< /katex >}}

Julia has operators for these comparisons. They return `true` or `false` based on whether the condition is met.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>5 &gt; 3
true

<font color="#98C379"><b>julia&gt; </b></font>2 &lt; -10
false
</pre>

Like any other operator, the values being compared are fully evaluated before comparison:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>x = 5
5

<font color="#98C379"><b>julia&gt; </b></font>y = 8
8

<font color="#98C379"><b>julia&gt; </b></font>x &lt; y
true
</pre>

| Operator           | Comparison            |
|--------------------|-----------------------|
| `==`               | equality              |
| `!=`, `≠` (`\ne`)  | inequality            |
| `<`                | less than             |
| `<=`, `≤` (`\leq`) | less than or equal    |
| `>`                | greater than          |
| `>=`, `≥` (`\geq`) | greater than or equal |

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>1 == 1
true

<font color="#98C379"><b>julia&gt; </b></font>1 == 2
false

<font color="#98C379"><b>julia&gt; </b></font>1 != 1
false

<font color="#98C379"><b>julia&gt; </b></font>1 ≠ 2
true

<font color="#98C379"><b>julia&gt; </b></font>1 &lt; 2
true

<font color="#98C379"><b>julia&gt; </b></font>2 &lt; 1
false

<font color="#98C379"><b>julia&gt; </b></font>4 &gt; 3
true

<font color="#98C379"><b>julia&gt; </b></font>3 ≥ 3
true

<font color="#98C379"><b>julia&gt; </b></font>2 &gt;= 3
false

<font color="#98C379"><b>julia&gt; </b></font>1.5 &lt; 1.6
true

<font color="#98C379"><b>julia&gt; </b></font>1 == 1.0
true
</pre>

Comparisons are chained together like in math. For example, `1 < x < 5` is true only if `x` is between `1` and `5`. Also, `x == y == z` is true only if `x`, `y`, and `z` are equal.

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>1 &lt; 2 &lt; 3
true

<font color="#98C379"><b>julia&gt; </b></font>1 == 1 == 2
false

<font color="#98C379"><b>julia&gt; </b></font>1 == 1 &lt; 3
true
</pre>


## Boolean Operators {#boolean-operators}

Lots of conditions involve combining other conditions. For example, `x > 5` and `y == 2`. You can express these conditions with the boolean operators for _and_, _or_, and _not_:

-   and: `x && y`
    -   are `x` and `y` are both `true`?
-   or: `x || y`
    -   is at least one of `x` and `y` `true`?
-   not: `!x`
    -   `true` if `x` is `false`, `false` if `x` is `true`

Here are the outputs for each input combination:

-   and
    -   `false && false` is `false`
    -   `false && true` is `false`
    -   `true && false` is `false`
    -   `true && true` is `true`
-   or
    -   `false || false` is `false`
    -   `false || true` is `true`
    -   `true || false` is `true`
    -   `true || true` is `true`
-   not
    -   `!false` is `true`
    -   `!true` is `false`

You can find the precedence of these operators in the [Julia manual](https://docs.julialang.org/en/v1/manual/mathematical-operations/#Operator-Precedence-and-Associativity). In short, `&&` is evaluated before `||`. That is, `x && y || z` is equivalent to `(x && y) || z`. When in doubt, use parentheses.


## Exercises {#exercises}


### Exercise 1 {#exercise-1}

Create a function `inside_circle` that determines if a point is inside a circle.

```julia
inside_circle(r, (x, y))
```

The circle has radius `r` and is centered at the origin `(0, 0)`. The function should return `true` if the point `(x, y)` is inside the circle and `false` otherwise.


### Exercise 2 {#exercise-2}

Create a function `passes_class` that determines if a student passes a class.

```julia
passes_class(midterm1, midterm2, final, hw_avg, attendance)
```

For example, `passes_class(0.95, 0.83, 0.91, 0.99, 0.6)` means that the student got 95% on midterm 1, 83% on midterm 2, 91% on the final, averaged 99% on homework, and attended 60% of their classes.

A students overall grade is determined by averaging each grade with the following weights:

```julia
grade = 0.3 * (midterm1 + midterm2) + 0.2 * final + 0.2 * hw_avg
```

The function should return a boolean deciding whether a student passes the class based on the following conditions:

-   A student fails if they attend less than half of classes
-   If a student gets less than 30% on any exam (midterm of final), they fail
-   The student fails if their overall grade is below 60%
-   Otherwise, a student passes

{{< expand "Hint" >}}

I recommend making boolean variables for each condition above. For example, `attendance_ok`, `exam_ok`, and `grade_ok`. The student should only pass if all variables are `true`.

{{< /expand >}}
