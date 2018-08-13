Project setup
=============

If you are setting up the project, remember that it should be easily maintainable for other developers, devops and should fit into our deployment setup.

You can experiment with architecture, technologies and solutions but within safe boundaries which help us speed up the process.

All our new projects use bootstrap repository which is a starting point for the project. Bootstrap repository contains docker-compose which describes all modules / services. All additional configuration like nginx configuration should be there as well. For a more detailed information see our [bootstrap-bootstrap](https://github.com/SwingDev/bootstrap-bootstrap) official repository. Every new project should use this tool.

Also, please use other application bootstraps as an example, to solve more complex problems, and to speed up the process. All the bootstraps we have within the company came from months of work in other projects so almost all the decisions made there are battle-tested.

Do not hesitate to question the solutions there, but give them a chance.

If you don't know where to look for a bootstrap, contact other developers working in this technology within the company - they will show you the way.

*   Your project will be developed, run, tested and built through Docker.   
    
    *   [Develop locally in Docker](Develop_in_Docker/index.md) \- it's enabled for live-reload.  
        
    *   [Run tests in Docker](Run_tests_in_Docker/index.md) environment.  
        
    *   Have the [required commands](Required_yarn_commands/index.md) working at all times in Docker container.  
        
    *   [Handle per-environment constants](Per-environment_constants/index.md) according to our rules.  
        
*   Projects must be runnable in a complete state through `docker-compose`, using a [`<project name>-bootstrap` repository](Bootstrap_repository/index.md).  
    
    *   All third party services need to have [their own shared local burner environment](Local_burner_account_for_all_3rd_party_services /index.md) set up.  
        
*   Be prepared for [asset caching](Prepare_for_asset_caching/index.md).