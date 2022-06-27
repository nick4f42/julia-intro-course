+++
title = "While Loops"
author = ["Nick OBrien"]
draft = false
weight = 1005
+++

## Basic Structure {#basic-structure}

A `while` block executes code _while_ a condition is true. In general, a `while` block looks like:

```julia
# A
while condition
    # B
end
# C
```

The `A`, `B`, and `C` comments represent some code that might be there. Julia follows these steps when executing this code:

{{< mermaid class="text-center" >}}
graph TD
    A --> while[check condition]
    while -- true --> B --> while
    while -- false ---> C
{{< /mermaid >}}

If the condition is always `false`, the block will not execute:

```julia
while false
    println("won't print")
end
println("will print")
```

```text
will print
```

If the condition is always `true`, the block will execute forever (or until you interrupt the execution with `CTRL-c`).

```julia
while true
    println("hi")
end
```

If the condition depends on a variable, the while loop can run some whole number of times:

```julia
x = 1
while x <= 5
    println(x)
    x += 1
end
println("done")
```

```text
1
2
3
4
5
done
```

{{< mermaid class="text-center" >}}
graph TD
    A[set x to 1] --> while["check if x ≤ 5"]
    while -- true --> B[print x] --> C[increase x's value by one] --> while
    while -- false ----> D["print #quot;done#quot;"]
{{< /mermaid >}}

This has the effect of printing the integers between `1` and `5`, then printing "done". Here's a similar example that counts down instead of up:

```julia
t = 3
while t > 0
    println(t)
    sleep(1)
    t -= 1
end
println("liftoff!")
```


## Exercises {#exercises}


### Exercise 1 {#exercise-1}

Without running it, determine the output of the following code:

<a id="code-snippet--while-exercise-1"></a>
```julia
x = 1234

while x > 0
    print(x % 10)
    x = div(x, 10)
end

println()
```
