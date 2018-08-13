Prepare for asset caching
=========================

Background
----------

Remember that all your files will be cached by - the browser, a proxy, CDN - you never know what, when and for how long.

It's necessary to develop under this assumption from the very beginning.

Rules
-----

*   Version **all** of your files - e.g. by having Webpack append a hash to bundle file names  
    
*   Have a list of files that need to be invalidated on deploy (if any other than `index.html`) listed in the README.  
    
    *   Otherwise the assumption is - nothing is to be invalidated apart from index.html.  
        

How to test this behavior?
--------------------------

Build the production version and look for fetched files under the Network tab of your Dev Tools.

Any filename that isn't unique will cause problems and will be cached.

Implementation hints
--------------------

Use content hash in your filenames.