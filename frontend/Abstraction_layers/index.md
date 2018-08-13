Abstraction layers
==================

Background
----------

Having too little abstraction layers cause the whole code to be one-off, not reusable, and not able to adhere to the 'single responsibility rule'.

Having too many causes unnecessary code to be written - at the same time this code is usually boilerplate, and quick to write - making this a much smaller problem than having too little layers.

Rules
-----

*   [Keep your UI, logic and data layers separate.](UI_logic_data_layers/index.md)  
    
*   Favor abstractions:  
    
    *   where components tend to evolve quickly during project ramp-up, e.g:  
        
        *   HTTP fetching layer (fetch through own abstraction, rather than straight through axios / etc.) - unless it's already abstracted away (per Angular > 2) - for global control of automatic retries, exceptions abstraction, etc.  
            
        *   Authentication logic - as it tends to evolve a lot with sudden ACLs / changed behavior / added opt-ins / popups, etc.  
            
    *   where components might be replaced (API calls)  
        
    *   where logic seems a bit too complex  
        
*   Always write interfaces, and make sure to never rely on private / protected methods and properties.  
    

How to test
-----------

*   Think of your code from a perspective of someone who has no idea about the codebase and needs to:  
    
    *   add a feature  
        
        *   will he be able to do that without knowing current implementation details?  
            
    *   change behavior of a feature  
        
        *   will he be able to do that in one place  
            
            *    is it easily findable?  
                
        *   are there any quirks that need to be known?  
            
    *   change the way e.g. data is being returned from the API (e.g. from one endpoint to having to hit 2 endpoints and combine the results)  
        
        *   does it require a change in any components that use this data?  
            
        *   is it easily implementable in one place