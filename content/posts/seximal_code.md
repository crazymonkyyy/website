
---

title: "seximal\_code"

date: "2021-06-23"

draft: "false"

categories: ["d","programming"]

---

Code used to generate stuff for my next post

```d
struct sexy(T:int){
	T i; alias i this;
	dchar digit(T j){
		enum dchar zero='☐';
		enum dchar one='⚀';
		assert(j>=0 && j<=6);
		if(j==0){ return zero;}
		return one+(j-1);
	}
	dstring toString(){
		auto j=i;
		dstring out_;
		bool neg= j<0;
		if(j<0){j=-j;}
		while(j!=0){
			out_=digit(j%6)~out_;
			j=j/6;
		}
		if(out_.length==0){return [digit(0)];}
		return out_;
	}
}
alias sint=sexy!int;
unittest{
	import std;
	writeln(sint().digit(0));
	foreach(i;1..100){
		writeln(sint(i));
	}
}
void main(){
	import std;
	foreach(i; 0..36){
		auto f(T)(T a){
			if(a.length==1){a=" "~a;}
			return a;
		}
		write(f(sint(i).to!string),":",f(i.to!string),",");
		if(i%6==5){writeln;}
	}
	"times".writeln;
	foreach(i; 0..36){
		write(sint((i%6)*(i/6)),",");
		if(i%6==5){writeln;}
	}
	"mods".writeln;
	foreach(i; 0..36){
		write(sint(i),":");
	foreach(j;2..7){
		write(sint(i%j),",");
		}
		writeln;
	}
}
```
