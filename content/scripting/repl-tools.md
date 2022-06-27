+++
title = "REPL Tools"
author = ["Nick OBrien"]
draft = false
weight = 1007
+++

## Getting Help {#getting-help}

If you're ever unsure what an operator (like `+`), function (like `abs`), or variable (like `pi`) does, you can use the REPL's built-in help system. Start on a blank prompt and type a single `?` character:

<pre class="julia-repl"><font color="#98C379"><b>julia&gt; </b></font>?</pre>

This will automatically bring up the `help?>` prompt:

<pre class="julia-repl"><font color="#D19A66"><b>help?&gt; </b></font></pre>

Now type the name of the item you're curious about and press enter. We'll start with the `+` operator:

<pre class="julia-repl"><font color="#D19A66"><b>help?&gt; </b></font>+
search: <b>+</b>

<font color="#56B6C2">  +(x, y...)</font>

  Addition operator. <font color="#56B6C2">x+y+z+...</font> calls this function with all arguments, i.e.
  <font color="#56B6C2">+(x, y, z, ...)</font>.

<b>  Examples</b>
<b>  ≡≡≡≡≡≡≡≡≡≡</b>

<font color="#56B6C2">  julia&gt; 1 + 20 + 4</font>
<font color="#56B6C2">  25</font>
<font color="#56B6C2">  </font>
<font color="#56B6C2">  julia&gt; +(1, 20, 4)</font>
<font color="#56B6C2">  25</font>

  ────────────────────────────────────────────────────────────────────────────

<font color="#56B6C2">  dt::Date + t::Time -&gt; DateTime</font>

  The addition of a <font color="#56B6C2">Date</font> with a <font color="#56B6C2">Time</font> produces a <font color="#56B6C2">DateTime</font>. The hour, minute,
  second, and millisecond parts of the <font color="#56B6C2">Time</font> are used along with the year,
  month, and day of the <font color="#56B6C2">Date</font> to create the new <font color="#56B6C2">DateTime</font>. Non-zero microseconds
  or nanoseconds in the <font color="#56B6C2">Time</font> type will result in an <font color="#56B6C2">InexactError</font> being thrown.</pre>

The examples section is very useful to learn the usage at a glance. The second example actually shows a feature of `+` that you probably haven't used in this course before: it also acts like a function. `a + b` is the same as `+(a, b)`.

The second help section that involves `Date` and `Time` is less useful to you right now. All that's important to know right now is that the section is there because `+` has a special definition for dates and times.

Now, let's look at the help output for the `abs` function.

<pre class="julia-repl"><font color="#D19A66"><b>help?&gt; </b></font>abs
search: <b>abs</b> <b>abs</b>2 <b>abs</b>path <b>abs</b>tract <b>Abs</b>tractSet &apos;<b>abs</b>tract type&apos; <b>Abs</b>tractChar

<font color="#56B6C2">  abs(x)</font>

  The absolute value of <font color="#56B6C2">x</font>.

  When <font color="#56B6C2">abs</font> is applied to signed integers, overflow may occur, resulting in the
  return of a negative value. This overflow occurs only when <font color="#56B6C2">abs</font> is applied to
  the minimum representable value of a signed integer. That is, when <font color="#56B6C2">x ==</font>
<font color="#56B6C2">  typemin(typeof(x))</font>, <font color="#56B6C2">abs(x) == x &lt; 0</font>, not <font color="#56B6C2">-x</font> as might be expected.

  See also: <font color="#56B6C2">abs2</font>, <font color="#56B6C2">unsigned</font>, <font color="#56B6C2">sign</font>.

<b>  Examples</b>
<b>  ≡≡≡≡≡≡≡≡≡≡</b>

<font color="#56B6C2">  julia&gt; abs(-3)</font>
<font color="#56B6C2">  3</font>
<font color="#56B6C2">  </font>
<font color="#56B6C2">  julia&gt; abs(1 + im)</font>
<font color="#56B6C2">  1.4142135623730951</font>
<font color="#56B6C2">  </font>
<font color="#56B6C2">  julia&gt; abs(typemin(Int64))</font>
<font color="#56B6C2">  -9223372036854775808</font>
</pre>

If you weren't sure before, the first line of the help output tells you that `abs(x)` is the absolute value of `x`. There is an additional paragraph that explains some subtleties but you don't need to worry about those right now.

Finally, let's look at the help output for the variable `pi`.

<pre class="julia-repl"><font color="#D19A66"><b>help?&gt; </b></font>pi
search: <b>pi</b> <b>Pi</b>pe <b>pi</b>peline <b>Pi</b>peBuffer sin<b>pi</b> cos<b>pi</b> cis<b>pi</b> get<b>pi</b>d rem2<b>pi</b> mod2<b>pi</b> <b>p</b>r<b>i</b>nt

<font color="#56B6C2">  π</font>
<font color="#56B6C2">  pi</font>

  The constant pi.

  Unicode <font color="#56B6C2">π</font> can be typed by writing <font color="#56B6C2">\pi</font> then pressing tab in the Julia REPL,
  and in many editors.

  See also: <font color="#56B6C2">sinpi</font>, <font color="#56B6C2">sincospi</font>, <font color="#56B6C2">deg2rad</font>.

<b>  Examples</b>
<b>  ≡≡≡≡≡≡≡≡≡≡</b>

<font color="#56B6C2">  julia&gt; pi</font>
<font color="#56B6C2">  π = 3.1415926535897...</font>
<font color="#56B6C2">  </font>
<font color="#56B6C2">  julia&gt; 1/2pi</font>
<font color="#56B6C2">  0.15915494309189535</font>
</pre>

Again, there is a brief description at the start and some examples at the bottom.
