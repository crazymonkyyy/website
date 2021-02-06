
---

title: "devlog"

date: "2021-02-05"

draft: "false"

categories: ["devlog"]

---

So... I started a rewrite to organize things in my game a while ago; longer than I'm going to admit to. But it's done now, it's working on a fundamental level, with a level of organization under it.

Or to put it another way, it took months between these two screenshots:
![newscreenshot.png](/images/newscreenshot.png)
![oldscreenshot.png](/images/oldscreenshot.png)

Programing is alienating in the Marxist sense, extremely so, and I'm not sure how to deal with that. This progress doesn't feel real. Here the different file structures, so a lot did happen:

>before

```bash
├── art.png
├── bar.d
├── carts.png
├── dub.json
├── dub.selections.json
├── foo.d
├── hello
├── mix
├── PixAntiqua.ttf
├── random code
│   └── shaderattempt.d
├── raylib_cheatsheet.pdf
├── raylib-d.wiki
│   ├── Docs-(cheatsheet).md
│   └── Home.md
├── source
│   ├── app.d
│   ├── connectedcomponent.d
│   ├── draw.mix
│   ├── gameplay.mix
│   ├── group.mix
│   ├── libraylib.a
│   ├── libraylib.so
│   ├── __main-b9b3f17.o
│   ├── orecombo-60ce4ba.o
│   ├── orecombo.d
│   ├── orecombo.o
│   ├── orelist.d
│   ├── oremangiment.d
│   ├── rangematch.d
│   ├── raylib.dll
│   ├── raylib.lib
│   ├── ringarray.d
│   ├── smart2darray.d
│   ├── stable.mix
│   └── table.d
└── wave.fs
```

>after

