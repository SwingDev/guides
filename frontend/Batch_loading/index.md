Batch loading
=============

Background
----------

Many components on the page might require access to the same entity. This cannot cause multiple fetches, as it's a waste of bandwidth and time.

Same goes for a lot of individual objects - if we're showing 50 entities in a grid - they must be fetched in bulk, not doing 50 separate requests.

Rules
-----

*   Batch loading of the same entity  
    
*   Batch loading of multiple entities at the same time whenever possible.  
    
    *   Always question loading objects one by one if showing more than one at a time.  
        

How to test this behavior
-------------------------

**Always** test your component and application behavior by checking out 'networking' tab of your Dev Tools.

Be able to explain each and every request made by your application - and make them a decision, not an accident.

Make it a job of your persistence layer to coordinate loading.

Implementation hints
--------------------

### Batch requests for the same entity

Cache promises in the persistence layer. Return the same promise if available. Decide if refetch necessary there.

### Batch requests for multiple entities

Always check if the API allows for batching GETs - it usually does. Demand it from your Backend team if needed.

In the persistence layer - gather IDs to be fetched for a single 'tick'. Then gather them up into a single request, and resolve all of the promises after fetching.