Exception Hierarchy
===================

Background
----------

Exceptions are good - they simplify error handling and increase readability. 

Rules
-----

*   Be aware of your exception hierarchy, and how it changes across the application layers.   
    
*   Catch exceptions early, and transform them from very specific low level exceptions to more generic, high level ones.  
    

Implementation hints
--------------------

### Have base exceptions you'll use all over the application

*   'temporary problem'  
    
*   'permanent problem'  
    
    *   'uncorrectable failure'  
        
    *   'critical internal failure'  
        

### Create exceptions inheriting from these base exceptions to constrain possible exceptions being thrown from services:

*   example  
    
    *   URLFetchingService with GET method   
        
*   exception hierarchy  
    
    *   BaseTemporaryErrorException  
        
        *   URLFetchingRemoteNotAvailableException - for 5xx and connection problems  
            
    *   BasePermanentErrorException  
        
        *   BaseCriticalInternalFailureException  
            
            *   URLFetchingCriticalInternalFailureException - for any situations that could indicate that something's very wrong (eg. can't serialize passed DTO to JSON) - so that we as developers are informed about this  
                
        *   URLFetchingNotFoundException - for 404  
            
        *   URLFetchingBadURIException - for internal axios exceptions dealing with uri  
            
*   now an example service that enables user to fetch remote urls would look like:  
    

try {  
    return URLFetchingService.get(uri, params);  
} catch (e) {  
    if (e instanceof BaseTemporaryErrorException) {  
        return retry();  
    } else if (e instanceof URLFetchingBadURIException) {  
        this.addErrors({uri: 'Wrong URI format.'});  
    } else if (e instanceof URLFetchingNotFoundException) {  
        this.addErrors({nonfield: 'Resource is long gone.'});  
    } else if (e instanceof BasePermanentErrorException) {  
        this.onFailure();  
  
        // this will:  
        //  \- fire up a notification  
        //  \- notify us if e is BaseCriticalInternalFailureException  
        ErrorService.dealWith(e);   
    } else {  
        throw e;  
    }  
}