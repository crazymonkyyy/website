---

title: "tools wanted function parameters as types"

date: "2022-04-19"

draft: "false"

---

There is a cute but ultimately fragile pattern
```c
void F(int i=1,float f=4.20){}
Parameters!F Fpara=ParameterDefaults!F;
F(Fpara);
```

Your probably thinking "oh sweet I could make nice api's with this".

But... no.

If you make the types ref, you cant supply defaults. you'll get a compile error.

```c
void F(ref int i=1,float f=4.20){} 
    // Error: cannot modify constant `1`
```

If you try to use an voldemort type as a parameter, the type stops the std function from compiling
```c
void F(T)(T a,int){}
Parameters!F[1..$] Fpara;
    //template instance `std.traits.Parameters!(F)` 
    //does not match template declaration `Parameters(alias func)`
struct mylocaltype{}
F(mylocaltype,Fpara);
```

So I think its to fragile to use, often requiring extreme work arounds. And wish someone would make some tools fixing some common use cases for parameter storage.