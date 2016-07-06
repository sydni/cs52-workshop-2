#Jekyll & Sass Workshop
Tutorial contents:
* [Welcome to Jekyll](#welcome-to-jekyll)
* [Jekyll Tutorial](#mini-jekyll-tutorial)
* [Welcome to Sass](#welcome-to-sass)
  * [Installation](#install)
* [Sass Tutorial](#mini-sass-tutorial)

#Welcome to Jekyll

#Mini Jekyll Tutorial

#Welcome to Sass
This will run you through a quick introduction to SASS, including **installation**, **basics**, and a simple first **project** to get you familiar with Sass.

###Install
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
Nesting allows you to write Sass so that it's more hierarchical (and in this way, more similar to HTML). So instead of having to type out: 
```CSS
nav ul {
 margin: 0;
 padding: 0;
 list-style: none;
}

nav li {
 display: inline-block;
}

nav a {
 padding: 6px;
 text-decoration: none;
}
```
in Sass you can nest the ul, li, and a components under nav. 
```sass
nav
 ul
  margin: 0
  padding: 0
  list-style: none
  
 li
  display: inline-block;
  
 a
  padding: 6px;
  text-decoration: none
```
(This is also useful when formatting with divs and different class and id names).

### Mixins
With mixins we can create reusable chunks of CSS, which is helpful so we don't have to write a lot of repetitive code.
Instead of having to write out
```css
 a:link { color: white; }
 a:visited { color: blue; }
 a:hover { color: green; }
 a:active { color: red; }
``` 
in different parts of a large site, you can create a mixin.
To create a mixin you use the `$mixin` tag followed the name of the mixin followed by any inputs you want to pass in.
`$mixin mixin_name ($input1, $input2) {...` and then define the mixin within it.
This example even uses a variable as one of the inputs:
```sass
$base-color: pink;

@mixin headline($color, $size) {
 color: $color;
 font-size: $size;
}
``` and then to call it use `@include` and pass in the appropriate values (in the correct order):
```sass
h1 { @include headline($base-color, 12px);}
```
which would compile to:
```css
h1 {
 color: pink;
 font-size: 12px;
}
```
You can also set *default values* for the arguments, so from the example above:
``` sass
@mixin headline($size, $color: red) {
  color: $color;
  font-size: $size;
}

h1 {
  @include headline(12px);
}

h1 {
  @include headline(12px, blue);
}
```
Which would set the color to red in the first (by default) and then blue, since we pass in that argument.
### Inheritance
Again, Sass is meant to make your CSS coding life easier, and inheritance is another way to do that, instead of repeatedly typing out the `color`, `border`, `box-shadow`, `margin`, and `padding` properties over and over again with the same values:
```sass
.breakfast {
  color: #333;
  border: 1px solid #bbb;
  box-shadow: 1px 1px 0 #ddd;
  margin: 0 0 10px;
  padding: 15px;
}

.lunch {
  background-color: yellow;
  color: #333;
  border: 1px solid #bbb;
  box-shadow: 1px 1px 0 #ddd;
  margin: 0 0 10px;
  padding: 15px;
}

.dinner {
  background-color: orange;
  color: #333;
  border: 1px solid #bbb;
  box-shadow: 1px 1px 0 #ddd;
  margin: 0 0 10px;
  padding: 15px;
}
```
we can rewrite it with `@extend`:
```sass
.meal-box {
  color: #333;
  border: 1px solid #bbb;
  box-shadow: 1px 1px 0 #ddd;
  margin: 0 0 10px;
  padding: 15px;
}

.breakfast {
  @extend .meal-box;
}

.lunch {
  @extend .meal-box;
  background-color: yellow;
}

.dinner {
  @extend .meal-box;
  background-color: orange;
}
```
<p data-height="265" data-theme-id="0" data-slug-hash="BjZYVL" data-default-tab="css,result" data-user="SitePoint" data-embed-version="2" class="codepen"> See the Pen <a href="http://codepen.io/SitePoint/pen/BjZYVL/"> Duplication of Properties in SCSS</a> by SitePoint (<a href="http://codepen.io/SitePoint">@SitePoint</a>) on <a href="http://codepen.io"> CodePen </a> . </p>
<script src="//assets.codepen.io/assets/embed/ei.js"> </script>

### And so much more!
Sass has so many more options, such as allowing to split your CSS into smaller portions of code and saving those a snippets to **import** into a larger file,
```sass
// snippet: _reset.sass
html,
body,
ul,
ol
  margin:  0
  padding: 0
``` 
which can then be imported to the main or base file:
```sass
// base.sass

@import reset

body
  font: 100% Helvetica, sans-serif
  background-color: #efefef
```

, or even doing math with a few standard **math operators** `+`,`-`,`*`,`/`, and `%` which could be used as follows: 
```sass
 .container 
  width: 600px/960px * 100%
```

#Mini Sass Tutorial

**Resources**:
* http://sass-lang.com/install
* http://sass-lang.com/guide
* https://www.sitepoint.com/the-benefits-of-inheritance-via-extend-in-sass/
* https://www.sitepoint.com/sass-basics-the-mixin-directive/
