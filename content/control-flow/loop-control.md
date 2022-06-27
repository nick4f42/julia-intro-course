+++
title = "Loop Control"
author = ["Nick OBrien"]
draft = false
weight = 1007
+++

In both `while` and `for` loops, there are a couple keywords that allow you to further control their execution.


## Break {#break}

When Julia arrives at a `break` statement, the loop is immediately stopped. For example, this loop usually prints the numbers from 1 to 5:

```julia
for x in 1:5
    println(x)
end
```

```text
1
2
3
4
5
```

Adding a break statement when `x` is `3` has this effect:

```julia
for x in 1:5
    if x == 3
        println("breaking!")
        break
    end

    println(x)
end
```

```text
1
2
breaking!
```


## Continue {#continue}

When Julia arrives at a `continue` statement, the current loop is skipped and the loop continues at the next step. For example, replacing the `break` with `continue` in the example above has this effect:

```julia
for x in 1:5
    if x == 3
        println("skipping!")
        continue
    end

    println(x)
end
```

```text
1
2
skipping!
4
5
```


## Return {#return}

The `return` statement immediately exits a function, even if the `return` statement is inside a loop. You can use this to control the flow of a loop.

For example, the following function returns the first even number in a collection of numbers, or nothing if there are only odd numbers.

```julia
function first_even(nums)
    for x in nums
        if iseven(x)
            return x
        end
    end
    return nothing
end
```

Testing this function out:

```julia
first_even((1, 3, 5, 8, 9))
```

```text
8
```


## Exercises {#exercises}


### Exercise 1 {#exercise-1}

Consider the following `while` loop:

```julia
x = 1
while x < 5
    println(x)
    x += 1
end
```

Now, write code that has the same output by replacing the `while` loop with...

1.  A `for` loop
2.  A `while true` loop


### Exercise 2 {#exercise-2}

Create a function `isprime(n)` that determines whether `n` is prime.

{{< expand "Prime Numbers" >}}

A prime number is a whole number greater than 1 that is only divisible by 1 and itself. For example, 7 is prime but 6 is not since you can evenly divide 6 by 2.

{{< /expand >}}

{{< expand "Hint 1" >}}

Checking if a number `x` is divisible is `y` is equivalent to asking if the remainder or `x / y` is zero. See the `rem` function (or its operator `%`).

{{< /expand >}}

{{< expand "Hint 2" >}}

To determine if some number `n` is prime, you need to check if any number evenly divides `n` (other than `1` and `n`).

In fact, you only need to check the numbers between =2= and =floor(sqrt(n))=.

{{< /expand >}}


### Exercise 3 {#exercise-3}

Using your `isprime` function, print the first 50 prime numbers.
