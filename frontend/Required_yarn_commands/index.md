Required yarn commands
======================

Background
----------

These commands will be used by different parts of the whole process - from CI, through actual servers running your app. Therefore it is vital they are being kept in 'always working' state.

Developing strictly in Docker helps to achieve this goal with next to no additional work, but as 'build' command triggers the 'production' pipeline - it's important to test it as well after making any changes to the pipeline (webpack etc.).

Rules
-----

*   Always keep these commands working:  
    
    *   `yarn start` \- to fire up a local web server with hot-reload and all the works on port 8080  
        
    *   `yarn build` \- to build a production bundle to `/app/dist`  
        
    *   `yarn test` \- to fire up unit / integration tests  
        
*   Test `yarn build` and built assets every time you modify the Production WebPack pipeline.