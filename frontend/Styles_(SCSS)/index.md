Styles (SCSS)
=============

Background
----------

> **Cascading Style Sheets** (**CSS**) is a [stylesheet](https://developer.mozilla.org/en-US/docs/DOM/stylesheet) language used to describe the presentation of a document written in [HTML](https://developer.mozilla.org/en-US/docs/HTML) or [XML](https://developer.mozilla.org/en-US/docs/XML) (including XML dialects such as [SVG](https://developer.mozilla.org/en-US/docs/SVG) or [XHTML](https://developer.mozilla.org/en-US/docs/XHTML)). CSS describes how elements should be rendered on screen, on paper, in speech, or on other media.

For writing CSS styles we prefer [SCSS](https://sass-lang.com/) (Sassy CSS), which is Sass with CSS syntax. Due to the [cascading](https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade) nature of CSS you should use any class naming convention. We prefer BEM, which quick introduction you can read [here](https://en.bem.info/methodology/quick-start/).  

When we make web application using one of our preferred frameworks, we use [CSS modules](https://github.com/css-modules/css-modules) for React applications and Vue.js (or at least [scoped CSS](https://vue-loader.vuejs.org/en/features/scoped-css.html) classes in this case).

Rules
-----

*   Always [normalize](https://github.com/necolas/normalize.css/) your styles  
    
*   Define [meaningful class names](https://seesparkbox.com/foundry/naming_css_stuff_is_really_hard)  
    
*   Never write selectors using only tags, attributes and ids  
    
*   Use any naming convention (like BEM or CSS modules) to avoid global scope issues  
    
*   For styling elements use mostly pseudo-elements instead of _div_  
    
*   Mind writing styles for different states of elements, like “hover”, “active” and “focus”  
    
*   Define basic styles for typography - titles, default text, links, etc.  
    
*   Keep your code flat, don't nest (visually) selectors no more than [3 levels of depth](https://medium.com/@mciastek/s-css-best-practices-that-you-have-not-yet-known-ba2f6329b5dd)  
    
*   Define variables for common properties like [colors](https://davidwalsh.name/sass-color-variables-dont-suck) or sizes  
    

Linter
------

Our linter settings for CSS styles you can find here - [https://github.com/SwingDev/react-ts-boilerplate/blob/master/.stylelintrc.json](https://github.com/SwingDev/react-ts-boilerplate/blob/master/.stylelintrc.json)