Project structure
=================

Background
----------

Good project structure helps you and your teammates to find quickly part of the application. Moreover, well-thought project structure increases your application's scalability. It leads to less painful refactoring.

Rules
-----

*   Divide your application into logical parts  
    
    *   For example move views components to _views_ directory  
        
*   Place files according to their scope  
    
    *   It's good to have common helpers directory, but when helper is used only in one place, keep it near.  
        
*   Always keep third party libraries in _node_modules,_ unless it's necessary   
    
    *   When you need to copy library to your project, add proper note to README file  
        
*   Add README - it really makes on-boarding easier  
    
*   Divide dependencies to [_dependencies_ and _devDependencies_](https://medium.com/@dylanavery720/npmmmm-1-dev-dependencies-dependencies-8931c2583b0c)  in _package.json_  
    
*   Divide styles to global and component scoped  
    
*   Place folder with component's tests in it's directory  
    
*   Organise _images_ directory according to one of the conventions:  
    
    *   by their file type  
        
    *   by their function  
        

Implementation hints
--------------------

The example of good project structure you can find in our _react-ts-boilerplate_ [repository](https://github.com/SwingDev/react-ts-boilerplate/tree/master/src).