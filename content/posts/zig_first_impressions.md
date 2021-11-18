
---

title: "zig\_first\_impressions"

date: "2021-11-18"

draft: "false"

categories: ["programming"]

---

So I worked my way thru "ziglings", I'm not claiming to be an expert or anything but I do have some takes.

## Use case

From the non-hype talk on zig, the impression I take away from it was it would be a good target lang for a transpiler and maybe some low-level software. After learning a bit, I'm even more sure of this.

The "there is no confusing control flow" as a design goal, so no op overloading, passing a value by reference means making a pointer, etc. means there is constant friction for me; I wouldn't use it for anything that would require complex types.

On the plus side, it seems they made some effort to clear up c pointer syntax, dereferencing is a postfix .\* and I think defining type syntax maybe strictly right to left(see cdecl for why this is important)

Async seemed comfy in the examples, if so go is ded and should never be bought up again.

Maybe it should be used for async inner-loop hyper-performance code? How hard is it to interop with something else?

## Dislikes

1. Type syntax is split when it's immutable or comptime, from the rest of the definition, maybe this makes sense but I don't see it.

2. I really really like op overloading.

3. The error messages for what the hell I was doing wrong weren't very clear and would cite errors well into the std

4. I haven't tried enough yet but I don't see anything that would make composition comfy, in d there's utfs, so the composition can be .map.filter.map.map.map and not something read with a "spiral method" and far too many ()'s