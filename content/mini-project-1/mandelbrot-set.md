+++
title = "The Mandelbrot Set"
author = ["Nick OBrien"]
draft = false
weight = 1002
+++

## Definition {#definition}

Let {{<katex>}}c{{</katex>}} be a complex number and let {{<katex>}}z_0, z_1, \ldots{{</katex>}} be an infinite series where

{{< katex display >}}
\begin{align*}
    z_0 &= 0 \\
    z_n &= f(z_{n-1}, c) \\[1em]
    f(z, c) &= z^2 + c
\end{align*}
{{< /katex >}}

{{<katex>}}c{{</katex>}} is in the mandelbrot set if {{<katex>}}z_n{{</katex>}} does not diverge to infinity.


## Examples {#examples}

Let's go through a few examples. First, let's see if {{<katex>}}c = -1{{</katex>}} is in the mandelbrot set. We start out with the initial value  {{<katex>}}z_0 = 0{{</katex>}}. Then, we use {{<katex>}}f(z,c){{</katex>}} to get {{<katex>}}z_1, z_2, \ldots{{</katex>}} and so on.

{{< katex display >}}
\begin{align*}
    z_0 &= 0 &&= 0 \\
    z_1 &= 0^2 - 1 &&= -1 \\
    z_2 &= (-1)^2 - 1 &&= 0 \\
    z_3 &= 0^2 - 1 &&= -1
\end{align*} \\
\vdots
{{< /katex >}}

Since the sequence alternates between {{<katex>}}0{{</katex>}} and {{<katex>}}-1{{</katex>}}, it will never diverge to infinity. Therefore, {{<katex>}}-1{{</katex>}} is in the mandelbrot set.

Next, let's check if {{<katex>}}1{{</katex>}} is in the mandelbrot set.

{{< katex display >}}
\begin{align*}
    z_0 &= 0 &&= 0\\
    z_1 &= 0^2 + 1 &&= 1 \\
    z_2 &= 1^2 + 1 &&= 2 \\
    z_3 &= 2^2 + 1 &&= 5 \\
    z_4 &= 5^2 + 1 &&= 26
\end{align*} \\
\vdots
{{< /katex >}}

Obviously {{<katex>}}z_n{{</katex>}} will blow up for this choice of {{<katex>}}c{{</katex>}}. Therefore, {{<katex>}}1{{</katex>}} is not in the mandelbrot set.


## Algorithm {#algorithm}

It can be shown that {{<katex>}}c{{</katex>}} is not in the mandelbrot set if {{<katex>}}\left|z_n\right| > 2{{</katex>}} for some {{<katex>}}n{{</katex>}}. It is harder to conclusively show that a number is /inside/ the mandelbrot set because you can't compute {{<katex>}}z_\infty{{</katex>}}. Instead, you can set a large upper bound {{<katex>}}N{{</katex>}} and give up after {{<katex>}}z_N{{</katex>}}.

In pseudocode, the algorithm is:

```text
set z to 0

loop N times:
    set z to z^2 + c
    if abs(z) > 2:
       return false

return true
```

{{< expand "Pseudocode" >}}

_Pseudocode_ is a way to express in algorithm in no specific programming language. It usually has similar syntax to common languages.

{{< /expand >}}
