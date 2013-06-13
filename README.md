# [minimit-anima](http://www.minimit.com/projects/code/minimit-anima)

**Hardware accelerated css3 animations with fallback for older browsers.**

It's built to have fast animation execution and it has an Api very similar to Jquery animate.

By default the anima method do **automatic fallback animation** on browsers without transitions or transform3d, and **instant animation** on browser without transforms.

It also does scale, rotate and skew animations on browsers without transitions thanks to <a href="https://github.com/louisremi/jquery.transform.js" target="_blank">jquery.transform.js</a> included in the plugin.

My website [minimit.com](http://www.minimit.com) and my twitter [@beaver82minimit](http://twitter.com/beaver82minimit)

Api
-------

Use the **anima** method to have automatic fallback:

``` javascript
anima(properties:object, duration:number, easing:string, options:object);
```

Use the **anima2d** method to execute animations only on browsers without transitions or transform3d:

``` javascript
anima2d(properties:object, duration:number, easing:string, options:object);
```

Use the **anima3d** method to execute animations only on browser with transitions or transform3d:

``` javascript
anima3d(properties:object, duration:number, easing:string, options:object);
```

Use the respective **stopAnima** method to stop animations:

``` javascript
stopAnima(clearQueue:boolean, jumpToEnd:boolean);
stopAnima2d(clearQueue:boolean, jumpToEnd:boolean);
stopAnima3d(clearQueue:boolean, jumpToEnd:boolean);
```

Use the respective **delayAnima** method to delay animations:

``` javascript
delayAnima(time:number);
delayAnima2d(time:number);
delayAnima3d(time:number);
```

Use the respective **clearAnima** method to clear the queue:

``` javascript
clearAnima();
delayAnima2d();
delayAnima3d();
```

Parameters
-------

The properties you can animate can be:
* **any css**, use string if it's not a valid javascript variable like {"margin-top":500}
* **any transform**, like x, y, z, skew, skewX, skewY, scale, scaleX, scaleY, scaleZ, rotate, rotateX, rotateY, rotateZ, perspective

The easing property can be:
* a **custom bezier**, you can make your own at [cubic-bezier.com](http://cubic-bezier.com).
* a **preset**, like linear, ease, easeIn, easeOut, easeInOut, easeInQuad, easeInCubic, easeInQuart, easeInQuint, easeInSine, easeInExpo, easeInCirc, easeInBack, easeOutQuad, easeOutCubic, easeOutQuart, easeOutQuint, easeOutSine, easeOutExpo, easeOutCirc, easeOutBack, easeInOutQuad, easeInOutCubic, easeInOutQuart, easeInOutQuint, easeInOutSine, easeInOutExpo, easeInOutCirc, easeInOutBack

Instant animations are default:

- $(this).anima({x:10});

Default easing is "ease":

``` javascript
$(this).anima({x:10}, 400);
```

Custom easing is a bezier string:

``` javascript
$(this).anima({x:10}, 400, ".19,1,.22,1");
```

You can set a function to execute on animation completed:

``` javascript
$(this).anima({x:10}, 400, ".19,1,.22,1", {complete:function(){alert("done")}});
```

You can skip automatic fallback animations

``` javascript
$(this).anima({x:10}, 400, ".19,1,.22,1", {skipNoSupport:true, skipPartialSupport:true});
```

Examples
-------

###Translate

Use **x** , **y**, or **z** property:

``` javascript
$(this).anima({x:10, y:10});
```

###Scale

You can use scale, scaleX, scaleY or scaleZ
``` javascript
$(this).anima({scaleX:0.8, scaleY:0.8}, 400);
```

``` javascript
$(".mydivs").anima({x:100}); // instant animation of transformX
$(".mydivs").anima({scale:0.8}, 800, ".19,1,.22,1"); // animation of scale with duration and custom easing
$(".mydivs").anima({"margin-top":500}, 200, ".19,1,.22,1", {complete:function(){$(this).css("display","none");}}); // example with css property animation and complete function
$(".mydivs").anima3d({x:200}, 800).anima2d({x:100}, 800); // different animations based on browser support of transition and transform3d
$(".mydivs").anima({x:200}, 800, "linear", {skipNoSupport:true}); // skip the animation on browser without transform support
$(".mydivs").delayAnima(200).anima({x:100}); // delay anima animations
$(".mydivs").stopAnima(); // stop all anima animations
$(".mydivs").clearAnima(); // stop all anima delays
```

License
-------
Copyright © 2013 Riccardo Caroli. Licensed under [MIT license](http://www.opensource.org/licenses/mit-license.php).

