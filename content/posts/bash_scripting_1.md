
---

title: "bash\_scripting\_1"

date: "2020-08-20"

draft: "false"

categories: ["bash"]

---

So, in order to make writing a blog with images comfy I need a tool of some sort way to inject the infomation into the blog and set it up so it will be auto hosted.

A software maximalist would set up a drag and drop interface, you would take your screen shot run over to m$ paint, paste your screen shot, then go to you document folder and hope you find it quickly then you drag and drop into your webshit website editor.

***I will not be doing that.*** Instead I will write a bash script; to start with I need to gather up the pieces to bodge together.

----


From my last blog post the markdown syntax in hugo was
```md
![bleh](bleh.png)
```
From past knowledge I know scrot has a "click a window to screen shot it" option.

Zenity to pop up a text box.

I've been looking for a good image cropping resize tool. "pix" seems good enough, as it a) opens the image when give it from the command line and b) automaticly is happy with overwriting the file.

And something that will boop something into my copy and paste. Looking into xclip I find this syntax.
```bash
echo "hello" | xclip -selection clipboard

ctrl-v hello
```
Well thats jank but whatever **I've grabed my tools.** Time to unix them together.

---

To start with I'm going to go to my src/bash folder and touch and chmod a new file.
```bash
[monkyyy@no bash]$ touch hugoimagesyntax

[monkyyy@no bash]$ chmod +x hugoimagesyntax
```
Double checking the syntax, and that scrot tends to make png's I write
```bash
echo ![$1]($1.png)
```
which unfornately clashes with bash, five tries later I got (and a post edit to make it link correct) 
```bash
echo "!["$1"](/images/"$1".png)" | xclip -selection clipboard
```
Moving on.
```bash
[monkyyy@no bash]$ touch blogscreenshot

[monkyyy@no bash]$ chmod+x blogscreenshot

bash: chmod+x: command not found

[monkyyy@no bash]$ chmod +x blogscreenshot
```
My hugo image folder is well... I'll copy and paste that
![nemo_images_propertys](/images/nemo_images_propertys.png)

Which I will need to format to make a cd command. Next man-paging scrot:

```bash 
man scrot

SYNOPSIS
       scrot [options] [file]
       
       -s, --select
              Interactively select a window or rectangle with the mouse.  See -l and  -f
              options.
```
So I try a few things but get this
```bash
cd ~/src/hugo/content/images
scrot -s $1
```
which seems to be working correctly. So I add:
```bash
pix $1.png
```
it unfornately errors out, probaly a racing error. Adding a sleep..... and it also doesnt work.

Wait no, scrot doesnt automaticly add .png ops.

And lets end off with calling my earlier file, bring my script to this
```sh
cd ~/src/hugo/content/images
scrot -s $1.png
pix $1.png
~/src/bash/hugoimagesyntax $1
```
to finish things off I drop down to home to try to make a final command to put into my general system keybroad shortcut.

Reading thru zenitys man page
```bash
--entry
              Display text entry dialog
```
then, wrapping it in $() to make it run correctly
```bash
[monkyyy@no ~]$ ./src/bash/blogscreenshot $(zenity --entry)
```
it seems to be working so I copy and paste it into my keybindings config, skhdx, or whatever it is; you should have something simuliar, if you don't get one; running arbitary commands on a key press is very useful.
```bash
super + Print
  ./src/bash/blogscreenshot $(zenity --entry)
```
And like magic since I live in this opinionated miniumalist world, I can do something quite complex with quite a bit of automation, at any point by pushing super+printscreen.

![I_am_king](/images/I_am_king.png)

I will of course need to edit this to format it nicely and to get my numerous spelling mistakes but this is why I stay minimal. This probaly wasn't the bestm but hopefully you can get the raw bodging attitude that you should take.

