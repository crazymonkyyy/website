
---

title: "shower\_algorithm"

date: "2021-03-21"

draft: "false"

categories: ["programing"]

---

So a few days ago an algorithm for k-largest came to me in the shower and I've been having migraines thinking about the problem since.

1. It started as:

2. take a sample of the array

3. deduce the shape of the array

4. compile a pivot function

5. based on that pivot function, move elements to the front of the array getting a smaller array

6. repeat

I was literally considering writing jit asm to make that pivot function for a while during migraines. I highly don't recommend this sort of process, very not fun.

anyway I eventually settled on a different algorithm that is correct and sane

1. do a radix count

2. process the radix count array to get a pivot number of which digit contains k

3. run thru the array with radix function and filter elements that equal the pivot number to the front of the array and numbers under the pivot number to an output array

4. repeat on the smaller slice with the next radix function

There are more details to make it work and [it does work](https://github.com/crazymonkyyy/radix/blob/master/radixksmallest.d); but.... it isn't faster than the existing algorithm its ties with the pivot-based algorithm in d's std. (I'm literally crying rn, sadpepe.jpg)

The reasoning why it seems to tie would be that while my code should decrease the problem by 1/256(for the unaware the standard size for radix digits once optimized, so for 64-bit numbers, you have 4 iterations) it does touch the data twice, while the pivot based algorithm decreases the code in half each iteration and to be sloppy math 1 + 1/2 + 1/4... does equal 2; so yes roughly the same, if you assume that the problem is decreased by 1/256, is trivial and ignorable; which.... yeah.

(again literally crying; hold me... why wasn't I just magically smarter than everyone else with a few days of thinking with migraines)

But, I have a differently working code for the problem, and I'm imagining ways that maybe are loose on correctness but do work on the insight that a radix digit+number is a good discriminator function

What happens if do a random sample of the array with radix digits and process the count array of this sample with a heuristic of some kind? Assuming I'm ok with being loose on correctness, I could touch the majority of data once, but the complexities of recursive algorithms with template messes made writing the last version hard so I want some outside advice and thoughts on the matter if only to clarify my thoughts into something sane.

What are some known ways to manage multi streams of data as you filtering? If you're discarding down data it's possible to have nice space complicity, with radix you can sort nicely; but inbetween seems kinda a mess, the radix sort depends on perfect knowledge of counts as far as I'm aware.

Anyway enough rambling, if anyone has any thoughts wherever my email at monkyyy@cocaine.ninja if you don't know me someway else.
