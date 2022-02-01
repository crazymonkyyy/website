
---

title: "Mutable\_Templates"

date: "2022-01-28"

draft: "false"

categories: ["d","dlang","programming"]

---

So a while ago I went ahead a did the impossible, irresponsible, and full initialization of my incorrigible insanity and made an [appendable alias sequence](https://github.com/crazymonkyyy/aliaslist) in d. This is not supposed to be possible. While templates are Turing complete, it is via the church lambda calculous or function style of patterns and not Turing mutability; mutability just doesn't exist, yet I made a data structure.

This blog is to document the hacks I used and to stroke my ego.

## [Counting](https://github.com/crazymonkyyy/aliaslist/blob/master/counter.d)

The sanest piece of the puzzle first: how to poke an int.

The core of this is around how `mixin("__LINE__")` behaves, alone it's nothing special, but with the `-mixin` flag, it will point at the output file, which seems to be strictly appended to.

Also, `__LINE__` in a template header will force a reinintaulaztion.

Consider this code; when its compiled with the `-mixin` flag it returns 0,1,2:

```d
import std;
template counter(){
	template access(int i){
		enum access=mixin("__LINE__");
	}
	template get_(int i,int sentinel){
		static if(access!(i)>sentinel){
			enum get_=i;
		} else {
			enum get_=get_!(i+1,sentinel);
	}}
	template get(int i=__LINE__){
		enum setty=mixin("__LINE__");
		alias get=get_!(0,setty);
	}
}
void main(){
	counter!().get!().writeln;
	counter!().get!().writeln;
	counter!().get!().writeln;
}
```


non-template version:

```d
struct mixinline_{
	int line;
	int next(){
		line+=uniform(3,100);// when -mixin is used mixin("__LINE__") only increases
		return line;
	}
}
mixinline_ mixinline;

auto access_(int i){//(should be in counter, but memoize doesnt like it)
	return mixinline.next;
}
struct counter_{
	auto access(int i){
		alias f=memoize!(access_);//templates are naturally memoized, while thats what we are attempting to break, Im using it here
		return f(i);
	}
	auto get_(int i,int sentinel){
		if(access(i)>sentinel){
			return i;
		} else {
			return get_(i+1,sentinel);
	}}
	auto get(){//i=__LINE__ is to break memoization (which may break cross file)
		return get_(0,mixinline.next);
	}
}
counter_ counter;

void main(){
	counter.get.writeln;
	counter.get.writeln;
	counter.get.writeln;
}
```

So, given a memoized function that returns a randomly increased number you can grab a sentinel, and iterate thru another memoized access, to get a clean counter.

# [Monkyyy Templates](https://github.com/crazymonkyyy/monkyyy_templates)

The time for sanity is already over, now we explicitly explore compiler bugs

A template header such as `(T, T[] data)` will work exactly once. the second time it will read data as if it's first `T`. Quite the headache to debug I assure you.

Note this may be out of spec, wrap this header like below for what actually works
```d
template foo(T,alias data){
	template foo_(T[]=data){
		
	}
	foo=foo_!(data);
}
```
But what was that "data has a spooky type from a distance"; you'd have to have some sort of manic episode to drop what you were debugging to look into turning such a bug into a feature you could explore later.

Anyway, [this helpful github project](https://github.com/crazymonkyyy/monkyyy_templates) had such a thing that cleaned the bug into an interface of sorts:
```d
struct monkyyytemplate(T){
	T payload;
	private bool ___set=false;
	T get(){
		assert(___set);// if you havnt  set it, you get cypric errors 
		return payload;
	}
	void set(T a){
		assert(!___set);// if you already set it, you will get cypric errors
		payload=a;
		___set=true;
	}
}
```

It's then straightforward to wrap it with a template that takes an int, to sort of memoizing it into an array of sorts.

## Template Folds

Templates weren't supposed to be Turing complete; why can they be?

I'm not sure about c++, but d has the "Eponymous" templates which make this pattern possible:

```d
template fold(int conditions){
	template fold_(int condictions, int acc){
		static if(condictions.ishalt){
			enum fold_=acc;
		} else {
			enum fold_=fold!(condictions.modify,acc.modify);
		}
	}
	enum fold=fold_!(condictions,acc.init);
}
```

```d
template fibonacci(int i:1){
	enum fibonacci=1;
}
template fibonacci(int i:2){
	enum fibonacci=1;
}
template fibonacci(int i){
	template f(int i,int a,int b){
		static if(i==0){
			enum f=a;
		} else {
			enum f=f!(i-1,a+b,a);
		}
	}
	enum fibonacci=f!(i-2,1,1);
}
```

I hate verbose folds, I hate this syntax, I hate that the pieces are in a different order then for loops; but its how to do heavy lifting in templates.

## [Combining The Pieces](https://github.com/crazymonkyyy/aliaslist/blob/master/aliaslist.d)

This is a truly awful hack, but by having length increase with each access, reads and writes, and filtering out the reads, you can make a correct appendable array out of these broken tools, with terrible time complexity; but I aimed to do the impossible and I did. Don't use this in production code.

Non-template code:

```d
struct mixinline_{
	int line;
	int next(){
		line+=uniform(3,100);// when -mixin is used mixin("__LINE__") only increases
		return line;
	}
}
mixinline_ mixinline;
auto access_(int i){
	return mixinline.next;
}
struct nullable(T){
	T get;
	bool has=false;
	this(T a){
		get=a;
		has=true;
	}
}
struct monkyyytemplate(T){
	T get;
	bool ___set=false;
	T get(){
		assert(___set);
		return get;
	}
	void set(T a){
		assert(!___set);
		get=a;
		___set=truse;
	}
}
struct badarray(T){
	T[] array;
	ref T opIndex(int i){
		if(i==array.length){
			array.length++;
		}
		return array[i];
	}
}
struct aliaslist{
	alias writeobject=nullable!string;//using string for a standin for types
	alias numberedmonkyyytemplate_=badarray!writeobject;
	numberedmonkyyytemplate_ numberedmonkyyytemplate;
	auto access(int i){
		alias f=memoize!(access_);//templates are naturally memoized, while thats what we are attempting to break, Im using it here
		return f(i);
	}
	auto length_(int i,int sentinel){
		if(access(i)>sentinel){
			return i;
		} else {
			return length_(i+1,sentinel);
	}}
	auto length(){//i=__LINE__ is to break memoization (which may break cross file)
		return length_(0,mixinline.next);
	}
	auto get_(int i,int j,string types){
		if(i==j){
			return types;
		} else {
			auto nmt=numberedmonkyyytemplate[i];
			if(nmt.has){
				return get_(i+1,j,types~nmt.get);
			} else {
				return get_(i+1,j,types);
			}
		}
	}
	auto get(){
		auto l=length();
		auto nmt=numberedmonkyyytemplate[l];
		//create a null in the bad array to make it possible for future reads to filter out, 
		//but mantain the length to match the counting
		return get_(0,l,[]);
	}
	auto write(string type){
		auto l=length();
		numberedmonkyyytemplate[l]=writeobject(type);
		return get_(0,l,[]);
	}
}
aliaslist mylist;
import std;
void main(){
	mylist.write("bool");
	mylist.get.writeln;
	mylist.write("int");
	mylist.get.writeln;
	mylist.write("float");
	mylist.get.writeln;
}
```