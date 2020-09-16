
---

title: "how\_should\_standard\_libs\_be\_managed"

date: "2020-09-16"

draft: "false"

categories: ["programing"]

---

So, an under appreciated feature of a lang is the std. Honestly at this point I think it could make or break a lang. Having a good std means its easy to write acceptable code from the gate.

C-style langs historically require immense effort to **render** hello world, I believe this is the singular reason webshit is winning, because the js can draw things "easily" with the js os known as chromium. While C has these whole nightmares to make a cross platform ui. Why tho?, couldn't you just have simple window rendering in the std? You probaly wouldn't want to write a game engine with an std but text drawing and simple shapes should be there.

Also there was this whole mess with python with its trasition from 2 to 3. I'm fuzzy on the details but it sounds like they over did it and assumed far to much complience.

And then D lang, whitch turn down my appication to try to improve the std, in "SAoC" and has horror storys on community managiment.

With those issues in mind, heres roughly what I would do:

1. Std writing should be trivial to get into, you can sumbit an "expmerimental" lib sith almost no approval process. The writter of that lib owns thier experimental branch and can write to it as they see fit. No bullshit about not changing it.

2. Libs have major version numbers on the libs where "std.whatever" points to the current stable version, "std.whatever.expermental" points to the raw expermental version getting live updates, with a limit of non-bug fixing updates being 6 months apart. While there is depercation, old versions of the std lib should never become unaccessable. "Import std.functions.3" should load 3rd major version of the code even if "functions" is on its 7th version. So even if there is a breaking change, you just look up the version number and append it to single lines, or if your working on something meant to be hyper stable write a style guide that requires std imports to specify the version number.

3. The std should be expansive, window rendering, several competing collections of data stuctures, the kicten sink. There should be standards of quality, but proving a general usecase should not be a thing that holds something back.

4. When theres is conflict where both sides have working code, then some sort of bureaucratic process should get involved; for example an simd xml reader thats super complient with xml version $currentminusone and a oo xml reader that adapted quickly, if **both** been written then there is a reason to have some conflict other who wrote better code and who has the std.xml namespace and you need a process to handle it(with the loser getting std.xmlnew or something). But before that point anyone anti having something in the std can fuck right off either they can choose not to use that code or get working on thier own code to prove it can be done better.

Tools should be easy to come by, and the unmoderated ecosystem with random biuld tool seems awful, and std thats a very large toolbox so you don't need an outside system should be preferred.
