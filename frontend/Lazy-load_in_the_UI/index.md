Lazy-load in the UI
===================

Background
----------

To fulfill our requirements for data handling all UI components need to be ready to lazy-load content, even if application doesn't call for it (e.g. because the data is always there - will it be, always? nope). 

It's for a simple reason - whether the data should be fetched, refetched or served from cache is not a decision that should be made by the UI component. It belongs to the persistence layer.

Now - if your component is ready to lazy load content - it'll be robust enough to handle all the other async scenarios too, for free - e.g. background changes to the object, action failure scenarios - the lot.

Rules
-----

*   Component is lazy-loading ready, when:  
    
    *   it calls for the persistence layer to fetch the object when it's shown  
        
    *   it handles all entity loading / error states  
        
    *   it shows updated content when the entity updated in the background - not just this once, but always  
        
        *   exception - 'edit' components - they should resolve conflicts as well as update the changes  
            
*   Lazy-load and create remaining routes on demand (_L_ from [PRPL pattern](https://developers.google.com/web/fundamentals/performance/prpl-pattern/))  
    

How to test this behavior?
--------------------------

Check your component's behavior when the entity is changed by another component on the screen. If an entity is marked as stale by another component - will it show new content? Test the loading state and the error handling.

How to preload routes on demand?
--------------------------------

The first load of your application is significant. Ideally, during this 2-3 seconds, you need to keep the user on your site, so it's better to load the content fast. In case of small applications, this seems to be an easy task, but what happens, when your application's size increases? It's good to keep things small. Remember, 100kb of JavaScript isn't the same as 100kb of JPEG image.

To reduce the [cost of your JavaScript](https://medium.com/dev-channel/the-cost-of-javascript-84009f51e99e), split your code into several chunks and load them, when necessary. You have plenty of tools, which can help you with it. With Webpack, you can use [dynamic imports](https://webpack.js.org/guides/code-splitting/#dynamic-imports). In React with React Router, you can [load components on demand](https://reactjs.org/docs/code-splitting.html).