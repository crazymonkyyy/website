
---

title: "mixin\_interfaces"

date: "2021-11-12"

draft: "false"

categories: ["d","programming"]

---

It strikes me I've never seen someone else explore the concept of asking for mixin templates to be a major "interface" of anything in d. It's quite flexible, and could potentially be expandable.

Imagine a UI interface implementing dirty flags, you either implement a recursive template that goes into user-generated widgets types to build up a parallel dirty hierarchy that must be similar in structure to whatever the user is doing, or you could put something that detects if the user-defined a dirty bool, and if not, mixes something that makes an educated guess of a method(perhaps you store a hash of your widget)

In the former, you would need to detect or have API for every edge case, you'd be working with a hairy recursive template without easy access to context; the latter I assert while it would have some issues(it is an invitation to the edges of the compiler where other havn't tread) would just werk, edge cases can be defined by the user to do what the user thinks is best.
