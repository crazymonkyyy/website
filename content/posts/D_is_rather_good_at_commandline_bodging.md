
---

title: "D\_is\_rather\_good\_at\_commandline\_bodging"

date: "2020-08-26"

draft: "false"

categories: ['D']

---

I have not seen this written down anywhere, and the pieces are seperated in the documation; But I assume it took effort to make pieces of this to work apperently correctly and comfy.

Taking command line input:
-----
```d
void main(string[] s){
```
Besides element 0 being the command for posix reasons; its rather staight forward, your input is whatever you named s.

running commands:
----
```d
import std.process;
string userinput=executeShell("zenity --entry"); 
```
Zenity pops up a window for the user to input something into, so these two lines of code will do the rather complicated thing of getting a string from the user, assuming its installed and not vomiting gtk warnings.
Read the fucking manual for bash tools and all that jazz.


Reading files lazily:
----

A bit more complicated, but you can read and write to files without any sort of hassle with the following pattern.

>in data.d
```d
struct mystruct{
  int i;
  float f;
  bool b;
}
```

>in foo.d

```d
import data;
import std.file;
void main(){
  mystruct a=mystruct(
    42,
    1337.0,
    true,
  );
  //import std.process; executeShell("touch store");
  write("store",[a]);
}
```

>in bar.d

```d
import data;
import std.file;
void main(){
  mystruct a;
  if(exists("store")){
    a=(cast(  mystruct[]  )read("store"))[0];
  }
  assert(a.i==42);
  assert(a.f==1337.0);
  assert(a.b==true);
  import std.stdio; "success".writeln;
}
```

I mean you could read in files as intended but do you really want to do that?

