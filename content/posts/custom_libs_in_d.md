
---

title: "custom\_libs\_in\_d"

date: "2021-08-30"

draft: "false"

categories: ["d","programming"]

---

I've been wanting it for a while but no one ever talked about how to set up, so I assumed it would be hard and kept putting it off.

It aint; it makes a near pointless file in home but... ok I've been writting alot of d.

In your home copy and paste this file:

>dmd.conf

```bash
[Environment64]
DFLAGS=-I/usr/include/dlang/dmd -L-L/usr/lib -L--export-dynamic -fPIC -I~/src/mylibs
```

Then write create files in /src/mylibs; and like magic they start working golbally.
