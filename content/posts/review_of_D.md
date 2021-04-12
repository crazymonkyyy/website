
---

title: "review\_of\_D"

date: "2021-04-12"

draft: "false"

categories: ["d","programing"]

---

So... D, I've been using it for a while and I have some opinions.

As it stands I would not suggest picking up D for metaprogramming or as your language for the next 2 decades but for your next small project with modest goals it's a maybe. This space of C replacements has several newcomers in it, D will likely be my 3rd pick at the end of the day, I don't know who wins, but it won't be the old horse, it will be one of the risky new experiments.

D as a C replacement is stable, launched, and has bindings to the c ecosystem today; BUT, its meta programming is flawed and inadequate for building new better paradigms, the compiler is buggy and that won't be changing in the foreseeable future and it fell for many of last generations memes.

pros:

1. No Cdecl needed, it has complexities(mostly 2d arrays are defined backward) but you will not need to learn the spiral method. Types are defined reading left to right.

2. Simplified templates. I own the red book, I can't read it for shit, I learned templates in D and while they are still insane and wonky, simple patterns are possible and several quality of life things were added over c++. I take that on faith since I don't and won't be learning c++ templates, but the example code I've seen is quite convincing.

3. It's stable today; this can't be overstated, most of the c replacement langs are young, and my favorite in the race, Jai hasn't shipped a compiler yet.

4. Mixins and ctfe; you can inject strings into code at compile-time and set compile-time constants with standard runtime code. Real attempts to make decent metaprogramming that's quite a bit more sane than the python/c++ meme. 

cons:

1. It's a c++ replacement not truly a c replacement. With ranges(iterators) and templates and having oo memes; the aim was off the mark, it's a related goal of course, but it's very clear there are philosophical differences here. The GC, while I don't actually care I can use big arrays of plain old structs anyway but as a feature suggests the philosophical difference that is labor not spent on fundamentals I would care about.

2. Safetyphila; there are several indefensible design choices with their explanation being preemptive safety. Why are int promoted rules fucked, safety; why is there complexity to treat a file as a string compile-time, safety; why doesn't Compile-Time Function Execution have access to the full feature set, safety; why were they thinking of mimicking rust and by default marking all code as safe(meaning lots of code I write will need to be marked unsafe verbosely), safety. Why is a lot of the std so very verbose with a few examples I know about being wildly complex and slowing down compile times when a simple 5 line block of code would do the same job, safety.

3. Poor namespace management; "__traits", like oh my god what is that shit, why are there namespace conflicts of common functions when you "import std". The std is organized ... poorly, to say the least, the functions for "I want to do functional programming now" in the suggested style are split up at least 4 places (if not 5)

4. The bug list is long, with no end in sight. I do not have the slightest hope the bugs I run into will be fixed and there are many, there are 2 extremely common bugs for delegates that kneecap any hope in using them in abusive ways. Templates and context are strange and often not worth looking into if you run into bugs; instead, you should drop the approach and attempt a different more procedural solution to the problem.

5. One arm is tied behind your back with all types of metaprogramming; whether it's safetyphila or the bugs; all the meta-programming patterns and paradigms I've looked into, have nuance that makes it not something to trust. I want my tools very sharp; templates, opoverload duck typing, "alias this" abuse, ctfe + mixins, even the suggested functional programming with std; etc. all are scratched and dented with irritating land mines ready to trip you up if you want to learn the hard way.

That's enough of a rant, hopefully, one of the new c replacements are paying attention and manage to dodge these issues, for the time being, this is a soft suggestion its probably possible to start on whatever project today in d; but avoid the Koolaid, be wildly skeptical of any claims that it all just works and plan on headaches.