
---

title: "web\_is\_bloat\_what\_would\_I\_do"

date: "2020-09-10"

draft: "false"

categories: ["programing"]

---

The webshit is webshit, I imagine anyone who manages to find this blog will agree that the socail media web is bad or is a "systems" programmer who looks at webshit with disgust; so not going into detail, so what would I replace it with?

I see 3 main tasks as part of the web:

1. Layout

2. Rich text with a focus on links

3. Generic system aided user messages

(I would add a 4th, a flash replacement, but that would be another rant.)

Html only managed the 2nd, and the first historically was a nightmare, poeple had space partition trees in thier mind for so long; **my** wm is "Binary Space Partition Window Manager" and let me tell you, poeple don't think in 1.5d trees they think about layout in grids I like tiling wm's but its still jank. And to my knowlegde no one has solved the thrid problem cleanly.

Layout
---

So, layout is futher sub divided into 2 parts, grid defination and grid coloring.

If you give poeple enough dials in your grid layout they can compose websites that most poeple find pleasing, whether thats think  margins, and collection of images, having a logo at the top corner and a wall of text, whatever. Trational html defined "frames" which are like the space trees; don't, learn from that mistake. You grab a list of 95% of the definations of css grids poeple ussally poke and allow poeple to define it as the header of the web page. Oh and have muliple for different screen sizes.

Followed by that header is a grid coloring; even if humans think in grids they do this silly thing where they will define content as being bigger then a single grid cell; so you have an n by m 2d array of lets say 8 length strings which will "color" the boxes. The strings link to a block of text below and boxes that share a "color" are touching are combined.

Rich text
---
Markdown is pretty good. The links are a bit of a strange choice but you have blocks of text that is markdown.

Oh and color hints; not color definations; thats a topic I'm not super on top of but color multiplication is possible, so the user would have thier system theme that has a list of colors, a dark theme would have white text on black and light theme would have black text on white, a web site could ask that thier background is more blue and broswer would make a dark blue for the dark theme and a light blue for the blinding theme via some sort of color muliplier.

So you have a header of the name of the content for the layout, some color hints, with a block of text of probaly an expanded markdown; like my blog is generated from markdown, its functional.

Lets say when injecting an image or a video in markdown that the file type determines what subsystem renders it.

System aided user messages
---

So this is the tricky bit, defining the 2 way communication; this would also go into the grid coloring system. And some heading.

Fundmentally what a pizza site is doing with its layers and layers of js is asking you for an order and some bank info; this is a message. And users are not going to be learning its internal data system and would be very upset if they moved things around during a refactor.

I'd point at zenity (it creates popup windows for bash scripts, like files manager, calenders etc.), and some posix. You have some posix syntax to generate a file with some user help and a system of envermental varibles like say $VISAID, and it will generate and send a text file according to some spefication when the user hits send.

"Makepiza" of the pizza website could append $temporderdetails while "checkout" could be something like, encypt(pizzasitekey,$temporderdetails $VISAID userinput --tip "20.00 usd")

