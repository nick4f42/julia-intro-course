+++
title = "Conditional Blocks"
author = ["Nick OBrien"]
draft = false
weight = 1004
+++

So far, your code has been layed out linearly:

```julia
# A
# B
# C
```

In reality, `# A` is just a comment and doesn't execute any code. `A`, `B`, and `C` just represent where code might be. In this example, the code would run in sequence:

{{< mermaid class="text-center" >}}
graph LR
    A --> B --> C
{{< /mermaid >}}

Conditional blocks let you creates _branches_ in this sequence.


## If Block {#if-block}

An `if` block takes a boolean and executes the block only if the boolean is `true`.

```julia
if condition
    # A
end
# after
```

{{< mermaid class="text-center" >}}
graph TD
    if[check condition]
    if -- true --> A --> after
    if -- false --> after
{{< /mermaid >}}

For example, the following code prints a different message depending on the `age` variable.

```julia
age = 21

if age >= 16
    println("You can drive.")
end

if age < 21
    println("You can't drink.")
end

println(age)
```

```text
You can drive.
21
```

{{< mermaid class="text-center" >}}
graph TD
    A[set age to 21] --> if_1(["check if age ≥ 16"])
    if_1 -- true --> B["print #quot;You can drive.#quot;"] --> if_2
    if_1 -- false --> if_2
    if_2([check if age < 21])
    if_2 -- true --> C["print #quot;You can't drink.#quot;"] --> D
    if_2 -- false --> D
    D[print age]

    linkStyle 0,1,2,6 stroke:red;
{{< /mermaid >}}

The red connections represent the path that is actually taken by the code when it runs.


## Else Block {#else-block}

You can attach an `else` block to an `if` block to execute code if the condition is `false`. Together, they are called an if-else block. In general, they look like:

```julia
if condition
    # A
else
    # B
end
# after
```

This corresponds to the following flow chart:

{{< mermaid class="text-center" >}}
graph TD
    if([check condition])
    if -- true --> A
    if -- false --> B
    A & B --> after
{{< /mermaid >}}

For example, this code chooses what to do based on if `x` is greater or equal to `21`.

```julia
age = 25

if age >= 21
    println("you can drink!")
else
    println("go grab a juice box")
end
```

```text
you can drink!
```

{{< mermaid class="text-center" >}}
graph TD
    A[set age to 25] --> if(["check if age ≥ 21"])
    if -- true --> B["print #quot;you can drink!#quot;"]
    if -- false --> C["print #quot;go grab a juice box#quot;"]

    linkStyle 0,1 stroke:red;
{{< /mermaid >}}


## Elseif Block {#elseif-block}

If you change the `else` in an else block to `elseif`, you can specify another condition.

```julia
if x
    # A
elseif y
    # B
end
# after
```

This is equivalent to:

```julia
if x
    # A
else
    if y
        # B
    end
end
# after
```

{{< mermaid class="text-center" >}}
graph TD
    if_x([check x])
    if_x -- true --> A ---> after
    if_x -- false --> if_y([check y])
    if_y -- true --> B --> after
    if_y -- false --> after
{{< /mermaid >}}

You can specify many different `elseif` blocks on one `if` block.

```julia
if x
    # A
elseif y
    # B
elseif z
    # C
end
# after
```

{{< mermaid class="text-center" >}}
graph TD
    if_x([check x])
    if_x -- true --> A ----> after
    if_x -- false --> if_y([check y])
    if_y -- true --> B ---> after
    if_y -- false --> if_z([check z])
    if_z -- true --> C --> after
    if_z -- false --> after
{{< /mermaid >}}

You can also add an `else` block after any amount of `elseif` blocks:

```julia

if x
    # A
elseif y
    # B
else
    # C
end
# after
```

{{< mermaid class="text-center" >}}
graph TD
    if_x([check x])
    if_x -- true --> A ---> after
    if_x -- false --> if_y([check y])
    if_y -- true --> B --> after
    if_y -- false --> C --> after
{{< /mermaid >}}

For example:

```julia
speed = 90

if speed < 40
    println("too slow")
elseif speed > 80
    println("too fast")
else
    println("just right")
end

println(speed)
```

```text
too fast
90
```

{{< mermaid class="text-center" >}}
graph TD
    A[set speed to 90] --> if_1([check if speed < 40])
    if_1 -- true --> B["print #quot;too slow#quot;"] ---> E
    if_1 -- false --> if_2([check if speed > 80])
    if_2 -- true --> C["print #quot;too fast#quot;"] --> E
    if_2 -- false --> D["print #quot;just right#quot;"] --> E
    E[print speed]

    linkStyle 0,3,4,5 stroke:red;
{{< /mermaid >}}


## If/Else Output {#if-else-output}

Say you wanted to set `y` to the absolute value of `x` without using the built-in `abs` function. You could use an if/else statement. In words, we want \`y\` to be \`-x\` if \`x\` is negative and just \`x\` otherwise.

```julia
x = -10

if x < 0
    y = -x
else
    y = x
end
```

This works fine, but it doesn't really reflect how we conceptualized the absolute value. There are two different assignments to `y` in the code. It would be better to think of only one assignment to `y` like a piecewise expression in mathematics:

{{< katex display >}}
y = \begin{cases}
-x & \text{if } x < 0 \\
x & \text{otherwise}
\end{cases}
{{< /katex >}}

Chained if/else/elseif blocks evaluate to the last statement they execute. Because of this, you can assign their output to a variable:

```julia
x = -10

y = if x < 0
    -x
else
    x
end
```

This works no matter how many blocks you have. Consider the following piecewise function:

{{< katex display >}}
f(x) = \begin{cases}
-x/2 & \text{if } x < 0 \\
\sqrt{x} & \text{if } 0 \leq x < 1 \\
1 / x & \text{otherwise}
\end{cases}
{{< /katex >}}

You can translate `f` into Julia very easily:

```julia
f(x) = if x < 0
    -x / 2
elseif 0 ≤ x < 1
    sqrt(x)
else
    1 / x
end
```

If the code gets to the `0 ≤ x < 1` check, `x < 0` must have been `false`. Because of this, it's okay to leave out the `0 ≤ x` part:

```julia
f(x) = if x < 0
    -x / 2
elseif x < 1
    sqrt(x)
else
    1 / x
end
```

Here is `f`'s output for some test values:

```julia
@show f(-2)
@show f(0.25)
@show f(5)
```

```text
f(-2) = 1.0
f(0.25) = 0.5
f(5) = 0.2
```
