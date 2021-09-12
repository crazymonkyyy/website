
---

title: "playing\_with\_dimensions"

date: "2021-09-11"

draft: "false"

categories: ["programing","5d"]

---

So, a while ago I made a little demo of a 5d space ["game"](https://github.com/crazymonkyyy/5d_space_prototype). I'm pretty sure it would be a dead-end, "warheads" that lovely game that I found in a bargain bin for 1$ as a child isn't exactly well known, turn-based space combat with destructive planets didn't exactly stick, and 5d chess failed to communicate how it appended the rules to people to any practical degree. So taking a not all that well-known and loved genre of game and appending something that massively limits player bases to the point you can't find a game.

But nonetheless, my brain has been thinking about dimensions and I have an opinion.

I believe people think about dimensions wrong when it comes to video games, it's purely an int, and it's about the game world not the user control of it. For a simple example, consider tic tac toe vs connect 4, both are 2d worlds with a similar premise, but I would not say that connect 4 is 2d, the user input is 1d, with a \*flavorful\* additional d.

Dimensions with a flavor? Well sure, when was the last time you played a full 3d shooter, by which I mean one where you can walk on ceilings and your spinning around? Your relationship with up and down is extremely different from left and right. Games, where you fly a spaceship, tend to add giant props to act as a ground, or be largely empty and has an in-game computer tell you how to function. You function with 2d and a small state for your height off the ground, no different from "flying" enemies in a tower defense game, which is just a bool if they ignore collision. Even if you learn to fly, you will likely maintain a very very distinct relationship with the ground and your height is a decreasing resource/liability that ties in with your sense of time.

So what are some flavors of dimensions:

gravity, obviously, whether this is gravity, or say an auto-runner, gravity makes an infinite void, into a resource to be managed. In 5d chess, both time travel and multi-dimensional timelines acted as a precious resource. There are 2 main speeds in gravity dimensions, managing to stay still, or falling.

Spooky quantumy, in games such braid or puzzle games with a clone, your creating spooky ghosties that go do things while you do a constructive action that interferes. This makes objective reality change based on your opinion of what's more useful at the time. There also fez and that 3d paper Mario where the "depth" dimension would flatten and while you couldn't see it, things which were infinitely thin would be thicc; and really isn't spooky ghosts about things which may ignore walls. It seems to me, it's all conditional collision.

Portals. Hey, hey, did you know this unknown videogame portal made a non-euclidian space a thing?

Hyperbolic..... Outside of that one rouge game, I don't know of a released game of any note. Maybe it should be explored, by someone who knows how to manage that data struct on a basic level(I don't)

Others?

-----

So what's a dimension anyway? It's a single point of data that a player can intimately affect that hopefully, you made a whole lot of complexity to justify the player learning it. 5d chess didn't at a competitive level, time travel is either a winning move or wasted, my 5d space battle would have been two more sliders to the gravity aiming while making my code that much harder to make interesting weapons in, like say the extreme weapons in worms or warheads.

Why does it seem so easy to make a case that games shouldn't have time travel when as a concept it's generally adored and it is likely to have complex interactions with game theory?

I don't see any formal reason time travel must be either an endless space of pointlessness or necessarily so expensive to be not worth whatever complexity, but I can't imagine a multiplayer game capable of doing anything with it unless time is hyperbolic... somehow. Also just how do hyperbolic dimensions work, give me a 1d example, it completely eludes me.

