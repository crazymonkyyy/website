
---

title: "dice\_seximal"

date: "2021-06-23"

draft: "false"

categories: ["seximal","vapid ranting"]

---

I believe seximal should be taught to children. You can finger count to 36 easily, and the time's tables are fairly small and you could probably start teaching them to preschoolers in a way I don't think the 12 by 12 one could be, 6 is an anti-prime. Modulus and division as concepts should also be smaller to get it into the minds of children earlier. And maybe you could use dice in classrooms for math while children are still struggling with writing.

But there should be a standard for the digits so there's clarity, and I suggest dice faces; they are in Unicode already and they should scream 6-ness to even the unaware, who may need to reverse engineer what they are looking at without resources.

(altho, it is kinda small in normal fonts)

## to base ten
``` bash
 ☐: 0,   ⚀: 1,   ⚁: 2,   ⚂: 3,   ⚃: 4,   ⚄: 5,
⚀☐: 6,  ⚀⚀: 7,  ⚀⚁: 8,  ⚀⚂: 9,  ⚀⚃:10,  ⚀⚄:11
⚁☐:12,  ⚁⚀:13,  ⚁⚁:14,  ⚁⚂:15,  ⚁⚃:16,  ⚁⚄:17
⚂☐:18,  ⚂⚀:19,  ⚂⚁:20,  ⚂⚂:21,  ⚂⚃:22,  ⚂⚄:23
⚃☐:24,  ⚃⚀:25,  ⚃⚁:26,  ⚃⚂:27,  ⚃⚃:28,  ⚃⚄:29
⚄☐:30,  ⚄⚀:31,  ⚄⚁:32,  ⚄⚂:33,  ⚄⚃:34,  ⚄⚄:35
```

## simple times table
``` bash
  ⚀  ⚁  ⚂  ⚃  ⚄ 
 ┏━━━━━━━━━━━━━━━
⚀┃ ⚀, ⚁, ⚂, ⚃, ⚄
⚁┃ ⚁, ⚃,⚀☐,⚀⚁,⚀⚃
⚂┃ ⚂,⚀☐,⚀⚂,⚁☐,⚁⚂
⚃┃ ⚃,⚀⚁,⚁☐,⚁⚃,⚂⚁
⚄┃ ⚄,⚀⚃,⚁⚂,⚂⚁,⚃⚀
```
## mod tables
```bash
   ⚁,⚂,⚀,⚄,⚀☐
  ┏━━━━━━━━━━
 ⚀┃⚀,⚀,⚀,⚀,⚀
 ⚁┃☐,⚁,⚁,⚁,⚁
 ⚂┃⚀,☐,⚂,⚂,⚂
 ⚃┃☐,⚀,☐,⚃,⚃
 ⚄┃⚀,⚁,⚀,☐,⚄
⚀☐┃☐,☐,⚁,⚀,☐
⚀⚀┃⚀,⚀,⚂,⚁,⚀
⚀⚁┃☐,⚁,☐,⚂,⚁
⚀⚂┃⚀,☐,⚀,⚃,⚂
⚀⚃┃☐,⚀,⚁,☐,⚃
⚀⚄┃⚀,⚁,⚂,⚀,⚄
⚁☐┃☐,☐,☐,⚁,☐
⚁⚀┃⚀,⚀,⚀,⚂,⚀
⚁⚁┃☐,⚁,⚁,⚃,⚁
⚁⚂┃⚀,☐,⚂,☐,⚂
⚁⚃┃☐,⚀,☐,⚀,⚃
⚁⚄┃⚀,⚁,⚀,⚁,⚄
⚂☐┃☐,☐,⚁,⚂,☐
⚂⚀┃⚀,⚀,⚂,⚃,⚀
⚂⚁┃☐,⚁,☐,☐,⚁
⚂⚂┃⚀,☐,⚀,⚀,⚂
⚂⚃┃☐,⚀,⚁,⚁,⚃
⚂⚄┃⚀,⚁,⚂,⚂,⚄
⚃☐┃☐,☐,☐,⚃,☐
⚃⚀┃⚀,⚀,⚀,☐,⚀
⚃⚁┃☐,⚁,⚁,⚀,⚁
⚃⚂┃⚀,☐,⚂,⚁,⚂
⚃⚃┃☐,⚀,☐,⚂,⚃
⚃⚄┃⚀,⚁,⚀,⚃,⚄
⚄☐┃☐,☐,⚁,☐,☐
⚄⚀┃⚀,⚀,⚂,⚀,⚀
⚄⚁┃☐,⚁,☐,⚁,⚁
⚄⚂┃⚀,☐,⚀,⚂,⚂
⚄⚃┃☐,⚀,⚁,⚃,⚃
⚄⚄┃⚀,⚁,⚂,☐,⚄
