# Learn CSS in simple terms
Ok, so you learned HTML basics, know how to write an HTML document, and now want to learn how to style an HTML document? If so, then you're at the right place!
**Here we're gonna learn CSS, simple and fast!**

You won't see me talk too much, but see codes a lot! And the only way to learn a coding language, is to get your hands dirty with it, **open up a text editor, and just start typing**! That's exactly what we're going to do. **If you don't understand everything at this moment** (e.g., why to write this or that symbol), **don't worry**! Simply watch my sample codes and then try to write the exact (or similar) codes yourself! Just do it! Right now, you don't have to know every little detail... You like to learn fast (and maybe earn some money as a web designer or frontend developer), right? So don't worry about theoretical stuff or history mystery at this stage! There's always time to study and learn such stuff... So here, we're just going to focus on the main stuff and aim to learn CSS a.s.a.p :rocket:




# For whom this tutorial is?
For anyone who has a basic understanding of HTML!

So please first take a look at the following **prerequisites for this tutorial**:
- ["Learn setting up a simple Frontend environment for beginners" tutorial](https://github.com/imalitavakoli/learn-frontend-env-setup) (9 min read)
- ["Learn HTML in simple terms" tutorial](https://github.com/imalitavakoli/learn-html) (4 min read)

So you're ready? Let's do it :thumbsup:




# Sample files?
Any sample codes that I write here in this tutorial, can be found in the "*Samples*" directory of the GitHub repository of the tutorial. [Click here](https://github.com/imalitavakoli/learn-css/archive/refs/heads/main.zip) to download them all.

**NOTE:** To learn coding and gain confidence, please do not just look at the samples! open up a text editor, write some similar codes yourself, save your files, and open them via a web browser to check out your results! This is the only way to be a coder!




# Table of contents to learn
- [What is CSS?](#what-is-css)
- [Basics](#basics)
- [Columns](#columns)
- [Transforms](#transforms)
- [Transitions & animations](#transitions--animations)
- [Flexbox](#flexbox)
- [Media Queries](#media-queries)
- [Custom Properties (Variables)](#custom-properties-variables)
- [Import](#import)
- [Tips & Tricks](#tips--tricks)
- [Scalable & Modular Architecture for CSS (SMACSS) Methodology](#scalable--modular-architecture-for-css-smacss-methodology)
- [BEM Methodology](#bem-methodology)




## What is CSS?
CSS stands for "*Cascading Style Sheets*". It describes how HTML elements are to be displayed on screen, paper, or in other media. CSS saves a lot of work. It can control the layout of multiple webpages all at once.

Imagine a human body... **CSS is the skin**! (You can imagine CSS as the clothes and makeup you wear too) It styles webpages and beautify HTML documents. CSS is actually used to define styles for webpages' layout and variations in display for different devices and screen sizes.


### How to produce CSS?
CSS can be written inside HTML documents themselves (as an internal CSS or inline CSS), or in a separate file which multiple HTML documents can use (external CSS).

Here's how to write CSS inside an HTML document:
- You can write CSS within the `<style>` element, inside the `<head>` section of an HTML page. This type of inserting a style sheet is known as an **internal CSS**.
- Or you can write CSS to apply a unique style for a single element. This type of inserting a style sheet is known as an **inline CSS**. To use inline styles, add the `style` attribute to the relevant element. The `style` attribute can contain any CSS property. e.g., `<h1 style="color:blue;text-align:center;">This is a heading</h1>`

Here's how to write CSS in a seperate file (**external CSS**):
1. You **write your style sheet in a text editor** and save it with the extension of *.css* and *UTF-8* encoding. (e.g., main.css)
2. Now **include a reference to the external style sheet file inside your HTML pages** and save your documents. In order to do that, the reference must be inside the `<link>` element, inside the `head` section. e.g., `<link rel="stylesheet" href="main.css">`

**What style will be used when there is more than one style specified for an HTML element?** Well, All the styles in a page will "cascade" into a new "virtual" style sheet by the following rules, where number one has the highest priority: 1.Inline style (inside an HTML element) 2.External and internal style sheets (in the head section) 3.Browser default. So, an inline style has the highest priority, and will override external and internal styles and browser defaults.


### CSS syntax?
A CSS rule consists of a *selector* and a *declaration block*: `selector { property:value; }`. e.g., `p { color: red; }`.  
The selector points to the HTML element you want to style. The declaration block is surrounded by curly braces, and contains one or more declarations separated by semicolons. Each declaration includes a CSS property name and a value, separated by a colon.


### A sample that uses an external CSS?
Here you can see a simple HTML document that includes a reference to an external style sheet file.

**NOTE:** In my sample codes, I try to quickly explain some definitions by placing comments among the codes.

**NOTE:** What is a comment? You can write comments among your codes to explain your code, which can help you when you edit the source code at a later date. In CSS, anything between `/*` and `*/` is ignored by browsers. e.g., `/* This is a comment */`

```css
/* css/01.css */

p {
  color: red; /* Change the color of all <p> tags to red */
}
```

```html
<!-- 01_use-external-styles.html -->

<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>

    <!-- Reference to our external style sheet. -->
    <link rel="stylesheet" href="./css/01.css">
  </head>
  <body>
    <h1>First Heading</h1>
    <p>First paragraph.</p>

    <h1>Second Heading</h1>

    <!--
    By setting an inline CSS we override the external CSS rule that made all 
    paragraphs to be red!
    -->
    <p style="color: green;">Second paragraph is green!</p>
  </body>
</html>
```


### A sample that uses an internal CSS?
Here you can see a simple HTML document that includes some CSS rules within the `<style>` element, inside the `<head>` section of the page.

```html
<!-- 02_use-internal-styles.html -->

<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>
    <style>
      p {
        color: red; /* Change the color of all <p> tags to red */
      }
    </style>
  </head>
  <body>
    <h1>First Heading</h1>
    <p>First paragraph.</p>

    <h1>Second Heading</h1>

    <!--
    By setting an inline CSS we override the internal CSS rule that made all 
    paragraphs to be red!
    -->
    <p style="color: green;">Second paragraph is green!</p>
  </body>
</html>
```


### CSS selectors?
CSS selectors are used to find (or select) the HTML elements you want to style.
CSS selectors can be divided into five categories:
- Simple selectors (select elements based on name, id, class)  
  e.g., `#idOfAnElement { text-align: center; } .class-of-an-element { color: red; }`
- Combinator selectors (select elements based on a specific relationship between them):
  - Descendant Selector: Matches all elements that are descendants of a specified element.  
  e.g., `div p { background-color: red; }`
  - Child Selector (>): Selects all elements that are the direct children of a specified element.  
  e.g., `div > p { background-color: red; }`
  - Adjacent Sibling Selector (+): Selects an element that is directly after another specific element.  
  e.g., `div + p { background-color: red; }`
  - General Sibling Selector (~): selects all elements that are next siblings of a specified element.  
  e.g., `div ~ p { background-color: red; }`
- Pseudo-class selectors (select elements based on a certain state). The syntax of pseudo-classes: `selector:pseudo-class {}`  
e.g., `a:hover { text-decoration: none; }`
- Pseudo-elements selectors (select and style a part of an element). The syntax of pseudo-elements: `selector::pseudo-element {}`  
e.g., `p::first-letter { font-size: 200%; color: orange; }`
- Attribute selectors (select elements based on an attribute or attribute value)  
e.g., let's select all `<a>` elements with a target attribute: `a[target] { text-decoration: underline; }`.  
Or select all elements with a class attribute value that contains "ye": `[class*="ye"] { color: yellow; }`




## Basics
In my sample code below, we're going to see different ways of styling HTML elements in practice.

```html
<!-- 03_basics-01.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>03</title>

    <style>
      /*
      The following CSS rules are going to be aplied to ALL elements and their 
      ::before and ::after pseudo-elements.
      */
      *,
      *::before,
      *::after {
        box-sizing: border-box;
      }

      /* The following CSS rules are going to be aplied ONLY to the body element. */
      body {
        background-color:#333333;
        color: #ffffff;
      }

      /* The following CSS rules are going to be aplied to h1, h2, h3, h4, h5, h6 elements. */
      h1, h2, h3, h4, h5, h6 {
        text-transform: uppercase;
      }

      /*
      The following CSS rules are going to be aplied ONLY to an element which 
      its id attribute is "specificElement".
      */
      #specificElement {
        font-size: 2.5rem;
        color: pink;
      }

      /*
      The following CSS rules are going to be aplied ONLY to any element which 
      its class attribute includes "someElements".
      */
      .someElements {
        text-decoration: underline;
      }
      .color-yellow {
        color: yellow;
      }

      /*
      The following CSS rules are going to be aplied ONLY to any span element 
      which its class attribute includes "boldish" AND is the direct or indirect 
      child of any p element.
      */
      p span.boldish {
        font-weight: bold;
      }
    </style>

  </head>
  <body>

    <h1 id="specificElement">Heading</h1>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id <a href="#" class="someElements">est laborum</a>.
    </p>

    <!-- 
    The HTML class attribute is used to specify a class for an HTML element.
    The class attribute is often used to point to a class name in a style sheet. 
    (It can also be used by a JavaScript to access and manipulate elements with 
    the specific class name)
    
    NOTE: The class name is case sensitive!

    TIP: To define multiple classes, separate the class names with a space, 
    e.g., <div class="city main">. The element will be styled according to all 
    the classes specified.
    -->
    <p class="someElements color-yellow">
      Here is the second <span class="boldish">paragraph</span>.
    </p>

  </body>
</html>
```


In my sample code below, we're going to see some of the most frequently used CSS rules related to styling texts and links.

```html
<!-- 04_basics-02.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>04</title>

    <style>
      /* ///////////////////////////////////// Text related styles */

      p {
        color:#333333;
      	text-align: center;
      	text-decoration: none;

        /*
        NOTE: The inherit keyword specifies that a property should inherit its 
        value from its parent element. The inherit keyword can be used for any 
        CSS property, and on any HTML element.
        */
      	text-transform: inherit;

        /* Indent the first line of text. e.g., 20px, -1rem, 5%. */
      	text-indent: 20px;

        /* The default line height in most browsers is about 110% to 120%. */
      	line-height: 1.2;

      	word-spacing: normal;
      	white-space: normal;
      	letter-spacing: 3px;
        direction: ltr;

        /*
        Specifies whether or not the browser can break lines with long words, if 
        they overflow the container.
        */
        overflow-wrap: anywhere;

        font-family: Arial, Helvetica, sans-serif;
        font-size: 1rem;
        font-style: normal;
      	font-weight: normal;

        /* Specifies whether or not a text should be displayed in a small-caps font. */
      	font-variant: normal;

      	/*
      	Syntax:
      	text-shadow: h-shadow v-shadow blur-radius color|none|initial|inherit;
      	NOTE: To add more than one shadow to the text, add a comma-separated list of shadows.
      	*/
      	text-shadow: 2px -2px 5px rgba(51, 51, 51, 0.5);
      }
      .serif {
        font-family:"Times New Roman", Times, serif;
      }
      .monospace {
        font-family:"Courier New", Courier, monospace;
      }

      /*
      With the @font-face rule, we do not have to use one of the "web-safe" 
      fonts anymore.
      To use the font for an HTML element, we can refer to the name of the font 
      through the font-family property: div { font-family: myCustomFont; }
      */
      @font-face
      {
        font-family: myCustomFont;
        src: url(path/to/font.ttf);
      }

      /*
      We must add another @font-face rule containing descriptors for bold text.
      Browsers will use "font-bold.ttf" font whenever a piece of text with the 
      font-family "myCustomFont" should render as bold.

      NOTE: The following font descriptors can be defined inside the @font-face 
      rule: font-family, src, font-stretch, font-style, font-weight, unicode-range
      */
      @font-face
      {
        font-family: myCustomFont;
        src: url(path/to/font-bold.ttf);
        font-weight: bold;
      }


      /* ///////////////////////////////////// Link related styles */

      a:link,                         /* a:link - a normal, unvisited link */
      a:visited,                      /* a:visited - a link the user has visited */
      a:active {                      /* a:active - a link the moment it is clicked */
      	color: #FF6600;
      	text-decoration: none;
      }
      a:hover {                       /* a:hover - a link when the user mouses over it */
      	text-decoration:underline;
      }
    </style>

  </head>
  <body>

    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
      <a href="#">A sample link</a>.
    </p>
    <pre class="monospace">Sample preformatted text.</pre>

  </body>
</html>
```


In my sample code below, we're going to see some of the most frequently used CSS rules related to styling lists and tables.

```html
<!-- 05_basics-03.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>05</title>

    <style>
      /* ///////////////////////////////////// List related styles */

      ul {
        list-style-type: circle;
      }
      ol {
        list-style-type: lower-alpha;
      }

      .list-custom {
        margin: 0px;
      	padding: 0px;
        list-style-type: none;
      }
      .list-custom li {
        margin: 4px 0;
      	padding-left: 40px;
      	padding-top: 7px;
      	padding-bottom: 7px;
        background-image: url("list-custom.png");
      	background-repeat: no-repeat;
      	background-position: 0px 0px;
      }


      /* ///////////////////////////////////// Table related styles */

      table {
        /*
        Sets whether table borders should collapse into a single border or be 
        separated as in standard HTML.
        */
        border-collapse: collapse;
      }
      table, td, th {
        padding: 5px;
      	border: 2px dotted #FF99CC;
        text-align: center;
      	vertical-align: middle;
      }
      thead th {
        background-color: #FFCCFF;
      }
      tr.table-alt {
        background-color: #CCFFFF;
      }
      table caption {
        caption-side: bottom;
        padding: 5px;
        text-align:right;
      	vertical-align: middle;
      }
    </style>

  </head>
  <body>

    <ul class="list-custom">
      <li>List Item 01</li>
      <li>List Item 02</li>
      <li>List Item 03</li>
    </ul>

    <table>
      <caption>Table Caption</caption>
      <thead>
        <th>Table Head 01</th>
        <th>Table Head 02</th>
      </thead>
      <tbody>
      <tr>
        <td>Data 01</td>
        <td>Data 02</td>
      </tr>
      <tr class="table-alt">
        <td>Data 01</td>
        <td>Data 02</td>
      </tr>
      <tr>
        <td>Data 01</td>
        <td>Data 02</td>
      </tr>
      <tr class="table-alt">
        <td>Data 01</td>
        <td>Data 02</td>
      </tr>
      </tbody>
      <tfoot>
        <td colspan="2">My footer</td>
      </tfoot>
    </table>

  </body>
</html>
```


In my sample code below, we're going to see some of the most frequently used CSS rules related to styling outlines, borders, backgrounds, and box models.

```html
<!-- 06_basics-04.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>06</title>

    <style>
      /* ///////////////////////////////////// Outline related styles */

      .box {
        /*
        An outline is a line that is drawn around elements, outside the borders, 
        to make the element "stand out".

        The outline property is a shorthand property for: outline-width, 
        outline-style (required), outline-color.

        Syntax:
      	outline: outline-width outline-style outline-color|initial|inherit;
      	*/
      	outline: thick dotted blue;

        /* outline-width: thick;
        outline-style: solid;
        outline-color: blue; */
      }


      /* ///////////////////////////////////// Border related styles */

      .box {
      	border: 5px solid red;
        border-radius: 15px;          /* Defines the radius of the element's corners. */

        /* NOTE: Each of the borders (top, right, bottom, and left) can also be styled differently. */
        border-bottom-color: green;

        /* border-width: 5px;
        border-style: solid;
        border-color: red; */
      }


      /* ///////////////////////////////////// Background related styles */

      .box {
        /*
        RGBA color value is RGB color value but with an alpha channel which 
        specifies the opacity for a color.
        */
        background-color: rgba(255, 0, 0, .5);

        background-image: url('hero.jpg');
      	background-repeat: no-repeat;

        /* Specifies whether the background image should scroll or be fixed. */
        background-attachment: scroll;

      	background-position: top right;

        /* Specifies the size of the background images */
        background-size: cover;

        /* background: rgba(255, 0, 0, .5) url('hero.jpg') no-repeat scroll top right; */

        /*
      	Syntax:
      	box-shadow: none|h-offset v-offset blur spread color |inset|initial|inherit;

      	NOTE: To attach more than one shadow to an element, add a comma-separated list of shadows
      	*/
      	box-shadow: 2px -2px 5px rgba(51, 51, 51, 0.5);
      }

      body {
        background-attachment: fixed;

        /*
        CSS gradients let you display smooth transitions between two or more specified colors.

      	Syntax:
      	background-image: linear-gradient(direction, color-stop1, color-stop2, ...);
      	*/
        background-image: linear-gradient(to bottom right, yellow, rgba(255,0,0,1));
        /* background-image: linear-gradient(135deg, yellow, rgba(255,0,0,1)); */

        /* The repeating function is used to repeat gradients: */
        /* background-image: repeating-linear-gradient(135deg, yellow 10%, red 20%); */

        /*
        A radial gradient with differently spaced color stops.
        The size parameter defines the size of the gradient. It can take four
        values: closest-side, farthest-side, closest-corner, farthest-corner.
        */
        /* background-image: radial-gradient(farthest-corner at 90% 10%, red 60%, yellow 95%); */
        /* background-image: repeating-radial-gradient(red 60%, yellow 95%); */

        /*
        A conic gradient is a gradient with color transitions rotated around a
        center point.
        */
        /* background-image: conic-gradient(#fff4c6 0deg 90deg, #ffdf5b 90deg 180deg, #fff4c6 180deg 270deg, #ffdf5b 270deg); */
        /* background-image: repeating-conic-gradient(#fff4c6 0deg 10deg, #ffdf5b 10deg 20deg); */
      }


      /* ///////////////////////////////////// Box model related styles */

      .box {
        /*
        The margin property sets the margins for an element.
        The margin property is a shorthand property for: margin-top, 
        margin-right, margin-bottom, margin-left

        The margin property can have four values: [top] [right] [bottom] [left]
        The margin property can have three values: [top] [right & left] [bottom]
        The margin property can have two values: [top & bottom] [right & left]
        The margin property can have one value: [all four sides]
        In our example here, all four margins are 10px.

        NOTE: Negative values are allowed.
        */
        margin: 10px;

        /*
        An element's padding is the space between its content and its border.
        The padding property is a shorthand property for: padding-top, 
        padding-right, padding-bottom, padding-left

        Padding property like margin property can also have four, three, two, or 
        one values. In our example here, all four paddings are 10px.

        NOTE: Padding creates extra space within an element, while margin 
        creates extra space around an element.

        NOTE: Negative values are not allowed.
        */
        padding:10px;

        width:250px;
        max-height: 100px;

        /*
        Specifies whether to clip the content, add a scroll bar, or display 
        overflow content of a block-level element, when it overflows at the top 
        and bottom edges.
        
        TIP: Use the overflow-x property to determine clipping at the left and right edges.
        */
        overflow-y: auto;
      }
    </style>

  </head>
  <body>

    <p class="box" style="color: white;">
      Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Nam cursus. Morbi ut mi. Nullam enim leo, egestas id, condimentum at, laoreet mattis, massa. Sed eleifend nonummy diam.
    </p>

  </body>
</html>
```


In my sample code below, we're going to see some of the most frequently used CSS rules related to styling positioning and displaying.

```html
<!-- 07_basics-05.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>07</title>

    <style>
      /* ///////////////////////////////////// Positioning related styles */

      .toast {
        /*
        Specifies the type of positioning method used for an element. (static, 
        relative, absolute, fixed, or sticky)
        */
        position: fixed;

        /* The top/bottom property affects the vertical position of a positioned element. */
        top: 5px;

        /* The left/right property affects the horizontal position of a positioned element. */
        right: 5px;
      }


      /* ///////////////////////////////////// Displaying related styles */

      #nav li {
        /* Specifies the display behavior (the type of rendering box) of an element. */
        display: inline;
      }
      #nav li:last-child {
        /*
        Specifies whether or not an element is visible. Hidden elements take up 
        space on the page. Use the display property to both hide and remove an 
        element from the document layout!
        */
        visibility: hidden;
      }
    </style>

  </head>
  <body>

    <div class="toast" style="padding: 5px; background-color: lightblue;">
      This is a fixed positioned box.
    </div>

    <ul id="nav">
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Contact</a></li>
      <li><a href="#">Something else</a></li>
    </ul>

  </body>
</html>
```




## Columns
Here I introduce some of the column related CSS rules. With column rules you can create multiple columns for laying out texts. (like in newspaper)

```html
<!-- 08_columns.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>08</title>
    <style>
      .container {
        /*
        Specify the minimum width for each column, and the maximum number of columns.

        The columns property is a shorthand property for: column-width, column-count.
        */
        columns: 100px 3;

        column-gap: 20px;

        /*
        Specify the minimum width for each column, and the maximum number of columns.

        The columns property is a shorthand property for: column-rule-width, 
        column-rule-style (required), column-rule-color.
        */
        column-rule: 2px dashed #333333;
      }
    </style>
  </head>
  <body class="container">

    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

  </body>
</html>
```




## Transforms
Here I introduce some of the transform related CSS rules. The transform property applies a 2D or 3D transformation to an element. This property allows you to rotate, scale, move, skew, etc., elements.

```html
<!-- 09_transforms.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>09</title>
    <style>
      .container {
        width:200px;
        padding: 20px;
        border-radius: 10px;
      	background-color: #ffc90e;

        transform: rotate(10deg) translate(50px, 100px) scale(1.1, 1.1);

        /* Allows you to change the position of transformed element. */
        transform-origin: 50% 50%;

        /*
        Specifies how nested elements are rendered in 3D space.
        preserve-3d value specifies that child elements will preserve their 3D 
        position according to their parent. e.g., if the parent has 
        `transform: rotateY(60deg);` rule, then the child element respects its 
        parent element's 3D transformation.
        */
        transform-style: preserve-3d;
      }
    </style>
  </head>
  <body>

    <div class="container">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </div>

  </body>
</html>
```




## Transitions & animations
Here I introduce some of the transition and animation related CSS rules.

**CSS transitions** allows you to change property values smoothly, over a given duration.  
To do this, you must specify two things:
- the CSS property you want to add an effect to. e.g., `transition-property: width, transform;`
- the duration of the effect. e.g., `transition-duration: 1s;`

**NOTE:** The transition effect starts when the specified CSS property changes value, otherwise we cannot see the effect! So as an example we can set a width for our element, and then set another width for it on the `:hover` state. The transition will happen when user mouse over the element.

**CSS animations** allows you to animate HTML elements without using JavaScript or Flash! An animation lets an element gradually change from one style to another.  
To do this, you must specify two things:
- Define a `@keyframes` rule. `@keyframes` rule is where the animation is created! Inside of it, you can specify CSS styles at certain times, and the animation will gradually change from the current style to the new style. e.g., `@keyframes myAni { from { background-color: #ffc90e; } to { background-color: #bcd6ec; } }`
- Bind the animation to an element. e.g., `animation: myAni 1s ease 0s infinite alternate;`

```html
<!-- 10_transitions-and-animations.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>10</title>
    <style>
      .box1 {
        width:200px;
        padding: 20px;
      	background-color: #ffc90e;
        text-align: center;
        transform-origin: top left;

        border-radius: 10px;
        transform: scale(1, 1);

        /*
        The transition property is a shorthand property for:
        transition-property, transition-duration, transition-timing-function, transition-delay.
        */
        transition: transform .5s, border-radius 2s;

        /*
      	Syntax:
      	transition-timing-function: linear|ease|ease-in|ease-out|ease-in-out|
        step-start|step-end|steps(int,start|end)|cubic-bezier(n,n,n,n)|initial|inherit;

        NOTE: Test common easing curves on a range of interfaces, or generate 
        your own custom bezier curve, check out here: https://easings.co/
      	*/
        transition-timing-function: ease;

        transition-delay: 0s;

        /* transition: transform 1s ease 0s; */
      }

      .box1:hover {
        border-radius: 0;
        transform: scale(1.1, 1.1);
      }

      @keyframes myAni {
        from {
          background-color: #ffc90e;
        }
        50% {
          background-color: #bcd6ec;
        }
        to {
          background-color: #eeeeee;
        }
      }

      .box2 {
        /*
        The animation property is a shorthand property for: animation-name, 
        animation-duration, animation-timing-function, animation-delay, 
        animation-iteration-count, animation-direction, animation-fill-mode, 
        animation-play-state.
        */
        animation: myAni 1s;

        /*
      	Syntax:
      	animation-timing-function: linear|ease|ease-in|ease-out|ease-in-out|
        step-start|step-end|steps(int,start|end)|cubic-bezier(n,n,n,n)|initial|inherit;
      	*/
        animation-timing-function: ease;

        /* Specifies a delay for the start of an animation. */
        animation-delay: 0s;

        /* Specifies the number of times an animation should be played. */
        animation-iteration-count: infinite;

        /*
        Defines whether an animation should be played forwards, backwards or in 
        alternate cycles.

        Syntax:
        animation-direction: normal|reverse|alternate|alternate-reverse|initial|inherit;
        */
        animation-direction: alternate;

        /*
        Specifies a style for the element when the animation is not playing 
        (before it starts, after it ends, or both).

        Syntax:
        animation-fill-mode: none|forwards|backwards|both|initial|inherit;
        */
        animation-fill-mode: none;

        /*
        Specifies whether the animation is running or paused.

        Syntax:
        animation-play-state: paused|running|initial|inherit;
        */
        animation-play-state: running;
      }
    </style>
  </head>
  <body>

    <div class="box1">
      I grow on hover :)
    </div>

    <div class="box2">
      I am animated :)
    </div>

  </body>
</html>
```




## Flexbox
Here I introduce you to the Flexbox! **The Flexible Box Layout Module, makes it easier to design flexible responsive layout structure** without using float or positioning. Before the flexbox, designers had tough times centering text/element at the middle/bottom of the webpage or another element! But with the flexbox, everything got so much easier!

**The Flexbox model consists of a container and its items** (direct children).

The **container defines how its items should be shown** inside of it. e.g., shall the items listed from top to bottom (`flex-direction`), shall they wrap (`flex-wrap`), or how they should be distributed inside of the container horizontally and vertically (`justify-content`, `align-items`, `align-content`).

The **items define how they themselves should be shown** inside of their container (parent). e.g., what should be the order of an item (`order`), how much space an item can take (`flex-grow`, `flex-shrink`), what size the item should be (`flex-basis`), or whether the item should override the default alignment items of the container for itself or not (`align-self`).

```html
<!-- 11_flexbox.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>11</title>
    <style>
      .container {
        display: flex;                  /* or inline-flex */

        /*
        row (default): left to right in ltr; right to left in rtl
        row-reverse: right to left in ltr; left to right in rtl
        column: same as row but top to bottom
        column-reverse: same as row-reverse but bottom to top
        */
        flex-direction: row;

        flex-wrap: nowrap;              /* nowrap|wrap|wrap-reverse */

        /* Shorthand for flex-direction and flex-wrap properties */
        /* flex-flow: row wrap; */

        /*
        This defines the alignment along the main axis.

        Syntax:
        justify-content: flex-start|flex-end|center|space-between|
        space-around|space-evenly;
        */
        justify-content: flex-start;

        /*
        This defines the default behavior for how flex items are laid out along
        the cross axis on the current line. Think of it as the justify-content
        version for the cross-axis.

        Syntax:
        align-items: stretch|flex-start|flex-end|center|baseline;
        */
        align-items: center;

        /*
        This property only takes effect on multi-line flexible containers, where
        flex-wrap is set to either wrap or wrap-reverse.

        Syntax:
        align-content: flex-start|flex-end|center|space-between|space-around|stretch;
        */
        align-content: center;

        min-height: 100vh;
      }

      .item {
        padding: 10px;
        border: 1px solid #a5ccd6;
        background-color: #cbe7ee;
        font-size: 24px;
        text-align: center;
        box-sizing: border-box;
      }

      .item-grown {
        order: -1;                       /* default is 0 */

        /*
        Specifies the ability for a flex item to grow if necessary. It accepts a
        unitless value that serves as a proportion. Default is 0. Negative
        numbers are invalid.

        Here in our example, the element has a value of 2. It means that it
        would take up twice as much of the space either one of the other items
        (or it will try, at least).
        */
        flex-grow: 2;

        /*
        Specifies the ability for a flex item to shrink if necessary. It accepts
        a unitless value that serves as a proportion. Default is 1. Negative
        numbers are invalid.
        */
        flex-shrink: 1;

        /*
        Specifies the default size of the item. Default is auto. It accepts a
        length unit, or percentage.
        */
        flex-basis: 300px;

        /* Shorthand for flex-grow, flex-shrink, and flex-basis properties */
        /* flex: 2 1 300px; */

        align-self: stretch;             /* auto|flex-start|flex-end|center|baseline|stretch */
      }
    </style>
  </head>
  <body>

    <section class="container">
      <div class="item">01</div>
      <div class="item item-grown">02</div>
      <div class="item">03</div>
      <div class="item">04</div>
    </section>

  </body>
</html>
```


## Media Queries
Here I introduce you to media queries! They help us apply different styles for different media types/devices. In simple terms, they actually help us design a responsive webpage that is beautifully viewed in mobile, tablet, and desktop devices. As an example, we can set some CSS rules to beautify our webpage when viewed in mobile devices, and then use media queries to override some of those rules when our webpage is viewed in desktop devices! In this way the contents of our webpage is beautifully fit in both devices, and we call such a webpage, a responsive webpage. So anyway, in order to use media queries we need to define a `@media` rule.

The syntax of `@media` rule: `@media not|only mediatype and (expressions) { CSS-Code; }`  
e.g., `@media screen and (min-width: 576px) { .logo { display: block; } }`

**NOTE:** We can also include references to different external style sheet files for different media in our HTML pages, like this:

```html
<link rel="stylesheet" media="screen and (min-width: 768px)" href="main-md.css">
<link rel="stylesheet" media="screen and (min-width: 992px)" href="main-lg.css">
```

```html
<!-- 12_media-queries.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>12</title>
    <style>
      .b {
        color: red;
      }
      
      .c {
        width: 100px;
        background-color: lightblue;
      }

      .d {
        color: #333333;
        background-color: #cccccc;
      }


      @media (min-width: 576px) {
        .a {
          display: none;
        }
      }

      @media (min-width: 768px) {
        .b {
          color: blue;
        }
      }

      /*
      The following CSS rules will only apply on screens when the browser window 
      is wider than its height, a so called "Landscape" orientation.
      */
      @media screen and (orientation: landscape) {
        .c {
          width: 100%;
        }
      }

      /*
      The following CSS rules will only apply on print. I mean when the document 
      is printed.
      */
      @media print {
        .d {
          color: #000000;
          background-color: #ffffff;
        }
      }

      /*
      NOTE: Comma separated list, behave like an OR operator.
      So as an example, the following CSS rules will only apply when the width 
      is between 100px and 200px OR above 576px.
      */
      @media (max-width: 200px) and (min-width: 100px), (min-width: 576px) {
        .e {
          display: none;
        }
      }
    </style>
  </head>
  <body>

    <div class="a">I am hidden in a viewport wider than 576px.</div>
    <div class="b">I am blue in a viewport wider than 768px.</div>
    <div class="c">I am viewed with a 100% width when the browser window is wider than its height, a so called "Landscape" orientation.</div>
    <div class="d">I am in pure black & white colors ONLY when I'm going to be printed.</div>
    <div class="e">I am hidden in a viewport is between 100px and 200px OR above 576px.</div>

  </body>
</html>
```




## Custom Properties (Variables)
Here I introduce you to custom properties, that are known as variables too. Variables help you DRY (Don't Repeat Yourself) up your CSS. As an example they are helpful when you like to create color themes for your website or app...  Instead of copy and paste the same colors over and over again, you can place them in variables. You can just simply declare some variables (e.g., `:root { --bluish: #6199da; }`), use them in different places (e.g., `.heading { color: var(--bluish); } .card { background-color: var(--bluish); }`), and then simply re-declare them in different theme related selectors (e.g., `.theme-night { --bluish: #534c7e; }`). Now when you use the theme selector in your webpages for an element (e.g., you can add the theme CSS class to the `<body>` element: `<body class="theme-night">`), all the element's descending children that have already used the variable in their styles, now use the new overridden value of the variable.

We can create variables with local or global scope. Global variables can be accessed/used through the entire document, while local variables can be used only inside the selector where it is declared.

To create a variable with global scope, declare it inside the `:root` selector (The `:root` selector matches the document's root element). To create a variable with local scope, declare it inside the selector that is going to use it. The `var()` function is used to insert the value of a CSS variable.

The syntax of the `var()` function: `var(--name, value)`  
*name* is required. It is the variable name (must start with two dashes).  
*value* is optional. The fallback value (used if the variable is not found).

```html
<!-- 13_variables.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>13</title>
    <style>
      :root {
        --bluish: #6199da;
        --space: 1rem;
      }

      .theme-night {
        --bluish: #534c7e;
      }

      .heading {
        color: var(--bluish);
      }

      .card {
        --curve: 4px;                    /* This is a local variable only for the .card elements. */

        /* If we also re-declare a global variable, it will be overridden. */
        /* --space: 3rem; */

        /*
        The calc() function performs a calculation to be used as the property value.
        It works like a charm with CSS variables :)
        */
        margin: calc(var(--space) * 2);


        padding: var(--space);
        border-radius: var(--curve);
        background-color: var(--bluish);
        color: #fff;
      }
    </style>
  </head>
  <body>

    <h1 class="heading">Hello World!</h1>
    <p>This is our sample document.</p>

    <!--
    We have re-declared the --bluish variable in the .theme-night CSS class, and
    used for our <section> element here. Now as you can see, the
    background-color of the .card element is changed to the new overridden value
    (because it is the descending child of the <section> element), while the
    color of the above .heading element has remained unchanged since we have
    declared the --bluish variable inside the :root selector.
    -->
    <section class="theme-night">
      <div class="card">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
      </div>
    </section>

  </body>
</html>
```




## Import
The `@import` rule allows you to import a style sheet into another style sheet. The `@import` rule must be at the top of the document. In large projects you need to separate your stylesheets and organize your files for better folder structure and easier future upgrades. e.g., you can put your webpages' header related styles in one file, and your footer related styles in another one, and then import both of those files into the `main.css` file that is going to be included as a reference inside your HTML pages.

The syntax of `@import` rule: `@import url|string list-of-mediaqueries;`  
e.g., `@import "header.css";` or `@import url("header.css");`

**NOTE:** We can also import a stylesheet ONLY if a certain condition of a media query (or a comma-separated list of media queries) is meet. e.g., `@import "main-md.css" screen and (min-width: 768px);` Here the "main-md.css" style sheet will be imported ONLY if the media is screen and the viewport is minimum 768 pixels.

**NOTE:** What is the difference between using CSS `@import` rule and HTML link? If you're not targeting old browsers (the browsers that don't support the CSS `@import` rule), then there's no critical difference! Based on your projects and desires, you can choose either of them.

**NOTE:** As your project grows, you need more separated stylesheets! (e.g., you may need 100 stylesheets) Then using the CSS `@import` rule or HTML link won't be efficiently! Because each time an asset is going to be downloaded on users' machines, a separated request for each asset must be sent to the server! And it causes the webpage to load slower... Actually the less a webpage sends requests, the faster it will load. So a workaround to this issue, is to use preprocessors such as [SASS](https://sass-lang.com/). While developing your project, SASS can help you have as many stylesheets as you like, and then for production, it lets you combine all of your stylesheets together in a single .css file! [Click here](https://sass-lang.com/) to learn more about SASS.

```css
/* css/14.css */

@import "14_header.css";
@import "14_footer.css";
```

```css
/* css/14_header.css */

.header {
  padding: 2rem;
  background-color: #d6bed0;
  font-size: 2.5rem;
  text-transform: capitalize;
}
```

```css
/* css/14_footer.css */

.footer {
  margin: 1rem;
  background-color: #bfd6cc;
  font-style: italic;
}
```

```html
<!-- 14_import.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>14</title>
    <link rel="stylesheet" href="./css/14.css">
  </head>
  <body>
    <header class="header">HEADER</header>
    <section>Other parts of the webpage.</section>
    <footer class="footer">FOOTER</footer>
  </body>
</html>
```




## Tips & Tricks
Ok cool! Now that we've learned almost all of the CSS basics, let's learn some useful tips & tricks that may come in handy when you're designing a real webpage :dancer:

```html
<!-- 15_tips-and-tricks.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>15</title>
    <style>
      /* ///////////////////////////////////// rem units */

      html {
        font-size: 16px;                /* rem units are based on the font-size of the html element. */
      }

      div.a {
        /*
        It's the best practice to use rem instead of em units in most of the
        times, when we like to define font sizes, margin, padding spaces, or
        positioning an element.
        By doing so, we're defining the properties' values according to the
        base-font-size, not the parent element's font-size! This simple fact,
        avoids complex conflicts later... Specially in large projects that a
        team is working on different style sheets.
        */
        margin: 1.2rem;
        padding: 2rem;

        border: 2px solid;
        border-color: red;
        background-color: #c4d5e9;
      }


      /* ///////////////////////////////////// text/element center positioning */

      .b {
        margin: 0 auto;                 /* Simple way to put an element at center */
        width: 100px;
        background-color: lightblue;
        text-align: center;             /* text align at center */
      }


      /* ///////////////////////////////////// Positioning best practices */

      .box {
        position: relative;
        width: 200px;
        background-color: #ccc;
      }

      /*
      For positioning purposes, it's the best practice to not to change the
      element's padding or margin. Instead use top, right, bottom, or left properties.

      Difference between fixed and absolute position?
      Well, by fixed positioning, the element is positioned relative to the
      browser window. By absolute positioning, the element is positioned
      relative to its first positioned (not static) ancestor element.

      As you can see in our example here, the .c element's container is the .box
      element. And .box is positioned by relative... So when .c which is the
      .box child, gets absolute position, it acts just like a fixed positioned
      element, but not relative to the browser window! It is relatively
      positioned to the .box element.
      */
      .c {
        position: absolute;
        top: 10px;
        right: 10px;
        background-color: #aaa;
      }


      /* ///////////////////////////////////// important flag */

      @media (min-width: 576px) {
        /*
        When to use the important flag? Well, sometimes you need to override a
        style somewhere else (here we're re-styling .a when viewport is wider
        than 576px), but it doesn't work! Because you have addressed your target
        element more specifically previously! So to make the re-styling work,
        you can either address your target element more specifically than
        before, or use the important flag.

        Here in our example, we already have addressed our target element by
        mentioning its element name AND its class name (div.a), but now that we
        like to override some of its styles, we addressed it by ONLY mentioning
        its class name (.a)! So in order to make the re-styling work, we need to
        either address the target element at least as specific as before
        (div.a) or like what we did here, use the important flag.

        NOTE: It's the best practice to use the important flag, as less as
        possible! So here we just wanted to show you how to use the important
        flag for the sake of an example, but it is not recommended! So just try
        to use the important flag as the final solution when overriding some
        CSS rules, when other solutions won't work!
        */
        .a {
          border-color: blue !important;
        }
      }


      /* ///////////////////////////////////// width vs max-width */

      /*
      It's the best practice to use max-width property when setting the width of
      your container element (which is an element that contains most of your
      webpage's content). Why? Because max-width sets a maximum width and also
      decreases if needed in smaller viewports.

      NOTE: In CSS width has higher priority than max-width. So if you have
      ever, set a fixed width value for an element, and like to replace it by
      max-width in a media query to let CSS decrease the width of the element
      automatically as required... First set width to auto, and then define the
      value of your max-width property. In this way, CSS reads the max-width
      property's value, and not the value of width property.
      */
      .container {
        margin: 0 auto;
        max-width: 100%;
      }
      @media (min-width: 576px) {
        .container {
          max-width: 540px;
        }
      }
      @media (min-width: 768px) {
        .container {
          max-width: 720px;
        }
      }
      @media (min-width: 992px) {
        .container {
          max-width: 960px;
        }
      }
      @media (min-width: 1200px) {
        .container {
          max-width: 1140px;
        }
      }


      /* ///////////////////////////////////// clearfix hack */

      /*
      There's a known issue in CSS that will be fixed by a known solution that
      is called clearfix! If all of the children of an element are floated
      to left or right, th background of the element disappears! Or if a
      floating element is taller than the containing element, it will overflow
      outside its container.
      To fix such issues, you can add the clearfix CSS rules to the element.
      Here in our example, we have defined the clearfix solution CSS rules for
      the .clearfix selector, and set .clearfix class for our ul element.
      If you remove this class from the ul element, you will see that its background color will disappear!
      */
      ul {
        list-style-type: square;
        list-style-position: inside;
        margin: 0;
        padding: 0;
        background-color: #aed3f0;
      }
      ul > li {
        /*
        Specifies whether an element should float to the left, right, or not at all.

        NOTE: Absolutely positioned elements ignore the float property!
        */
        float: left;

        margin-left: 1rem;
      }

      .clearfix::after {
        content: '';
        clear: both;
        display: table;
      }


      /* ///////////////////////////////////// Smoother transitions & animations */

      @keyframes anibox {
        from { background-color: #f0bbc8; }
        20% { background-color: #cfbbf0; }
        40% { background-color: #bbcbf0; }
        60% { background-color: #bbf0db; }
        80% { background-color: #f0eabb; }
        to { background-color: #f0c6bb; }
      }

      .anibox {
        padding: 1rem;
        width: 100%;
        height: 100px;
        text-align: center;
        animation: anibox 5s ease 0s infinite alternate;
        transition: all .5s cubic-bezier(0.86,0,0.07,1);

        /*
        Properties that don't trigger repaints, can help us create extremely
        smooth animations on the web by increasing the performance. To do so, we
        should let the browser know to do some tasks on our GPU, and let the CPU
        handle other things. So we need to get hardware acceleration on our CSS
        transitions & animations. Defining one of the following CSS rules for
        our element (not all are necessary, only one is enough) will get
        hardware acceleration: `perspective: 1000px;`,
        `backface-visibility: hidden;`, `transform: translateZ(0.1);`

        Here in our example, as you can see we have set
        `backface-visibility: hidden;` CSS rule for our animated element. Well,
        you may not see any obvious results here because our animation is
        simple. But this solution can make huge difference in complex CSS animations.
        */
        backface-visibility: hidden;

        /*
        If you like to use the transform property to translate() or scale() your
        element, you may see that the texts inside the element may not look
        accurate while the animation is running! In order to avoid such jaggy
        animation, we need to define the will-change CSS property for our
        element and set its value, the CSS property that is causing the element
        to animate! (in our case it's the transform CSS property)

        The will-change propery improves the animation performance by letting
        the browser to be already prepared for changing a CSS property (the
        propery that is defined as the value of the will-change)
        */
        will-change: transform;
      }

      .anibox:hover {
        transform: scale(.95);
      }


      /* ///////////////////////////////////// Browser supports */

      .hero {
        width: 100%;
        padding: 2rem;
        background: url('hero.jpg') center/cover no-repeat scroll;
      }

      .glassy {
        padding: 2rem;
        border-radius: 8px;
        background-color: rgba(51, 51, 51, 0.8);
        color: #fff;
      }

      /*
      We can test if the browser supports a particular property or 
      property:value combination or not. e.g., `@supports (display: grid) { .a { display: grid; } }`
      */
      @supports ((-webkit-backdrop-filter: none) or (backdrop-filter: none)) {
        .glassy {
          background-color: rgba(51, 51, 51, 0.1);
          -webkit-backdrop-filter: blur(10px); /* What is it? Webkit vendor prefix! It's just a way to let browsers support new CSS features early. */
          backdrop-filter: blur(10px);
        }
      }


      /* ///////////////////////////////////// Some normalizations */

      *,
      *::before,
      *::after {
        /*
        The box-sizing property defines how the width and height of an element
        are calculated: Should they include padding and borders, or not.
        The default value of box-sizing property is content-box. But here we
        changed it to border-box so that the elements' width is not affected by
        padding or border.
        */
        box-sizing: border-box;
      }

      /*
      The ::selection selector matches the portion of an element that is
      selected by a user.
      Only a few CSS properties can be applied to the ::selection selector:
      color, background, cursor, and outline.
      */
      ::selection {
        background: #d6edff;
        text-shadow: none;
        color: #000;
      }

      html {
        overflow-y: scroll;             /* Always show the vertical scrollbar. */
      }

      body {
      	-webkit-font-smoothing: antialiased; /* Makes fonts smooth and beautiful. */
      }

      input,
      textarea,
      select {
        /* This removes the thick halo that some browsers add to the form fields when they are focused. */
        outline: none;
      }

      h1, h2, h3, h4, h5, h6 {
        /* It's good to have a bottom margin for our headings most of the times. */
        margin-bottom: 1.5rem;
      }

      p {
        /* In most of the designs, we need to seperate the paragraphs visually. */
        margin-bottom: 1.5rem;
      }

      a {
        color: orange;
        text-decoration: none;
      }
      a:hover {
        /* A simple trick to customize the underline of the hyperlinks. */
        border-bottom: 1px dotted;
      }
    </style>
  </head>
  <body>

    <div class="a">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</div>

    <div class="b">I am standing at the center horizontally.</div>

    <div class="box">
      <div class="c">I am absolute positioned element.</div>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco.
    </div>

    <hr>

    <section class="container">
      <p>Lorem ipsum dolor sit amet, <a href="#">consectetur adipisicing</a> elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
    </section>

    <hr>

    <ul class="clearfix">
      <li>List Item 01</li>
      <li>List Item 02</li>
      <li>List Item 03</li>
    </ul>

    <hr>

    <div class="anibox">
      Animated box :)
    </div>

    <hr>

    <section class="hero">
      <div class="glassy">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
      </div>
    </section>

  </body>
</html>
```




## Scalable & Modular Architecture for CSS (SMACSS) Methodology
Alright, you have learnt almost everything about the CSS basics! Now is the time to go a little bit deeper and take a look at some more advanced topics such as the SMACSS methodology! It helps us write better CSS :partying_face:

**SMACSS (pronounced "smacks") is a style guide that attempts to document a consistent approach to site/app development when using CSS**! It helps us better structure our CSS files in small or huge project, change our mindset to be more Object-oriented design (OOD) like, and build our projects in a way to be more recognizable even if we take a look at them after a long period of time.

Here I'm not going too deep into SMACSS! I just try to quickly mention some of its most important suggestions and best practices that most of the projects take into considerations. So if you like to learn more about SMACSS, [click here](http://smacss.com/), download its book, and start reading it!


### Folder structure
As I said earlier, as your project grows, you may need to use a CSS preprocessor (such as SASS) and need more and more stylesheets to style different stuff! Such as layouts, modules, states, and etc.

We can use different folder structures to organize all of these stylesheets, there's no strict rule from God to tell us how we should organize our own project! So here we're just mentioning a sample folder structure that you can use for your project, while considering the  SMACSS methodology:

- 'base' folder: Here we should put very basic stylesheets, such as normalizing styles or our default styles for the project. We usually use element selector when styling for such purposes.  
e.g., `p { margin-bottom: 1.5rem; }`

- 'layout' folder: Here we should put the styles related to our design layout, such as text related styles or positioning styles.  
e.g., `.l-inline { display: inline; }`

- 'modules' folder: Here we should put the styles related to our modules (some CSS rules that are supposed to style a semantic element), such as buttons, cards, dropdowns, forms, dividers, and etc.  
e.g., `.btn { text-align: center; }`

- 'state' folder: Here we should put the styles regarding different states of elements. As an example here we define how an element should look like in small screens or when it's appeared on sidebar rather than main section. Generally There are three types of state change: class, pseudo-class, and media query.  
e.g., `.is-pressed { transform: translate(0, 4px); }`

- 'theme' folder: Here we should take care of the coloring and feel of our webpages.  
e.g., `.theme-dark { background-color: #333; }`

- 'utilities' folder: Here we put some of the project's useful files that are going to be used in different other stylesheets. Files that include stylesheets' variables, mixins, or functions, such as '_variables.scss', '_mixins.scss', or '_functions.scss'. (These files can be created and imported in different stylesheets in SASS projects)


### Best practices
- We should avoid styling elements or IDs most of the times, except in some rare situations like when we're styling general layout or default elements' designs (normalizing). Instead we should **style class selectors**. This approach helps our styles to be independent from the HTML structure. 

- So generally we should avoid styling elements! But **if we like to style elements, then it's better to style a semantic element**! Such as the headings or p, NOT div or span elements.

- **Use Child Selector instead of Descendant Selector** most of the times. Because we may expand our HTML structure in the future and Child Selector will avoid conflicts, rather than the Descendant Selector which may be the cause of conflicts in the future, when we will add more descending elements into our HTML structure.

- **For styling a module** (e.g., `.btn`) **in a specific situation**, **use a sub-class name** for that module (e.g., `.btn-default`) and use both classes in the HTML part (e.g., `<button class="btn btn-default" type="button" name="search">Search</button>`). In this way, we not only keep our stylesheets simpler, but also add much more semantic into our HTML.

- **Keep media query related styles of a module, with other styles related to that module** itself to find everything about the module easier and at one place. There's no need to ONLY have one media query and style everything in it.

- **Use the important flag as less as possible even when facing complicated inheritance**! As an example when a parent element (e.g., `.cal`) has a CSS rule that its descending element (e.g., `.cal-today`) overrides it... We need to address the child element more specifically (e.g., `.cal .cal-today`), so that our style can be applied, otherwise our style won't work, because there is a more general style that is leading our style.

- **Avoid too much nested styles**, because it forces us to rely deeply on the HTML structure! **On the other hand, we don't always need to style everything using only classes**! Try to keep a balance between them... Depending on our project, we may not always like to give classes to every little element in order to style it! Instead we may like some elements to get your desired styles automatically! And that's why we can style elements themselves too. But remember to not go so deep relying on the HTML structure! Make sure to start styling a child from the nearest parent element.


### Styling icons
When we need icons or some repeatable images that we're going to use often in different parts of our webpages, we can make a sprite image (a collection of images put into a single image) and by CSS, show only some parts of the sprite image, each time we like to use it. Now, we may change our sprite image in the future and add more icons to it... We may also use icons in different sizes, colors, and etc. So icons should be independent from the HTML structure, and also greatly styled for future changes.

So to achieve a better OOD icon module, we can create our sprite image, and then define some CSS classes like our sample here in the following:
```css
.ico {display: inline-block; background: url('img/sprite.png') no-repeat; line-height: 0; vertical-align: bottom;}
.ico-16 {height: 16px; width: 16px;}
.ico-inbox {background-position: 20px 20px;}
```
Now in HTML we can use an icon like this: `<i class="ico ico-16 ico-inbox"></i>`. In this way, we can have a single sprite image, have icons in different sizes, and be completely independent from the HTML structure.


### Grouping properties
When defining variety of CSS properties for an element (such as border, background, font-size, and etc.), it doesn't matter you put what property first and what property last! But it's always good to be consistent. So as an example we can organize our CSS rules for an element in the following order:
1. Box (positioning) related styles.
2. Border related styles.
3. Background related styles.
4. Font and text related styles.
5. Other styles.




## BEM Methodology
There are plenty of methodologies out there aiming to reduce the CSS footprint, organize cooperation among programmers and maintain large CSS codebases. One of them is BEM! And I and many others love it :heart:

Here I just quickly let you know what BEM means and how its naming convention makes CSS fun again! So if you like to learn more about BEM, [click here](https://en.bem.info/methodology/)

**BEM is an abbreviation of the key elements of the methodology — Block, Element and Modifier**.
- Block: Standalone entity that is meaningful on its own. e.g., header, container, menu, checkbox, input.
- Element: A part of a block that has no standalone meaning and is semantically tied to its block. e.g., menu item, list item, checkbox caption, header title.
- Modifier: A flag on a block or element. Use them to change appearance or behavior. e.g., disabled, highlighted, checked, fixed, size big, color yellow.


### Naming convention
Having a standard naming convention can significantly increase development speed, debugging, and the implementation of new features in legacy code. The BEM approach does that all while keeping simple things simple.

- **Block**: A block name follows the `block-name` scheme. e.g., `.menu`, `.lang-switcher`.

- **Element**: An element name must identify its belonging to the block. It is delimited by a double underscore (`__`). The full name of an element is created using this scheme: `block-name__elem-name`. e.g., `.menu__item`, `.lang-switcher__lang-icon`.

- **Modifier**: A modifier name must identify its belonging to the block or its element. It is delimited by double hyphens (`--`). The full name of a modifier is created using the following schemes:
  - Block modifier: `block-name--mod-name`. e.g., `.menu--hidden`.
  - Element modifier: `block-name__elem-name--mod-name`. e.g., `.menu__item--visible`.

This naming convention makes the name of CSS selectors as informative and clear as possible. This will help make code development and debugging easier for producers, and also make learning the project’s style guide faster for codebase users.




# What's next?
In this tutorial we learnt what is CSS, where to write it, and how to write it. We showed you some of the most frequently used CSS properties, and also talked about some of the best CSS practices that companies and teams use for a better code structure and easy future upgrades such as the SMACSS and BEM methodologies.

If you practiced with my sample codes along the way, you may be wondering now: I know HTML, and now have learned the CSS basics, and even some advanced topics! but why I still cannot create a reasonable or beautiful webpage?! Well, give yourself a little bit more time! You just learned the basics, and you need to practice more and more, so that the concepts can fall into the right place in your mind...

You also need to know a little bit about UI/UX as well, to be a professional web designer! Knowing only HTML & CSS lets you convert an already photoshop designed image of a webpage into code and a real world working webpage; but knowing UI/UX lets you design even that photoshop image and design everything from zero to hero! So if you're wondering why you cannot use your HTML & CSS coding skills to build a beautiful webpage, don't wonder! It's because you don't have UI/UX skills yet! In order to know what HTML structure you have to write, and what CSS rules you need to write in order to style those HTML elements... First you need to have a ready beautifully designed image of a webpage right in front of your eyes! And designing that image, needs you to have UI/UX skills! Now, talking about UI/UX is out of the scope of this tutorial here, though I also provide you some useful resources that you can check out by yourself later at the end of this tutorial, if you like to learn about these topics as well...

Now **you still need to learn and practice more**. Your next step to become a web designer or frontend developer is to also learn JavaScript. And JavaScript tutorial, is what I'm going to provide next :smile:

But before we go to learn JavaScript... Do you like to level up your CSS learnings? If so, you can checkout the following resources:

* [W3schools CSS Tutorial](https://www.w3schools.com/css/default.asp)
* [SASS Language (a CSS Preprocessor)](https://sass-lang.com/)
* [Scalable & Modular Architecture for CSS (SMACSS) Methodology](http://smacss.com/)
* [BEM Methodology](https://en.bem.info/methodology/)
* ["What is UX Design?" tutorial](https://webdesign.tutsplus.com/articles/what-is-ux-design--cms-37111)
* ["Mobile UI Design for Beginners" tutorial](https://webdesign.tutsplus.com/articles/new-course-mobile-ui-design-for-beginners--cms-25610)
* ["What is Adobe XD?" tutorial](https://webdesign.tutsplus.com/articles/what-is-adobe-xd--cms-36536)
* ["How to Create a Banking App Prototype in Adobe XD" tutorial](https://webdesign.tutsplus.com/tutorials/how-to-create-a-banking-app-prototype-in-adobe-xd--cms-93174)
