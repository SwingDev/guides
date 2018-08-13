Handle conflicts consciously, not accidentally
==============================================

Background
----------

So what's a conflict? - in our case conflict is said to happen when our application tries to update an object which state changed in between the last fetch and now. It might have been edited, it might have been removed.

You might think that this is an edge case - **it's not**. Your application will be used by multiple people on the same account, by the same user in multiple tabs, by the same user on different devices at the same time. You might want to add live websocket connection to propagate changes as they happen.

All of these cause conflicts.

Rules
-----

*   Always make a decision how this particular entity / action should handle conflicts. Have this, and the reason why, ready for your PR review.  
    
*   Always make a decision whether this particular entity in this scenario should PUT or PATCH the changes.  
    
*   Solve conflicts on the frontend automatically whenever possible.  
    
    *   Some UI actions should automatically overwrite all the fields **that were explicitly changed by the user.** Example - JIRA task title.  
           
        I don't care that someone else changed the title or description in the meantime - if I wanted to change the title, I still want it to happen without any additional alerts.  
          
        Now - for description it would be the opposite - as it might have taken a long time for someone else to put their changes in.  
        
    *   Some UI actions should automatically overwrite the entire entity. Example - background worker task which job is to update the object from a 'ground truth' - e.g. external API.  
        
    *   Some UI actions should just fail whenever the original object changed. Example - Plane seat booking - if it's been snatched by someone else there is nothing we can do.  
        
    *   Some failures are not failures, and should not be treated as such:  
        
        *   404 on a DELETE action - state is exactly as expected, action was a success  
            
    *   Some things must be left for a user to fix - make sure it's a decision though, not an accident.  
        
    *   Balance occurrence rate + frustration vs time to implement on edge cases:  
        
        *   Example 1 - while PATCHING the object I receive a 404  
            
            *   Option 1 - alert the user and transfer his data to 'add object' UI dialog.  
                
            *   Option 2 - automatically create a new object  
                
            *   Option 3 - just alert the user and have him retype everything somewhere else - **don't be this guy! - unless you have a valid reason.**   
                
*   Always handle this automation after a failure returned by the backend - usually it will be 409. Don't leave 409 unhandled.  
    
*   Handle changes being made in the background to the entity the user is editing on your 'edit' component.  
    
    *   Example - I open a JIRA task panel, start editing. In the meantime another polling component fetches the new version of this object. I want this to be handled.  
        

How to test this behavior?
--------------------------

Explicitly check this behavior e.g. by using your component in to tabs or on two devices at the same time.

Implementation hints
--------------------

### Conflict detection

If there is an autoincrementing 'version_id' field - remember to send it to the backend alongside the changes.

### How to be able to make this kind of decisions in your error handling logic

Your 'draft' objects implementation should have the ability to check which fields were changed by the user, and which were not. This gives you a lot of power.

Prefer PATCHing diff over PUTting the whole entity.

### Care about state not single actions

*   “I want this object to be gone” not “I want deletion to succeed”  
    
*   “I want to change this field to X” not “I want the PATCH operation to succeed”  
    
*   Add logic to handle success / failure of your methods independent of actual underlying action success - e.g. 404 on DELETE is a success - object is gone.  
    

### Usual conflict handling scenario

*   Keep your 409 handler separate.  
    
    *   sometimes: entity-wide  
        
    *   sometimes: action-wide  
        
*   In your 409 error handler:  
    
    *   Download new state, keep previous diff  
        
    *   Try to resolve conflict automatically:  
        
        *   Option 1) diff user made can be patched onto new state without conflict  
            
        *   Option 2) we know by design this action should overwrite the state  
            
    *   Alert user if not the case, and let him decide