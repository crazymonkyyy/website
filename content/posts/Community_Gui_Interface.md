
---

title: "Community\_Gui\_Interface"

date: "2021-09-02"

draft: "false"

categories: ["D","programming","vapid vanting"]

---

So, D has ranges, I feel this is among its strongest traits that worked, despite giving zero fucks about the actual std.ranges.interfaces. "Why"?

Well, the main reason is it works as a solid landmark for a naming scheme for duck typing, you can write your bonkers data structure, and when you go to name the first element, and you pick front and not: head, Front, FrOnT, start, next, \_front, e, or EnterprizeGradeHeadOfIntQue, when you go and copy and paste an algorithm code to fit with your data structure code it has a chance it just magically works, and a more realistic chance you go make an ugly hack to make a compile error go away and write a unit test with your finger crossed.

This is still true if you do something like define an infinite range by making empty an enum, and that may optimize out those code paths as if you wrote the algorithm yourself.

I believe fully generic code is a pipe dream, but that 80% chance ducktyping two black boxes together is an incredible victory and that is what ranges do for the standard problem segmentation of data and algorithms.

I believe ranges could be simplified massively and still serve this purpose. The choice to have popFront not be simplified to just pop is indefensible, but it's still an aspect of the lang I consistently use, such is the value of a community interface.

---

So gui's; the state of gui's in d(and c style langs in general) is shit. And \*drumroll\* I think there should be some effort to define a community interface, much like ranges and the split between data and algorithms, I believe there is a semi-natural split between windowing, theming, and widgets.

To quickly give some structure to those ideas:

Windowing: creates the window, and interfaces with the nonsense of os's demands, takes input, and keeps timers.

Theming: Defines colors, spacing, fonts, and text size; if you want to memoize the time of day to swap to a dark theme at night or increase text size if you plug in a 4k monitor, sure; but it should be far far away from me when I'm trying to draw text to the screen for the 2nd time the month and rediscovering why I hate it so much.

Widgets: should be extremely like ranges, simplifies draw calls until its simple things like boxes and lines for the windowing to slove.

---

I believe the std needs to define at least a color and uirectangle struct, and a (simpler) meta-programming interfaces like std.range.interfaces for the widget, i.e. if something has a dirty flag, can it take text input, etc.



