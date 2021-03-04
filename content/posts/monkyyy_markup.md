
---

title: "monkyyy\_markup"

date: "2021-03-04"

draft: "false"

categories: ["webshit"]

---

Soooo, gopher and related projects are too limited, html5 has 3d rendering which is insane, and markup by carelessly using all the symbols breaks the ability to write out Japanese emotes, or even how you write out math. And there are new desires like twitch emotes.

(ﾉ>ω<)ﾉ :｡･:\* :･ﾟ'★,｡･: \*:･ﾟ'☆

So here's a theoretical spec for what markup lang I'd make, with the following goals:

1. light on "symbol namespace" pollution

2. having color (looking at you markdown)

3. easy to write free flow without looking anything up

4. a (sane) level of expandability

----

[b] - bolds text

[i] - itatics text

[c] - crosses out text

[h1] - header

[t1] - opinionated indent level, for code formating that survives whitespace sanitizing

[\>] - quote

[^] - small expont-like text

[\*] - bulletpoint

etc.

[pepe] draws a twitch emote style Pepe(decided by a community that thinks Pepe is more important than the family emoji having 7\*7\*7 racial versions, by 3\*3\*3 gendered versions, your fucking morons unicode, open-source emotes in sprite sheets up on github somewhere). For sanity require it to be at least 4 letters and symbol-less.

[duckduckgo.com] - link

[monkyyy.science/pepe.jpg] - "resource", inlined if supported by the client, downloads to temp and opened by xdg-open when clicked otherwise.

[] - resets text drawing to baseline, i.e. "[b]bold[] not bold", not the nested shit of html

[00F] - simple rgb hexadecimal, color *hints* if its the first element in the block of text sets the background color otherwise text color, if the user has a dark theme blue would make a dark blue background, if the user had bright theme a sky blue. Details would be left up to the client but the basic assumption would be no color combo should be unreadable. Maybe allow G-Z to overflow like "200% blue"

/n - endline should also reset the styling

maybe [[] and []] for "escaped" brackets 

----

So, 1 and 2 letter codes would be for text style details, 3 letter codes would be colors, 4 and more its either an emote or a link.

