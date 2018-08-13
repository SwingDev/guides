Developer Guide
===============

Introduction
------------

Aim of this guide is to help you understand how we work and what tools we use. It will aid you in setting your computer up, so that you can easily jump into current workflow. Also, this guide briefly covers standards and practices that we apply in our daily work. We hope that this guide will answer all your questions about how we develop applications here in SwingDev. If you have any questions, don't hesitate to ask us (you can find all needed contacts in [Who you can ask](#UWFACAhuTQe) section). Welcome aboard!

**About the Company**

Working at SwingDev means that you will be surrounded by people who are pushing the limits of software product development.

You will have the opportunity to give input on your tasks and you will have an actual impact on the products you build. On a daily basis, you will work in close collaboration with a team of professionals — IT specialists, project managers, designers, and other creatives who are always looking for ways to learn from each other.

At SwingDev, our mission is to make software product development and consulting an efficient, approachable service done with integrity.

We need your skills and dedication to make it happen.

Environment setup
-----------------

*   Before you start  
    
    *   [Computer Setup](Computer_setup/index.md)  
        
*   [Project Setup](Project_setup/index.md)  
    
*   [Git](Git/index.md)  
    
*   DevOps  
    
    *   [Continous Delivery](Continuous_Delivery/index.md)  
        
    *   [Prepare for Asset Caching](Prepare_for_asset_caching/index.md)  
        
    *   [Required Yarn Commands](Required_yarn_commands/index.md)  
        
    *   [Run tests in Docker](Run_tests_in_Docker/index.md)  
        
    *   [Develop in Docker](Develop_in_Docker/index.md)  
        
    *   [Pre-environment constants](Per-environment_constants/index.md)  
        

Architecture
------------

### Coding practices

Writing code using widely recognised and opinionated practices makes our job easier. In our work, we use following rules:

*   SOLID  
    
    *   **Single responsibility principle** - a class should have only a single responsibility (i.e. changes to only one part of the software's specification should be able to affect the specification of the class).  
        
        **Open/closed principle** - "software entities … should be open for extension, but closed for modification."  
        
        **Liskov substitution principle** - "objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program." See also [design by contract](https://en.wikipedia.org/wiki/Design_by_contract).  
        
        **Interface segregation principle** - "many client-specific interfaces are better than one general-purpose interface.”  
        
        **Dependency inversion principle** - one should "depend upon abstractions, \[not\] concretions.”  
        
*   KISS - keep it simple!  
    
*   DRY - don't repeat yourself  
    
*   YAGNI - you ain't gonna need it  
    
*   [Finite State Machines - can be helpful](Finite_State_Machines/index.md)  
    

### Application structure

To make our application scale well, we divide it into several layers — UI, logic and data. Also, a well-thought project structure helps with this task.

For more details, see:

*   [Project structure](Project_structure/index.md)  
    
*   [Keep your UI, logic and data layers separate.](UI_logic_data_layers/index.md)  
    
*   [Abstraction layers - not too little, not too many.](Abstraction_layers/index.md)  
    

### Error handling

We favour proper, well described error handling. It's not only a benefit for the user, but also for the developer. We recommend creating an exception hierarchy with custom error types.

For more details, see:

*   [Exception hierarchy](Exception_Hierarchy/index.md)  
    

Code
----

### Languages

The primary language in the browser environment is JavasScript. Its newest edition, ES6, adds a bunch of useful features. Currently it's the golden standard in web development and we recommend to use it.

ES6 is great but has one major flaw — no type checking. At the moment, there are two solutions for this issue — [FlowType](https://flow.org/en/) and [TypeScript](https://www.typescriptlang.org/). We prefer the latter in our daily work.

For more details, see:

*   [JavaScript (ES6)](JavaScript_(ES6+_standard)/index.md)  
    
*   [TypeScript](TypeScript/index.md)  
    

### Frameworks

Frameworks are a must in modern web development. They include a number of patterns and helpers which improve application development process.

One of the most popular frameworks is React. This library is a component focused rendering engine, it provides good maintainability and community support. Moreover, it gives high-performance, thanks to Virtual DOM.

For more details, see:

*   [React](React/index.md)  
    
*   Vue.js - _work in progress..._  
    

### Markup and Styles

Even if you prefer using a front-end framework over plain HTML, you still need to know basic rules of writing markup code. With HTML5 introduction, we change our way of writing HTML code, discarding divs in favour of semantic elements.

CSS seems to be a simple language, but due to it's cascading and global nature you can quickly fall into a pitfall. Consider using preprocessor such as SCSS and any class naming convention.

For more details, see:

*   [Markup (HTML)](Markup/index.md)  
    
*   [Styles (SCSS)](Styles_(SCSS)/index.md)  
    

### Linter rules

You should always lint your code! We do it, and you should do it also. It makes your life easier.

For more details, see:

*   [JavaScript (ES6)](https://swingdev.quip.com/pUiGAe3wrz7a)  
    
*   [TypeScript](https://swingdev.quip.com/MwWaAavZvLz4)  
    
*   [Styles (SCSS)](https://swingdev.quip.com/b0LwAaC9rQmO)  
    

Application behavior
--------------------

### User experience

As front-end developers, we are responsible for delivering excellent user experience. We need to keep in mind that all internet users are different from each other, and most importantly — from you. Some of them  will be on a poor cellular connection. Some of them will have disabilities.

For more details, see:

*   [Real-life connections](Real-life_connections/index.md)  
    
*   [Accessibility](Accessibility/index.md)  
    

### Performance

Poor connection may not be an only issue. Web can be accessed from a whole spectrum of devices — from old to modern ones. You have to care about your application's performance more than you think.

For more details, see:

*   [Battery performance matters](Battery_performance_matters/index.md)  
    
*   [Loading performance](Loading_performance/index.md)  
    
*   [Optimize Images and Videos](Image_Video_optimization/index.md)  
    
*   [Animations performance](Animations_performance/index.md)  
    

### Data handling

Proper data handling can significantly improve user's experience. You should always propagate latest data to your views and deal with data conflicts appropriately.

For more details, see:

*   [Fresh data should propagate across the whole UI](Fresh_data_should_propagate_across_the_whole_UI/index.md)  
    
*   [Handle conflicts consciously, not accidentally](Handle_conflicts_consciously,_not_accidentally/index.md)  
    

### Data fetching

Usually, front-end applications fetch data from back-end APIs. Poor request handling can cause extended response time or even break your back-end. You should incorporate lazy-loading and batch loading into your data fetching services.

For more details, see:

*   [Lazy-load in the UI](Lazy-load_in_the_UI/index.md)  
    
*   [Batch loading](Batch_loading/index.md)  
    

Tests
-----

*   Write as many tests as you need to be confident in your code.  
    
    *   Prefer end-to-end over integration tests for testing UI flow.  
        
    *   Prefer unit tests for small pieces of logic.  
        
    *   Don't write tests that will never fail.  
        
    *   Test behavior, not implementation.  
        
    *   Don't hesitate to remove tests which give none to little value.  
        
*   Keep end-to-end tests in a separate repository, separate docker file.  
    
*   Run unit / integration tests within Docker — that's the way they will be run.  
    

Who to contact
--------------

Marcin Mincer (COO) - [marcin@swingdev.io](mailto:marcin@swingdev.io)

Tomek Kopczuk (CTO) - [tomek@swingdev.io](mailto:tomek@swingdev.io)

Kacper Kula (Developer Evangelist) - [kacper@swingdev.io](mailto:kacper@swingdev.io)

Mirek Ciastek (Senior Front-end Developer) - [mirek@swingdev.io](mailto:mirek@swingdev.io)