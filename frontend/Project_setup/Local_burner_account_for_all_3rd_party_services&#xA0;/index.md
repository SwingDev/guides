Local burner account for all 3rd party services 
================================================

Background
----------

We believe in working with real services, not mocking them. The sooner a potential problem is found in the software lifecycle - the better.

Hence - we require all third party services to be configured and working using their own burner environment on a local Docker run from the bootstrap repository - with no additional config necessary.

This way you don't need to mock 3rd party services, or pretend you tested if it works - you know it does.

Rules
-----

*   All third party services (Google Analytics, authentication - like Firebase / Auth0, etc.) need to have their own environment set up for local development, shared between all developers.  
    
*   This environment must be treated as 'absolutely insecure'.  
    
    *   **No** private, confidential or in any way real data can be used while developing locally.   
        

How to test this behavior?
--------------------------

When I run the app from it's bootstrap repository:

*   Can I use every single feature of the application?  
    
    *   E.g. can I send and receive emails if such functionality exists?  
        

Implementation hints
--------------------

Look at e.g. [this bootstrap repository](https://github.com/SwingDev/swg-certalerts-bootstrap/blob/master/docker-compose-common.yml) and how it's configured for Mandrill and Auth0.