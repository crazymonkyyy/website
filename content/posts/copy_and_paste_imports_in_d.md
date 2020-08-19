
---

title: "copy and paste imports in d"

date: "2020-08-01"

draft: "false"

---

Orginally when I was looking for a lang, I had a single red flag when looking at d's web site; which when compared to other randomly selected webshit langs is amazing. However it still stands that the d devs shit on good parts of c, when allow me to be blunt **_c is the best lang aviable;_** thats more of a reflection on the other langs that exist, its really showing its age, but I stand by that statement until a suitable c replacement gets made.

```md
> We are better the c

> c is to much fun we cant have that

> Using monkey as a negitive adjective to mean silly

> Scoping is a good thing
```
>https://dlang.org/articles/mixin.html

Excuse me? That is not enough reverence to jank, c, or monkeys.

I digress, I _like_ c imports for being purely copy and paste, moving code around should the right of the programmer without restrictions, and scoping rules are ***oft'*** a restriction, and can cause a rewrite.

However they are possible in d, probally not intentionally so don't show this to the devs, they may get some anti-fun ideas.

```d

mixin(import("foo.mix"));

```

A bit of jank and shrill poeple who ever see your code being yelly are a small price to pay to avoid erroneous and non-comfy reformating or even leaving code where it doesn't belong just to keep it in scope.

You will however need to use to -J=. compiler option.

Throw these options in your dub.json if your using dub.

```css

  "dflags":["-mixin=mix", "-J=./source"],

  "extraDependencyFiles":["\*.mix"], 

```

And I'm declaring the (monkyyy) offical standard style guide for using copy and paste imports in d require them to have a .mix file extension; its on page 4.

