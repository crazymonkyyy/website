
---

title: "tiling\_DE\_part\_3\_The\_problem"

date: "2020-10-21"

draft: "false"

categories: ["tiling"]

---

So if tiling is so great why isn't everyone using it.

![considerthefollowing.png](/images/considerthefollowing.png)

1. Everyone is in the habit of being wrong. Just generally.

2. Historical inertia. Most software that has been written to be in the standard floating environment.

3. Composing workflows means composing applications. Which are spotty in the general user space.

For example, look at this timer app given an unusual size:

{{<raw>}}
<img src="/images/tomate-normal.png" alt="tomate-normal" style="max-width: max-content">

<img src="/images/tomate-borked.png" alt="tomate-borked" style="max-width: max-content">
{{</raw>}}

Trash, unusable trash, awful, horrifying, jank. Its only collection of buttons and some numbers **make it work**, it's a touch tricky but getting it to work properly but isn't rocket surgery.

Every app that doesn't resize properly is something I have to consider when I set up a workspace. A constrant that shouldn't exist.

Take [my](https://github.com/crazymonkyyy/pomodomo) timer app for example:

{{<raw>}}
<img src="/images/pomodomo-normal.png" alt="pomodomo-normal" style="max-width: max-content">

<img src="/images/pomodomo-borked.png" alt="pomodomo-borked" style="max-width: max-content">

<img src="/images/pomodomo-extra.png" alt="pomodomo-extra" style="max-width: max-content">
{{</raw>}}

Look it, varous sizes and all work; *rocket surgery*

Why? Why does mine work, when presumably the other one had more help from a toolkit and probably a less lazy dev; the "toolkits" are for floating wm's, all of them.

For the unaware, programmers don't remake everything from scratch, in this case, if your making a GUI app, you use a toolkit, a collection of software to make buttons and text and system theming work. They are usually tied to an OS or a desktop environment in the case of gtk and qt. In my opinion, its the benefit of a DE is having a toolkit define how to handle fonts and colors. Both the programmer and the user want a system color theme, I as a user don't want half my apps to be blinding theme, and prefer dark themes.
{{<raw>}}
<img src="/images/notepad.png" alt="notepad" style="max-width: max-content">
<img src="/images/myeyes.gif" alt="myeyes" style="max-width: max-content">
{{</raw>}}

And I, as a programmer, don't give a rats ass about color theory, let someone else solve the problem of picking colors. And really really do not want to deal with the madness that is font rendering.

So apps made with toolkits tend to fit nicely with their associated wm/os. But tiling wm's don't have one, at all. So the first order of business for making tiling better would be to make one, that places more emphasis on resizing. Which is actionable.
