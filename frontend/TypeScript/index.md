TypeScript
==========

Background
----------

> TypeScript starts from the same syntax and semantics that millions of JavaScript developers know today. Use existing JavaScript code, incorporate popular JavaScript libraries, and call TypeScript code from JavaScript.  
>   
> Types enable JavaScript developers to use highly-productive development tools and practices like static checking and code refactoring when developing JavaScript applications.

TypeScript is mainly superset of JavaScript language. This means that you get all this that is offered by JavaScript, plus new features (compatible with [ES6](JavaScript_(ES6+_standard)/index.md)) and type checking.

Thanks to TypeScript you can write maintainable and readable code. TypeScript brings types from statically typed languages to JavaScript. You don't need to worry about type mismatching, because compiler catches it for you.

There is one tradeoff, you lose the dynamic nature of JavaScript. Also, type checking is as much accurate as you are precise in types defining. The learning curve is steep for this language, but still, it's worth to use it in your project.

Checkout some tutorials about TypeScript:

*   [https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html)  
    
*   [https://toddmotto.com/typescript-introduction](https://toddmotto.com/typescript-introduction)  
    

Rules
-----

*   Disallow usage of _any_ type  
    
*   Use [enums](https://www.typescriptlang.org/docs/handbook/enums.html) to define flag variables  
    
*   Use interfaces over simple types  
    
*   Take advantage of using [generic types](https://www.typescriptlang.org/docs/handbook/generics.html)  
    
*   Consider using linter or / and [styleguide](https://basarat.gitbooks.io/typescript/docs/styleguide/styleguide.html)  
    

Linter
------

To use full potential of the TypeScript, we use strict linting rules. This allows us to levarage all the hard work of types checking to the language and helps with development if done properly. The main rule you should obey: The Stricter, The Better. 

Our linter settings for TypeScript you can find here - [https://github.com/SwingDev/react-ts-boilerplate/blob/master/tslint.json](https://github.com/SwingDev/react-ts-boilerplate/blob/master/tslint.json)