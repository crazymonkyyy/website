
---

title: "variable\_length\_data\_words"

date: "2021-04-22"

draft: "false"

categories: ["asm speculation"]

---

There is a trade-off between efficient pointer sizes and the fundamental max data allowed by your system. You can not have more memory than pointer size X the word size, period. If you want systems with more the 8 GB of ram or whatever tiny amount of hard drive space you needed to upgrade to 64 bit, which affected the fundamental choice of your pointers. What was the consequence of that?

Well, it depends how you use the pointers, but let's meme for a bit and assume you had a doubly-linked list of bools. That is to say, you used 2 pointers and a bool to store each bool to get the magic properties of linked lists; sooooo 64\*2+1 rounded up to 8, 136 bits, to store 1 bit of data. Given that moving data to the processor is the slowest operation on the computer, this is terrible, very very terrible. Yet that's kinda the world we live in how inefficiently we use computers but I digress.

But we want to live in a world with giant ram and hard drives. Whether you're following the [call to write a new isa](https://www.youtube.com/watch?v=kZRE7HIO3vk), or making a virtual machine I would find comfy; I would suggest looking at the other side of that pointer x word size equation that's flexible; the word sizes.

We live in a post simd world, data can come in giant chunks, the 8 size word... isn't used really, like an 8-bit int is frankly rare to see, its awkward for bools, it may not run well, and when your working with a simd of 64-bit ints its a level of precision, not necessary. Could we go to 32-bit pointers and 32-bit word sizes, dropping support for 8/16 bit ints? Sure but that makes bools even more silly(and compressing bools into 32 bits would be insane bitshifting).

Leading me to my suggestion, variable-length data words; what if depending on where in the data you were a bump of the pointer moved you a different amount of data forward? A pointer at the 7th memory address was a different amount of bits away from the 8th than the 2^16th and 2^16+1th.

I would suggest 3 sizes of data, bools, 32/64 bits, and then a giant simd type let's say 8\*64. Naturally compressed bools(and bitshifting), a reasonable data size for standard computation, and then massive data for massive storage sizes and simd. That should cover all the bases.

Let's suppose you have a 16-bit pointer, a prefix of 00 means it's in the bools memory, 01 means the 64-bit memory, 11 means the 8\*64 simd; leaving you 14-bit pointers for each, how much data is that? Well, 2^14+2^14\*64+2^14(8\*64)= 9453568, or 1.18 megabytes; compared to what the simple 16-bit pointer with 8-bit words gets you of 2^16\*8=524288, 65.5 kilobytes.

I believe this complexity gets you quite a bit, lets return to that doubly linked list of bools, 16\*2+1, or 33, still terrible but less so. Maybe there be a reason to use some of these data structures with pointers if they were cheap enough.

You'd probably want to make the pointer size 32 bit and have some metadata somewhere or something, or maybe even imbalance it a little; it's kinda unclear to me how to design a fresh isa since there hasn't been one in a while but throwing this idea out there. But I'm convinced there's a good answer to the question of how to design a isa with variable length data words.

