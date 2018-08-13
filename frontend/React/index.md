React
=====

Background
----------

> React makes it painless to create interactive UIs. Design simple views for each state in your application, and React will efficiently update and render just the right components when your data changes.

We choose React as our main front-end framework. It's one of the most popular frameworks nowadays. It’s fast and has pretty low learning curve. If you don’t know React, this [course](https://egghead.io/courses/the-beginner-s-guide-to-react) can give you good overview. React is not a 100% percent MVC-like framework. It only allows you to render dynamic views using JavaScript. That’s why developer needs to add all required stuff by himself.

For managing state in React we use Redux or Mobx. Below are good courses for both of them:

*   Redux - [https://egghead.io/courses/getting-started-with-redux](https://egghead.io/courses/getting-started-with-redux)  
    
*   Mobx - [https://egghead.io/courses/manage-complex-state-in-react-apps-with-mobx](https://egghead.io/courses/manage-complex-state-in-react-apps-with-mobx)  
    

Depending which state manager was used, we use different libraries to manage side effects:

*   Redux - [Redux Thunk](https://github.com/gaearon/redux-thunk) or [Redux Saga](https://github.com/redux-saga/redux-saga)  
    
*   Mobx - side effects are handled by state manager itself  
    

Rules
-----

*   Use [stateless components](https://hackernoon.com/react-stateless-functional-components-nine-wins-you-might-have-overlooked-997b0d933dbc), when you component doesn't need to keep state or event handlers  
    
*   Always keep application state outside from component's state  
    
*   Name your event handlers properly, using naming convention ([reference](https://jaketrent.com/post/naming-event-handlers-react/))  
    
*   Always check [prop types](https://reactjs.org/docs/typechecking-with-proptypes.html) \- in Typescript declare proper interfaces  
    
*   Mind the rendering [perfomance](https://reactjs.org/docs/optimizing-performance.html)  
    
*   Keep complex animations outside of React's state - DOM it's better in it than Virtual DOM  
    
*   Avoid arrow functions and bind in render function ([reference](https://medium.freecodecamp.org/why-arrow-functions-and-bind-in-reacts-render-are-problematic-f1c08b060e36))  
    

Boilerplate
-----------

We prepared boilerplates, which will help you with setup new project with React framework. You can find them here:

*   TypeScript - [https://github.com/SwingDev/react-ts-boilerplate](https://github.com/SwingDev/react-ts-boilerplate)  
    

Linter
------

Our linter settings for React you can find here:

*   TypeScript - [https://github.com/SwingDev/react-ts-boilerplate/blob/master/tslint.json](https://github.com/SwingDev/react-ts-boilerplate/blob/master/tslint.json)