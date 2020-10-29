
---

title: "What\_I\_want\_from\_metaprogramming"

date: "2020-10-29"

draft: "false"

categories: ["programing"]

---

Let me just list some quick opinions on meta programing to lay some groundwork, these could be separate rants on their own:

1. Inheritance is annoying to maintain, ducktyping is great and 90% of the time will just be correct and comfy.

2. Fuzzy human standards are better than formal standards, I and everyone else expect addition to be associative, even if most people don't know what associative means. I don't know how to check associativity automatically that won't have false negatives.

3. Templates can do most things I want, even if how c++ does templates is an ugly verbose lisp.

4. You have to check if it's working correctly as an user anyway, so why try to verify its correct in strange abstract meta-programming land?

With that in mind I expect the following things from metaprogramming:

a. A way to define a generic function that takes any type.

b. A way to define op overloads.

c. A way to overload a type's functions if I wish.

d. A way to copy a type with modifications. ```Nullable(T)```
should be easy to write.

e. A community editable rough standard for what op overloads mean.

f. A way to mix in and out strings/compilable data that can be modified compile time by standard code.

Currently, D does (a) and (b) verbosely but correctly. It attempts (c) and (d) but fails in sutle ways(alias this, but that's a rant). (E) happened once(it's what a range is) but doesn't have an actual community-level process. My genetic opRadix does this, but I didn't have a wiki to go edit to state my assumptions or look if someone defined something similar.

---

So in my ideal world, I would have capital letters be automatic generic templates, ```T``` would be disallowed for a type name and just mean straight up, this function is generic. ```T foo(T a)```. Drop the lispyness entirely, make the sane thing simple and inlined.

I would then have lua-like op overloads super-global master table, denoted by the preface of "op", ```string opstring(int a)```, would define the way ints are converted to strings globally. To avoid conflict, allow setting a priority, no bullshit on scoping or complex contracts, or whatever nonsense people are suggesting, just an int compare and make the std defaults negative numbers and user templates default to zero, throw an error if two are equal.

An op overload table for ```T```, and what that implies. 

Honestly string mixins, and mixouts(being an inverse), I still don't see the value in Jai AST trees whatever. I have learned how to parse strings from countless places, I have the tools, and it's presumably part of a good std. If it's a new data type, what's preventing repeating the c++ templates being an ugly lisp mistake? 
