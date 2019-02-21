# Style

### Absolute VS Relative

![bsolute & relativ](img\absolute & relative.png)



### Relative units

![elative unit](img\relative units.png)



### height VS min-height

`height:100%`

> Makes the height of the element equal to the height of the containing block. (However this could potentially be overruled, for instance if you also specified `max-height:50%`.) 

 `min-height:100%`

> If the computed height is less than 100%, in fact even if you explicitly specified a height less than 100%, it is treated as if you said `height:100%`. 
>
> Note that one key difference is that *max-height can overrule height but cannot overrule min-height*



### Position

### ![ositio](img\position.gif)



### `static` (*default*)

> won't work with any alignment style



### `relative`

> need alignment style: top, bottom, left, right



### `absolute`

> position relative to the nearest positioned ancestor. If unavailable, uses document body & align next to ancestor if no overriding style & moves along with page scrolling 
>
> "position" element is one whose position is anything except `static`

