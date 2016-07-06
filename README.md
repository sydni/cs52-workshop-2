# Welcome to SASS
This will run you through a quick introduction to SASS, including **installation**, **basics**, and a simple first **project** to get you familiar with SASS.

### Install
These instructions are for how to install on a mac using the :computer: terminal.
(If you are using a different OS then check this page for instructions: http://sass-lang.com/install )

1. **Run** `gem install sass` in terminal. This should install Sass and its dependencies. If it doesn't work, perhaps you need to run it using `sudo`, so `sudo gem install sass`.
2. **Check** that you have it installed by running `sass -v` and it should return what version of Sass you are running.

### Variables
Store info you want to reuse.
Can store:
 - colors
 - font stacks
 - any CSS value you want to reuse
Use `$` to make something a variable.

So for example if you get a font from [Font Awesome](https://fonts.google.com/) and want to save the **font stack** for "Merriweather" you can do it:
```sass
$font-stack: Merriweather, serif
```
and to save a **color**, say for the primary color of your page:
```sass
$primary-color: #ff7575
```
and then you could format that the body of your page. As you can see Sass is syntactically simpler than CSS in that you don't need to use brackets {} or semicolons ;
```sass
body
  font: $font-stack
  color: $primary-color
```

**How?** does it work?
Since Sass is a preprocesser, when it is processed, it takes the variables we defined and outputs normal CSS. 

### Nesting

### Mixins

### Inheritance



**Resources**:
* http://sass-lang.com/install
* http://sass-lang.com/guide
