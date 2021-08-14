
---

title: "adventures\_in\_programming"

date: "2021-08-14"

draft: "false"

categories: ["d","programming"]

---


So I needed an infographic tool and for some reason, I forgot to assume everyone else was an idiot and only pieces of shit existed. Was quite a mistake open office is bloated as all hell and when you use it for this is slows down further and further; until it was 30 seconds to process a single action by the end. So, I'm writting my own.

Anyway, I improved one of my libs so making my own tool will be comfy; after all, what I needed was something that displays a list of buttons; comparing the real work a computer needs to do with what enterprise oo open office must be is a horrifying prospect. Also, apparently, people don't understand how to use my comfysettings.

----

So to start I'll copy and paste a raylib folder, get the new version of comfysettings going, and set up a helloworld.

![hello](/images/hello.png)

So, what's going on here:

1. There's a raylib main loop (not explaining raylib).

2. I've setup a config system.

3. I've setup f1 to popup a zenity window to modify "hello".

Setup makes the functions reload and save; and mixes in "config.mix"(which has a simple assignment to hello). Reload and save interact with "config.conf".

Zenity is a command-line program that makes helpful popup boxes.

So the string hello is first set by whatever is in config.conf, and then whatever you put in f1 pop up box which then saves it to config.conf.

---

So we have a hello world with some basic syntax; let's do the data-oriented design thing and \*drum roll\* start with designing the data. I fundamentally believe I just need a list of buttons that need to be drawn to a screen.

![button](/images/button.png)

Truly it's inconceivable, how do I do it?

Strange is there to handle edge cases whenever they arise; I know I need at least diagonal buttons, comfysettings won't be kind to change the data types on it so I do need to think ahead here.

---

Let's get colors going, I like "base16 hardcore" well enough

![colors](/images/colors.png)

Some "rectangular selection" to make it into basic strings and a good old "throw enum in front of a variable to make it a compile-time const". I'll quickly make button.draw use this array.

---

Next, let's make a tooltip; realistically a tooltip is a collection of easy-to-modify variables that directly affect the main loop. And you have a text editor.

![tool1](/images/tool1.png)

And now when you edit tool.conf and press space; you're affecting the temp button in the main loop. wow, such magic.

---

Let's set up saving

![save](/images/save.png)

nice and easy right.

![fuck_everything](/images/fuck_everything.png)

wait.... wait... what? FUCKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKK

it's fixable but... god damn it, I wanted this to be nice and comfy ;\_\_;

Fuck the fucking compiler and the dev team for not fixing the bugs.

End of this semi tutorial.

---

You import app into dson and copy button to global scope; breaking the tiny bit of abstraction even I thought was a good idea and it works \*unammused\*. Ask me how I knew how to fix that quickly /s.

Anyway, hopeful this provided insight into how I think, taught you enough about zenity an option worth considering, and will work well enough to teach people how to use comfysettings.