**Sass for Web Designers** by *Dan Cederholm*

To Erin Kissane, thank you for making me sound like a better writer than I actually am. It’s been an honor to have you do that. And to Jina Bolton for being a wonderful technical editor and ambassador for Sass.

---

Here’s the retinize mixin I use in my everyday projects—I’ll break down each important section. @mixin retinize($file, $type, $width, $height) { background-image: url('../img/' + $file + '.' + $type); @media (-webkit-min-device-pixel-ratio: 1.5), (min--moz-device-pixel-ratio: 1.5), (-o-min-device-pixel-ratio: 3/2), (min-device-pixel-ratio: 1.5), (min-resolution: 1.5dppx) { & { background-image: url('../img/' + $file + '-2x.' + $type); -webkit-background-size: $width $height; -moz-background-size: $width $height; background-size: $width $height; }

---

#content { float: left; width: 70%; @include responsive(wide-screens) { width: 80%; } @include responsive(medium-screens) { width: 50%; font-size: 14px; } @include responsive(small-screens) { float: none; width: 100%; font-size: 12px; } } Which will compile to: #content { float: left; width: 70%; } @media only screen and (max-width: 1200px) { #content { width: 80%; } }

---

Combining @content blocks and mixins By using Sass’s @content directive, you can pass entire blocks of styles to a mixin, and Sass will place those blocks back into the declaration that calls the mixin. That sounds confusing, but in practice it’s simple and handy. Let’s create a responsive mixin that handles three different breakpoints, with @content placeholders for whatever styles we’d like to include for each breakpoint. We’ll also use variables to define the small, medium, and large breakpoint widths as we did earlier in the chapter. $width-small: 400px; $width-medium: 760px; $width-large: 1200px; @mixin responsive($width) { @if $width == wide-screens { @media only screen and (max-width: $width-large) { @content; } } @else if $width == medium-screens { @media only screen and (max-width: $width-medium) { @content; } } @else if $width == small-screens { @media only screen and (max-width: $width-small) { @content; } } } Notice Sass also supports @if and @else statements, which we’re using to evaluate the $width variable we’ll pass when including the mixin. For example, if we pass the mixin the medium-screens variable, Sass will compile the media query with our max-width set to the $width-medium variable (760px). The @content placeholder allows us to further pass blocks of styles to the mixin that get inserted inside the media query. With this single mixin set up, we can now call it from any declaration using a compact pattern that reflects the way we think about things:

---

Going a step further, you can also define an entire media query as a variable (not just the numeric value): $mobile-first: "screen and (min-width: 300px)"; @media #{$mobile-first} { #content { font-size: 14px; line-height: 1.5; } } Notice the interpolation brackets—#{}—surrounding the $mobile-first variable. That’s a special way to alert Sass to compile something within a selector or property name. The above SCSS will compile to: @media screen and (min-width: 300px) { #content { font-size: 14px; line-height: 1.5; } }

---

Using placeholder selectors with @extend What if the class you’re extending exists solely for the purpose of extending other styles? In other words, you might create a class that’s not used on its own. Enter placeholder selectors, which allow you to define “phantom” classes that won’t appear in the outputted CSS on their own. You can reference placeholders using @extend. Let’s take a look at this in practice. We’ll create a class for a block of styles that define a button. We’ll use a placeholder selector, which in Sass means prefixing the class name with a % instead of a period. %button { padding: 10px; font-weight: bold; background: blue; border-radius: 6px; } We can call this rule set in other classes as we did previously, using @extend. .buy { @extend %button; } .submit { @extend %button; background: green; } Sass will compile this like an extended class, but the %button placeholder rule set won’t appear in the output: .buy, .submit { padding: 10px; font-weight: bold; background: blue; border-radius: 6px; } .submit { background: green; }

---

@mixin linear-gradient($from, $to) { /* Fallback for sad browsers */ background-color: $to; /* Mozilla Firefox */ background-image:-moz-linear-gradient($from, $to); /* Opera */ background-image:-o-linear-gradient($from, $to); /* WebKit (Safari 4+, Chrome 1+) */ background-image:-webkit-gradient(linear, left top, left bottom, color-stop(0, $from), color-stop(1, $to)); /* WebKit (Chrome 11+) */ background-image: -webkit-linear-gradient($from, $to); /* IE10 */ background-image: -ms-linear-gradient($from, $to); /* W3C */ background-image: linear-gradient($from, $to); } Notice that I’m using the $to color to specify the background-color fallback for browsers that don’t support CSS gradients. Thankfully, we only have to write this monstrosity once. Now, when we want to create a simple linear gradient, we just call the mixin with two colors of our choosing and Sass does the rest. For the Sasquatch site, the declaration for the active tab style goes like this: &.active a { padding: 3px 8px; color: #fff; @include rounded(4px); @include linear-gradient(#ff70b1, #d42a78); }

---

Defining defaults for arguments When you use mixin arguments, it’s often convenient to define defaults. That way, you simply call the mixin with no arguments, if that’s the norm, but can still pass in overrides. @mixin title-style($color, $background: #eee) { margin: 0 0 20px 0; font-family: $font-serif; font-size: 20px; font-weight: bold; text-transform: uppercase; color: $color; background: $background;

---

Mixin arguments Sass mixins can also take arguments that we pass to the mixin when we call it. For example, let’s add an argument for specifying a color along with our title-style mixin. Specify arguments with variables inside parentheses when defining the mixin: @mixin title-style($color) { margin: 0 0 20px 0; font-family: $font-serif; font-size: 20px; font-weight: bold; text-transform: uppercase; color: $color; } When calling the mixin, we can now pass a color to it (here a lovely burnt orange), along with the other rules: section.main h2 { @include title-style(#c63); }

---

First, we’ll define a mixin in Sass using the @mixin directive at the top of the .scss file. I’ll name it title-style, and I’ll define the rules for margins and fonts: @mixin title-style { margin: 0 0 20px 0; font-family: $font-serif; font-size: 20px; font-weight: bold; text-transform: uppercase; } Once it’s defined, we can now refer to this mixin anywhere we’d like to insert those styles by using the @include directive. On the Sasquatch site, we have a section of the stylesheet that defines rules for the page’s main section, and we want the mixin to style all <h2> elements: section.main h2 { @include title-style; } This will compile to: section.main h2 { margin: 0 0 20px 0; font-family: Jubilat, Georgia, serif; font-size: 20px; font-weight: bold; text-transform: uppercase; } But we also want to style <h3> elements in the sidebar the exact same way. So, later in the stylesheet we can call the same mixin, which will compile the same rules: section.secondary h3 { @include title-style; } This lets us avoid duplicating the shared styles—or adding a class to the markup that both headings could theoretically share.

---

Using variables for style guides Jina Bolton wrote a great article on how Sass variables can help with creating a style guide from a brand palette (http://bkaprt.com/sass/10/). Says Jina: To keep our style guide relevant, it lives in our internal-only admin section on the very same application it describes. We display our color palette alongside the relevant Sass variables and since we’ve built the style guide into the application using the same front-end, we can use the same variables we’re referencing to render this palette. When we change values to these variables, the palette updates automatically (Fig 3.2). FIG 3.2: Jina Bolton uses Sass to help create style guides.

---

The ampersand is also useful in inserting overrides that happen in the presence of a specific class. For example, let’s say we style paragraphs in the main section of the site, but we want a slightly different style on a specific page. We add a class to the body, and then we can use the ampersand to slip this overriding declaration into the main one: section.main p { margin: 0 0 20px 0; font-size: 18px; line-height: 1.5; body.store & { font-size: 16px;

---

Similarly, there are many properties in the text- namespace. We can use Sass nesting to save some retyping: text: { transform: uppercase; decoration: underline; align: center; } And background- is another good example: background: { color: #ea4c89; size: 16px 16px; image: url(sasquatch.png); repeat: no-repeat; position: top left; }

---

In addition to nesting rules, you can nest properties that share a namespace in Sass (e.g., font-family, font-size, font-weight, etc.) like so: header[role="banner"] h1 { padding: 15px 0; font: { size: 54px; family: Jubilat, Georgia, serif; weight: bold; } line-height: 1; } That’ll compile to: header[role="banner"] h1 { padding: 15px 0; font-size: 54px; font-family: Jubilat, Georgia, serif; font-weight: bold; line-height: 1; }

---

$ gem install sass --pre

---

You can also choose to live on the bleeding edge, and install the latest alpha version by adding a pre flag at the end of the command. Using the latest alpha is not only safe, but it also enables you to take advantage of the latest functionality.

---

Part of the problem is that CSS wasn’t originally designed to do the things we do with it today.

---

Our stylesheets are also immensely repetitive. Colors, fonts, oft-used groupings of properties, etc. The typical CSS file is an extremely linear document—the kind of thing that makes an object-oriented programmer want to tear their hair out. (I’m not an object-oriented programmer, but I have very little hair left. Read into that as you may).

---

The float property, for example, was designed to simply align an image within a block of text. That’s it. Yet we’ve had to bend that property to lay out entire interfaces.

---

