UI / logic / data layers
========================

Background
----------

Good layer separation allows for:

*   Reuse of components  
    
*   Single-file, single-place changes of: ui, logic, behavior and api  
    
*   No regressions  
    

Rules
-----

### UI layer - Dumb Components

Do:

*   take data, produce UI  
    
*   take input, produce actions  
    
*   orchestrate micro-level behavior in the UI realm (e.g. an input field logic)  
    
*   initiate data layer / services layer data fetch if data unavailable  
    
*   handle loading state of the data layer / loading state of the data action  
    
*   handle failure state of the data layer / failure of data action  
    

Do not do anything else, for instance:

*   Fetch data  
    
*   Orchestrate application logic / flow  
    

### Logic layer - Smart components / Services / Actions / Controllers

Do:

*   Use data layer to save / populate business domain objects  
    
*   Orchestrate application logic / flow  
    

Do not:

*   operate on DTOs  
    

### Data layer

Read about: 

*   [DAO](https://en.wikipedia.org/wiki/Data_access_object)  
    
*   [DTO](https://en.wikipedia.org/wiki/Data_transfer_object)  
    

Data layer does:

*   Fetch DTOs  
    
*   Transform DTOs → business domain objects  
    

### Usual data flow:

*   Logic layer demands access to certain data  
    
    *   keeps it up to date with used cache changes  
        
*   Data layer checks cache  
    
    *   does nothing if populated  
        
    *   deletes and refetched when stale  
        
    *   refetches when none  
        
*   UI layer takes data from global application state / logic layer state