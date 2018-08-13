Fresh data should propagate across the whole UI
===============================================

Background
----------

One of the tell-tale signs of well-designed data handling layer: fresh data propagates across the whole UI without having to maintain all the links manually.

From the user's perspective - if I save my To Do item I expect this change to propagate automatically to all other pieces of the UI. 

From the developer's perspective - I expect it to just work if I add a new UI component or if I add a new place that allows me to edit this To Do item.

If I don't have to know the implementation details behind the propagation - I won't forget to add something I didn't know I had to add in the first place :)

Rules
-----

*   All UI components must respond to changes in the underlying data, or force a refetch any time data it's showing is stale.  
    
*   Persistence layer should be propagating the committed changes automatically to where it matters.  
    
    *   This means that there must also be a way to 'stage' changes before they are saved. I don't want my draft state to propagate everywhere - 'cancel' functionality would be a hell to implement  
        
*   Persistence layer could also - instead of propagating the changes - mark the objects as 'stale' - so that if there is a component that needs this data - it'll force a refetch.  
    

How to test this behavior?
--------------------------

Always check your UI components for their behavior when underlying data is changed by another component.

Make sure this logic is not mixed up with the UI layer - it should be reasonable transparent, so that a new person can add a new UI component easily, without having to know anything.

Check the behavior when the changes are cancelled (as in hit 'cancel' in the object edit component). These should not be propagated.

Check the behaviors of lists when an object is added / removed. They should also update automatically!

Check the behavior of components that show the object whenever this object is removed while the component is shown.

Check if your 'refetch-if-stale' implementation doesn't cause too many refetches for the same object. Always batch them up.

Implementation hints
--------------------

### global cache

*   Implement a global state using per-item caches, populated by events sent from the application's persistence layer.  
    
*   Marking data as to-be-refetched when actions could have changed it (e.g. parent entity aggregations when changing child entity).  
    
    *   Persistence layer to refetch the object instead of giving the cached one when requested.