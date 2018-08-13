Run tests in Docker
===================

Background
----------

This is the way that CI and your colleagues will run your tests. Don't try to be different ;-)

Rules
-----

*   Command to run tests:  
    
    *   `docker-compose run —rm <your service name> yarn run test`