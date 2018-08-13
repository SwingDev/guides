Per-environment constants
=========================

Background
----------

It's often necessary to bake some environment-specific information (api keys, urls, etc.) into our frontend builds. This is how we do it.

Rules
-----

*   enable WebPack / Gulp to use `.env` file as their source  
    
    *   CI will build the right one for the environment as a building step  
        
    *   Locally you'll have `.env.local` bind-mounted to `.env`