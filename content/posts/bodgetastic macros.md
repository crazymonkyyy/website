---

title: "bodgetastic macros"

date: "2022-03-28"

draft: "false"

categories: ["commandline","programming"]

---
I wanted macros. So like many times before I started mushing tools together lazily with the fuzziest idea of a big picture, and this time was so... easy comparably, and I can imagine several easy modifications. So here's a sign post, if you want macros of some sort consider these tools and the syntax:

### xte and xautomation
```bash
yay xautomation
xte 'str hello'
```
xte is from the collection of tools called xautomation, with this syntax with type out "hello"

I also use `xte xkeyup` to unpress a button

### sxkhd advanced syntax

`alt+{a-z}` will define 26 key commands all at once.

`alt+@a` (and it has to be on the letter key) will redefine the key command to be on release.

In general, you need to plan around this when writing your tools, but it's fairly straightforward.

### Combining it together with d

```d
import std.stdio;
import std.process;
import std.algorithm;
import std.array;
import std.conv;
void main(string[] s){
	string home=executeShell("echo $HOME").output[0..$-1];
	string t=File(home~"/.config/mymacro/"~s[1]).byLineCopy.joiner.array.to!string;
	t="xte 'str "~t~"'";
	t.executeShell;
}
```

That's it, that's all the code I wrote, I grab a file from a `.config` folder and construct an `xte` command.

and my sxkhdrc:
```bash
mod3 + @{a-z}
   xte 'keyup Hyper_R'; ~/src/d/quickmarcos {a-z}

mod3+shift+{a-z}
   zenity --entry >> ~/.config/mymacro/{a-z}
```

so, when I press `hyper+a` sxhkd constructs the following command
`xte 'keyup Hyper_R'; ~/src/d/quickmarcos a`; turning off the hyper key and telling the above d code the all-important message "a", telling it to open `~.config/mymacro/a`

and well `hyper+shift+a`, using zenity pops up a text box and then puts that text box into `a`

.... It's all so simple it makes me wonder why I didn't do it forever ago.

The complexities to pay attention to are:

1. you need to define the command to happen *after* the keys are pressed, for race condiction reasons
2. You need to disable the meta key trigger to prevent some rather unfortunate loops