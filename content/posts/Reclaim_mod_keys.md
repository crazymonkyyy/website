
---

title: "Reclaim\_mod\_keys"

date: "2020-10-31"

draft: "false"

categories: ["linux"]

---

So you learned bash, and you set up a hotkey deamon of some sort and your ready to edit your dotfiles like a good /g/ fren to have a "productive" system.

But, all your programs use all the easy to remember hotkeys. You only have ctrl and alt and 36 keys. Are you suppose to ctrl+alt+shift+o+m to open your music player?

Whatever is a newfren to do?

![I couldn't find one with broken fingers](/images/pepehands.png)

Its simple we kill capslock and reclaim super.

Install "xmodmap" and "xcape" 

Make the following file:

```.Xmodmap```
```bash
clear lock
keycode 66 = Hyper\_R
add Mod3 = Hyper\_R
```
add these lines to your autostart script (such as bspwmrc)
```bash
xmodmap ~/.Xmodmap
xcape -e 'Super\_L=Super\_L|Shift\_L|space'
```
and rewrite your run menu keybinding to be super+shift+space (sxhkdrc)
```bash
super + shift + space 
	rofi -show && ~/.config/wallpaper.sh_
```
And you have 2 new mod keys, super and hyper. And you to can be a cool haker with 20 workspaces and a tiling wm. Btw sxhkd calls hyper "mod3".

