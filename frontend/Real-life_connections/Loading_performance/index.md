Loading performance
===================

Background
----------

Fast application is not only working smoothly during user interaction, but also loads quickly. This means that you should care about how fast your application can be used by user at first time, he enters your website.

There are couple of key metric that you should be aware of:

*   First Paint - user sees first element on your website  
    
*   First Contentful Paint - user sees first content on your website (article, photo, etc.)  
    
*   First Meaningful Paint - user sees [app shell](https://developers.google.com/web/fundamentals/architecture/app-shell) (whole layout of your application)  
    
*   First Interactive / Time to Interactive - user can interact with your application  
    

More about user-centric performance metrics you can read [here](https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics#tracking_fpfcp).

Rules
-----

*   Keep your assets as small as possible  
    
    *   Minify scripts, styles, images, etc.  
        
    *   Load images prepared for certain devices  
        
*   Optimize assets loading time  
    
    *   Use Cache-Control header on server side - [reference](https://developers.google.com/web/fundamentals/performance/get-started/httpcaching-6)  
        
    *   Use Service Workers or App Cache on front-end side  
        
*   Prefer lazy loading over eager loading (loading everything at the application boot) - [reference](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/)  
    
*   Remove all initial render blockers  
    
    *   Mostly external scripts / stylesheets placed in <head />  
        
*   Inline [Critical CSS](https://www.smashingmagazine.com/2015/08/understanding-critical-css/) styles  
    
*   Inline critical SVG graphics  
    

How to measure performance of your app?
---------------------------------------

We recommend using Lighthouse, which makes audit of your website using different tools. It checks performance, accessibility and compatibility with PWA pattern. More about it you can read [here](https://developers.google.com/web/tools/lighthouse/).

Beside Lighthouse, you should definitely use your favourite browser's dev tools. In Chrome you have access to different tools like:

*   [Performance panel](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/)  
    
*   [Network panel](https://developers.google.com/web/tools/chrome-devtools/network-performance/)  
    
*   [Memory panel](https://developers.google.com/web/tools/chrome-devtools/memory-problems/heap-snapshots)  
    

There are other great tools for measuring performance of your application, which you can find in [this article](https://developers.google.com/web/fundamentals/performance/speed-tools/).

What you can do to improve loading time?
----------------------------------------

### Minification

When you see that your application is loading slowly, first thing you need to do it to check if assets are correctly optimised. There are couple ways how you can do it:

*   Minify your [scripts](https://webpack.js.org/guides/production/#minification) and [styles](https://github.com/webpack-contrib/css-loader#minimize) (using Webpack)  
    
*   [Optimise you images](Image_Video_optimization/index.md)  
    
    *   you can use [ImageminPlugin](https://github.com/Klathmon/imagemin-webpack-plugin) for Webpack  
        

### Caching

You have your assets optimised, but still you website can load slowly, especially during next reloads. There is one thing that you need to remember - never load the same resource twice. By “the same” we mean, resource that is not changed over time. That's why you need to leverage browser caching.

Here are some tips how you can do it:

*   Use Cache-Control header on server side - see [this article](https://jakearchibald.com/2016/caching-best-practices/)  
    
*   Cache files on client with Service Worker - see [this article](https://developers.google.com/web/ilt/pwa/caching-files-with-service-worker)  
    

More about caching you can find [here](https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook/).

### Lazy loading

Lastly, it's good to load only required assets. Imagine that you build huge application. You definitely don't want to load all assets at the first load. It's better to lazy load them.

You can lazy load images, styles, scripts and any other files. Here are tools which you can use:

*   scripts - [Code splitting in Webpack](https://webpack.js.org/guides/code-splitting/)  
    
*   styles - [Critical CSS tool](https://github.com/addyosmani/critical)  
    
*   images - [lazyload library](https://github.com/verlok/lazyload)  
    

### PRPL pattern

[PRPL](https://developers.google.com/web/fundamentals/performance/prpl-pattern/) is a pattern for structuring and serving Progressive Web Apps (PWAs), with an emphasis on the performance of app delivery and launch. It stands for:

    **Push** critical resources for the initial URL route.  
    
    **Render** initial route.  
    
    **Pre-cache** remaining routes.  
    
    **Lazy-load** and create remaining routes on demand.