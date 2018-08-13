Real-life connections
=====================

Background
----------

Majority of people use internet on their mobiles (2018). This behavioral change impacts everything we're doing on the frontend side. 

Facts:

*   LTE is a horrible connection type  
    
*   not all requests go through  
    
*   speed is not consistent  
    
*   connection might be offline one second and online the next second  
    
*   not all responses come through, even though the request actually worked  
    
*   backends might be busy one second, and absolutely fine the next one  
    
*   LTE works 3x worse outside of Poland, we're lucky :-)  
    

Our stance:

*   We accept these facts as facts of life  
    
*   We craft our applications in a way that users are not impacted by these facts - we are, they are not  
    
*   Users should be able to use our applications in the subway, while driving, because that's what they do  
    
*   Users should always know what's going on  
    
*   Users don't care about technology - they want to get something done  
    
*   Users must not be guinea pigs - they must not be the first  to test e.g. how the app behaves   
    

Rules
-----

### UI / UX

*   Loading state is communicated at all times.  
    
    *   all async. actions progress is communicated  
        
        *   [https://semantic-ui.com/elements/button.html#loading](https://semantic-ui.com/elements/button.html#loading)  
            
    *   we minimize layout changes between empty state, loading state, error state and 'fully loaded content' state  
        
        *   [https://semantic-ui.com/elements/segment.html#segment](https://semantic-ui.com/elements/segment.html#segment)  
            
*   App is usable on a bad connection  
    
    *   we automatically retry idempotent requests that failed  
        
        *   with a timeout  
            
        *   with no response  
            
        *   with non-critical error (like 5xx status code class)  
            
        *   example implementation:  
            
            *   [https://github.com/SwingDev/blz-web-app/blob/master/client/utils/axiosAutoRetry.js](https://github.com/SwingDev/blz-web-app/blob/master/client/utils/axiosAutoRetry.js)  
                [https://github.com/SwingDev/blz-web-app/blob/master/client/services/categories.js](https://github.com/SwingDev/blz-web-app/blob/master/client/services/categories.js)  
                
    *   we communicate critical errors in a meaningful way and give users the ability to do something about it - like retry the same action  
        
*   We interpret errors properly, examples:  
    
    *   404 on a DELETE request is not an error, expected state does match the facts → object does not exist  
        
    *   410 Conflict on a PUT is not an error if the response matches the request  
        
    *   think about different scenarios :-)  
        

### Development

*   We develop with link throttling enabled in the browser - as next to no users have a fiber optics internet connection:  
    
    *   [https://developers.google.com/web/tools/chrome-devtools/network-performance/network-conditions](https://developers.google.com/web/tools/chrome-devtools/network-performance/network-conditions)  
        
*   Use throttling to simulate average devices performance  
    
    *   [https://umaar.com/dev-tips/88-cpu-throttling/](https://umaar.com/dev-tips/88-cpu-throttling/)  
        
*   We develop using a variety of user accounts:  
    
    *   with content  
        
        *   some  
            
        *   a lot  
            
    *   without content - try being a new user once in a while, they make the application grow, we care about them :-)  
        
*   We test error handling at all times:  
    
    *   try accessing a resource that was deleted in a different tab  
        
    *   try killing your wifi and going through the application → that's the best simulation of a user using public transport :-)  
        
*   Leverage caching in your application  
    
    *   Use application cache  
        
    *   Use [browser cache](Loading_performance/index.md)