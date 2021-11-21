
---

title: "petal\_function"

date: "2021-11-20"

draft: "false"

categories: ["programing","vapid"]

---

I couldn't find it under any name and had to find it via trial and error, so here is the petal function, it statelessly places the petals of a flower:

```d
float centerx=windowx/2;//dont actaully pass these, make some compile time
float centery=windowy/2;//or wrap the loop in a function
float layer=4.7;
float scale=50;
float starting=.001;
float layerdistence=.3;
Vector2 spiral(float i){
	i+=1+starting;
	float angle=(std.math.PI*2)/layer;
	return Vector2(
			sin(i*angle),
			cos(i*angle)
		)
		*log((i/layer)*layerdistence+1)
		*scale
		+Vector2(centerx,centery);
}
```

layer distance: affects how squished the inside is (.3-5.0)

![layer](/images/layerdistence.gif)

Starting: affects how far along with the "new" inner seed in along (0-1)

![layer](/images/starting.gif)

Layer: is how many points it has for rotation (4.7-7)

![layer](/images/layer.gif)