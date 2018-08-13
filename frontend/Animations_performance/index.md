Animations performance
======================

Background
----------

Beautiful design and UX doesn't feel right if it's not accompanied by 60fps buttery smooth animations and scrolling. 

Going below 60fps also show inherent, sometimes hidden, issues with the JS main thread and the way we handle the DOM. Striving for smoothness helps us prevent many issues - battery performance, inability to cope with large datasets - before they impact real users.

Rules
-----

*   Develop a keen eye for 'jerkiness', non-60fps animations, etc. - and do treat this as an issue, not something to be accepted.  
    
    *   [https://developer.chrome.com/devtools/docs/rendering-settings](https://developer.chrome.com/devtools/docs/rendering-settings)  
        
*   Jerkiness / pauses are commonly caused by 3 things:  
    
    *   bad JS performance, blocking the main thread  
        
        *   [https://developers.google.com/web/tools/chrome-devtools/rendering-tools/js-execution](https://developers.google.com/web/tools/chrome-devtools/rendering-tools/js-execution)  
            
    *   unnecessary / huge repaints  
        
        *   [https://developers.google.com/web/tools/chrome-devtools/rendering-tools/](https://developers.google.com/web/tools/chrome-devtools/rendering-tools/)  
            
        *   [https://developer.chrome.com/devtools/docs/demos/too-much-layout](https://developer.chrome.com/devtools/docs/demos/too-much-layout)  
            
    *   reflow  
        
        *   [https://gist.github.com/paulirish/5d52fb081b3570c81e3a](https://gist.github.com/paulirish/5d52fb081b3570c81e3a)  
            
*   Try to measure performance using RAIL model  
    
    *   [https://developers.google.com/web/fundamentals/performance/rail](https://developers.google.com/web/fundamentals/performance/rail)  
        

How to create smooth animations?
--------------------------------

In order to make smooth animations you need to remember one important thing - no matter how complex is your animation, you need to do it under ~16ms. This is not a long time to do all your stuff, so keep your animation optimised as much as possible.

### Understand the Event Loop

JavaScript is very different from other language you might know. This affects animations greatly, and the main reason for this is - the event loop. Ever wondered why Promises and Callback Hell is something that only happens in JS? That's the reason.

These are enough to get you started:

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)

[https://medium.com/front-end-hacking/javascript-event-loop-explained-4cd26af121d4](https://medium.com/front-end-hacking/javascript-event-loop-explained-4cd26af121d4)

### Animation types

Whenever you start coding animation, first thing you need to do is to define a right tool for the job. The most general types of animation are complex and simple animation.

**Simple animation** \- basic motion, often triggered by pointer event like _hover_

**Complex animation** \- combination of several tweens, usually joined as one scenario

The rule of thumb is to use CSS transitions / animations for **simple animations** and use JavaScript (mostly along with animation library like [GSAP](https://greensock.com/gsap) or [animejs](http://animejs.com/)) for **complex animations**.

### Avoid repaints and reflows

Mostly it doesn't matter if you animation is a **simple** or **complex** one. What matters it that if it triggers repaints or reflows.

**Reflow (layout)**

> Layout (or reflow in Firefox) is the process by which the browser calculates the positions and sizes of all the elements on a page.

**Repaint**

> Paint is the process of filling in pixels. It is often the most costly part of the rendering process. If you've noticed that your page is janky in any way, it's likely that you have paint problems.

If you have any problems with animation performance, it's highly possible that your animations cause repaints or reflows. To check what properties can trigger these phases, we suggest you to take a look a super-handy [CSS Triggers](https://csstriggers.com/) site.

### Using FLIP technique

There is one helpful trick that you can use to improve your animations' performance. It's called FLIP, which stands for First, Last, Invert, Play. This technique simply puts the computation phase at the animation's beginning, so all the jerkiness-possible stuff is done at the bootstrap.

**First** 

> the initial state of the element(s) involved in the transition.

**Last**

> the final state of the element(s).

**Invert**

> here’s the fun bit. You figure out from the first and last how the element has changed, so – say – its width, height, opacity. Next you apply `transforms` and `opacity` changes to reverse, or invert, them. If the element has moved 90px down between First and Last, you would apply a transform of -90px in Y. This makes the elements appear as though they’re still in the First position but, crucially, they’re not.

**Play**

> switch on transitions for any of the properties you changed, and then remove the inversion changes. Because the element or elements are in their final position removing the transforms and opacities will ease them from their faux First position, out to the Last position.

More about FLIP you can find [here](https://aerotwist.com/blog/flip-your-animations/).