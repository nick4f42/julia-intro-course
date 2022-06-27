+++
title = "For Loops"
author = ["Nick OBrien"]
draft = false
weight = 1006
+++

## Basic Structure {#basic-structure}

For loops are useful for running the same code for multiple values. If you find yourself writing code like this:

```julia
println(1)
println(2)
println(3)
println(4)
println(5)
```

a for loop would make your life much easier. In general, a for loop looks like:

```julia
for var in iterable
    # code
end
```

In Julia, an _iterator_ is something that has individual elements that can be taken one by one. For example, `(1, 2, 3)` is an iterator since you can take out `1`, `2`, then `3`. The variable `iterable` represents any value that is an iterator.

{{< mermaid class="text-center" >}}
graph TD
    A[get next value in iterable]
    A -- has next --> B[set var to next value] --> C[run code inside loop] --> A
    A -- none left ----> D[exit loop]
{{< /mermaid >}}

For example, if `iterable` was `(1, 2, 3)`, the for loop above would be similar to:

```julia
var = 1
# code

var = 2
# code

var = 3
# code
```

Consider this example:

```julia
for x in (1, 2, 3)
    println("inside for loop!")
    println(x)
end
```

This would be like writing

```julia
x = 1
println("inside for loop!")
println(x)

x = 2
println("inside for loop!")
println(x)

x = 3
println("inside for loop!")
println(x)
```

{{< hint type=note >}}

Instead of writing `for x in y`, you could write `for x = y` or `for x ∈ y`. Each of them are equivalent.

{{< /hint >}}


## Ranges {#ranges}

Instead of manually typing a range of integers like `(1, 2, 3, 4, 5)`, you can use a _range_. Julia lets you specify a range of numbers from `start` to `stop` with `start:stop`.

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

You can also specify an interval `step` with `start:step:stop`.

```julia
for x in 0:2:6
    println(x)
end
```

```text
0
2
4
6
```

This works with decimal numbers as well:

```julia
for x in 0:0.25:1
    println(x)
end
```

```text
0.0
0.25
0.5
0.75
1.0
```


## Variable Unpacking {#variable-unpacking}

Say you had a tuple of `(x, y)` points:

```julia
points = ((3, 4), (1, 1), (-3, 10))
```

You can iterate over it in the same way as ranges:

```julia
for point in points
    x, y = point
    println("x = ", x)
end
```

```text
x = 3
x = 1
x = -3
```

Instead of unpacking `point` into `(x, y)` inside the block, you can do it after the `for` keyword:

```julia
for (x, y) in points
    println("x = ", x)
end
```


## Strings {#strings}

Strings are like lists of characters, so they can be iterated over with a for loop.

```julia
for c in "Hello!"
    println("char: ", c)
end
```

```text
char: H
char: e
char: l
char: l
char: o
char: !
```

`c` is assigned to the individual characters `'H'`, `'e'`, `'l'`, `'l'`, `'o'`, and `'!'`. Remember, a character surrounded by single quotes like `'x'` is a single character while anything between double quotes like `"xyz"` is a string of characters.

For example, if you wanted to change every `'H'` to a `'J'` you could add an if statement at the start of the block:

```julia
for c in "Hello!"
    # If c is 'H', use 'J'
    # Otherwise, use c
    char = if c == 'H'
        'J'
    else
        c
    end

    println("char: ", char)
end
```

```text
char: J
char: e
char: l
char: l
char: o
char: !
```


## Nested For Loops {#nested-for-loops}

There's nothing stopping you from putting for loops inside of other for loops:

```julia
for x in "AB"
    for y in (1, 2)
        println(x, y)
    end
end
```

```text
A1
A2
B1
B2
```

Julia provides an easier way to type the above:

```julia
for x in "AB", y in (1, 2)
    println(x, y)
end
```

```text
A1
A2
B1
B2
```


## Exercises {#exercises}


### Exercise 1 {#exercise-1}

Using a for loop, print the following output:

```text
*
**
***
****
*****
******
```

Note that the `^` operator repeats a character. For example, `'x' ^ 5` is `"xxxxx"`.


### Exercise 2 {#exercise-2}

Using a for loop, create a function `count_char(c, word)` that counts the number of characters `c` in `word`.


### Exercise 3 {#exercise-3}

The following function `english_words` returns a list of over 400k English words.

```julia
using Downloads

function english_words()
    io = Downloads.download(
        "https://raw.githubusercontent.com/dwyl/english-words/master/words.txt",
        IOBuffer())
    seekstart(io)
    return readlines(io)
end
```

Print out every English word that has 4 or more 'z's.