```bash
├── art
│   ├── art1x
│   │   ├── art.png
│   │   ├── buttons.png
│   │   ├── carts2.png
│   │   ├── carts.jpeg
│   │   └── carts.png
│   ├── art2x
│   │   ├── art.png
│   │   └── buttons.png
│   ├── art5x
│   │   └── art.png
│   ├── arts sources
│   │   ├── Donate.url
│   │   ├── Facebook.url
│   │   ├── License.txt
│   │   ├── PNG
│   │   │   ├── Blue
│   │   │   │   ├── letter_A.png

│   │   │   ├── Brown
│   │   │   │   ├── letter_A.png

│   │   │   ├── Marble
│   │   │   │   ├── letter_A.png

│   │   │   ├── Metal
│   │   │   │   ├── letter_A.png

│   │   │   ├── Solid
│   │   │   │   ├── letter_A.png

│   │   │   ├── Wood
│   │   │   │   ├── letter_A.png

│   │   │   └── Yellow
│   │   │       ├── letter_A.png

│   │   ├── Preview.png
│   │   ├── Sample.png
│   │   ├── Spritesheet
│   │   │   ├── blue_spritesheet.png
│   │   │   ├── blue_spritesheet.xml
│   │   │   ├── box_spritesheet.png
│   │   │   ├── box_spritesheet.xml
│   │   │   ├── brown_spritesheet.png
│   │   │   ├── brown_spritesheet.xml
│   │   │   ├── marble_spritesheet.png
│   │   │   ├── marble_spritesheet.xml
│   │   │   ├── metal_spritesheet.png
│   │   │   ├── metal_spritesheet.xml
│   │   │   ├── solid_spritesheet.png
│   │   │   ├── solid_spritesheet.xml
│   │   │   ├── wood_spritesheet.png
│   │   │   ├── wood_spritesheet.xml
│   │   │   ├── yellow_spritesheet.png
│   │   │   └── yellow_spritesheet.xml
│   │   └── Vector
│   │       ├── lettertiles_vector.ai
│   │       ├── lettertiles_vector.svg
│   │       └── lettertiles_vector.swf
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── PixAntiqua.ttf
│   ├── raylib
│   └── source
│       ├── app.d
│       ├── artscale.mix
│       ├── imageloader.mix
│       └── initwindow.mix
├── board
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── raylib
│   └── source
│       ├── app.d
│       ├── board.mix
│       ├── fakedraw.mix
│       ├── fakeorecombo.d
│       ├── initwindow.mix
│       ├── oreque.mix
│       └── ringarray.d
├── collision
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── raylib
│   └── source
│       ├── app.d
│       └── mayomath.d
├── encyclopedia
│   ├── dub.json
│   ├── dub.selections.json
│   ├── ency
│   │   ├── foo
│   │   └── table
│   ├── mix
│   ├── raylib
│   └── source
│       ├── app.d
│       ├── app.old
│       ├── cashe.d
│       ├── eccentricexpressions.d
│       ├── encyclopedia.mix
│       ├── page_.d
│       ├── parse.d
│       └── ui.d
├── journal
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── raylib
│   └── source
│       ├── app.d
│       ├── journal.d
│       └── ui.d
├── launcher
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── out
│   ├── out2
│   ├── raylib
│   └── source
│       └── app.d
├── link
├── link2
├── link3
├── link4
├── linkart
├── link.d
├── main
│   ├── art1x
│   │   ├── art.png
│   │   ├── buttons.png
│   │   └── carts2.png
│   ├── art2x
│   │   ├── art.png
│   │   └── buttons.png
│   ├── art5x
│   │   └── art.png
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── raylib
│   ├── source
│   │   ├── app.d
│   │   ├── artscale.mix
│   │   ├── board.mix
│   │   ├── cashe.d
│   │   ├── ctfestrings.d
│   │   ├── eccentricexpressions.d
│   │   ├── encyclopedia.mix
│   │   ├── imageloader.mix
│   │   ├── initwindow.mix
│   │   ├── journal.d
│   │   ├── mayomath.d
│   │   ├── orecombo.d
│   │   ├── ore_.d
│   │   ├── oreque.mix
│   │   ├── oretable.d
│   │   ├── page_.d
│   │   ├── parse.d
│   │   ├── playfulbuttons.mix
│   │   ├── rangematch.d
│   │   ├── ringarray.d
│   │   ├── scenecontrol.mix
│   │   ├── todolist.d
│   │   ├── uglyconnectedcomponent.d
│   │   └── ui.d
│   └── todo
├── ore
│   ├── ctfestrings.d
│   ├── dub.json
│   ├── orecombo.d
│   ├── orecombo.d.old
│   ├── ore_.d
│   ├── oreque.d.old
│   ├── oretable.d
│   ├── out
│   ├── rangematch.d
│   └── uglyconnectedcomponent.d
├── particals
│   └── dub.json
├── README.md
├── scenes
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── raylib
│   └── source
│       ├── app.d
│       ├── fakebuttonsprites.mix
│       ├── fakescenedepends.mix
│       ├── mayomath.d
│       ├── playfulbuttons.mix
│       ├── scenecontrol.mix
│       └── ui.d
├── systemlist
├── template
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   └── source
│       └── app.d
├── todo
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── raylib
│   ├── source
│   │   ├── app.d
│   │   ├── cashe.d
│   │   ├── eccentricexpressions.d
│   │   ├── example
│   │   ├── example.d.dubisstupid
│   │   ├── example.o
│   │   ├── out
│   │   ├── parse.d
│   │   ├── todo
│   │   └── todolist.d
│   └── todo
├── toyui
│   ├── dub.json
│   ├── dub.selections.json
│   ├── mix
│   ├── particals
│   └── source
│       ├── app.d
│       └── ui.d
├── tree
├── ulty
└── utilityfiles
	├── cashe.d
	├── ctfestrings.d
	├── dub.json
	├── eccentricexpressions
	├── eccentricexpressions.d
	├── eccentricexpressions.o
	├── fuzz.d
	├── golbal_state.d
	├── math.d
	├── mayomath.d
	├── mix
	├── mutatetemplate.d
	├── parse.d
	├── rangematch.d
	├── ringarray.d
	├── superstate.d
	└── uglyconnectedcomponent.d
```
note there are a lot of hard links here, and I want a source control thing that manages hard links(git doesn't and everything looks hacky), if anyone has any insight