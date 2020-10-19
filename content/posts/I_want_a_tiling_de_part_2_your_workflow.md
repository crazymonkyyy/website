
---

title: "I\_want\_a\_tiling\_de\_part\_2\_your\_workflow"

date: "2020-10-19"

draft: "false"

categories: ["tiling"]

---

Here's the thing, you use janky tiling as is. It's frankly rare to find someone engaging with their window manager.

I expect you to do a very small subset of actions with your computer:

1. You full screen a web browser, always, no exception.

2. You use a software suite that requires fullscreen and if it's a complex task it's built-in and has its own rolled tiling system.

3. You use the light tiling systems that most desktops have been adopted, by dragging the software to the side of the screen. Windows calls it "snap assist".

All of these while the window can in theory be defined by the user, in reality, you did a ritual you have the system do some math in the background to handle windowing for you; and really trivial things as well.

Ide's are generally speaking two text editors split horizontally with a terminal. I have text editors and a terminal installed, and I like my actual terminal better than the usually subpar one.

![vscode-screenshot](/images/vscode-screenshot.gif)

This is hardly uncommon:

![bitwig](/images/bitwig.png)
![blender](/images/blender.jpg)
![cutemarked](/images/cutemarked.png)
![gummi](/images/gummi.png)
![Kdenlive](/images/Kdenlive.png)
![toonz](/images/toonz.png)

Generally speaking, you have a toolbar, split the window into half or thirds, if you hide something it's with tabs. You'd need some sort of sane tabbing interface, but tabbing is something a window manager can do.

Yet every program must reimplement the logic, and you can't replace the terrible bits, *you can't compose your workflow*. Its the half baked general idea that someone else thought poeple would like.

Your ide is awful like the something from JetBrains, which takes seconds to start up and likely crashes. My ide is a 10 line bash script, and I picked my text editor and terminal separately.

![bspwm](/images/bspwm.png)

```bash
cd $1
textadept -f $(ls) &
bspc node -p east --follow
textadept -f -n &
bspc node -p south -o .6 --follow
nemo $1 &
sleep 1
bspc node -p south -o .15 --follow
alacritty --working-directory $1 &
```

I am ***QUITE*** confindent in this, you don't half hide windows like they are papers on a desk. 