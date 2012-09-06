Mixd CSS Framework
==================

Mixd's framework for beginning any front end build &mdash; containing HTML5, Sass &amp; CSS files, jQuery and a pattern / module library. Use of this framework should adhere to the following rules which complement its architecture **based around Jonathan Snook's [SMACSS](http://smacss.com/)**

## License

- This work is licensed under a [Creative Commons Attribution-NonCommercial 3.0 Unported License](http://creativecommons.org/licenses/by-nc/3.0/deed.en_US)
- You must attribute the work in the manner specified by the author or licensor (but not in any way that suggests that they endorse you or your use of the work)

## Pre-Processing

- Code CSS via [Sass](http://sass-lang.com/) using the `.scss` files in the `/assets/sass` folder, then compile to CSS
- We recommend [CodeKit](http://incident57.com/codekit/) as a compiler for Mac
- Directly compiled stylesheets sit at root level in the `/sass` folder, with all other separations inside sub folders
- CSS should compile to the `/css` folder and will be minified upon launch.

## Configuration

- **This is a good starting point** (`/config`)
- Global variables are set in `vars.scss` e.g. colours, font families etc.
- Place **any variables** you use during the project here, and **any mixins** within `mixins.scss`
- Import any external mixin libraries within `includes.scss`

## Global styles

- Coding small-screen first, all default styles sit within the `/global` folder
- Global styles are categorised into separations as per [SMACSS](http://smacss.com/): 

## Base

- [Normalize.css](http://necolas.github.com/normalize.css/) is used to create consistency across all browsers
- Project defaults are then set as reasonable starting point, but should be changed if needed
- Helper classes are used to alter global typographic styles when required or unset defaults e.g. `.unset-list` removes `list-style` and `margin-left`

## Layout

- Layout rules define major content areas e.g. container, header, footer and grids.
- Use `.l-` class prefix when indicating layout changes above the default e.g. `.l-full-width`
- *Layout* is reserved for layout components only, use nested elements or target modules within *theme* for appearance

**Read:**
* [goo.gl/S5inY](http://goo.gl/S5inY)

### Proportional Grids

This framework uses Matt Berridge's [Proportional Grids](http://builtbyboon.com/blog/proportional-grids) for layout. Classes are used on each grid column to determine which proportion is taken at which breakpoint e.g.

	<div class="grid-wrap">
	    <div class="grid-col bp1-col-one-half bp2-col-two-thirds">
	        <p>Column 1</p>
	    </div>
	    <div class="grid-col bp1-col-one-half bp2-col-one-third">
	        <p>Column 2</p>
	    </div>
	</div>
	
Here, `grid-col` starts life as a single column. The class `bp1-col-one-half` means that column becomes one-half at breakpoint 1. `bp2-col-two-thirds` means it becomes two-thirds at breakpoint 2. And so on.

`bp2-col` is simply a namespace / prefix for that breakpoint. Grids are configured in `layout.scss` for each breakpoint, setting the namespace of the grid class to be used.	

## Modules

- **This is where the bulk of your css will go**
- Modules (e.g. `.panel`) lie inside layout components and can **always** be moved to a different part of the page without breaking
- Use classes to define modules and prefix any child elements e.g. `.panel-heading` inside `.panel`, `.nav-item` inside `.nav`
- Objects are re-useable abstractions that do one job. First, look for existing objects to help you build a new module
- Common modules are included by default and explained
- When building modules, consider re-use and create abstractions if necessary
- **Don't modify a base object** once created. Either extend it for your module or don't use it.
- Use *theme* to define background, typography, colour styles even if they relate to a module
- Use explicit properties e.g. `border-width`, `border-style`, then define `border-color` in *theme*
- Use *state* to define e.g. `:hover`, `:active` styles even if they relate to a module

**Read:**
- [goo.gl/QKEuz](http://goo.gl/QKEuz)
- [goo.gl/tTQJg](http://goo.gl/tTQJg)

### Mixd Modules

`/libs/mixd-modules.scss` contains mixins for common modules and details of accompanying markup. Should you produce any potentially re-useable / useful modules, update this file in the [master repository](https://github.com/Mixd/Mixd-CSS-Framework) after project completion. This allows for greater re-use of code between projects.

Modules should **only** contain structure and layout with **no theme styles** (defined by explicit CSS properties). *Theme* for each module can then be added on a per-project basis, with a full view of that project's cascade prior to styling.

## Theme

- **This is where you define appearance**
- Theme rules define look and feel e.g. tyopgraphy, background, colour etc.
- Use explicit properties e.g. `border-color` **not** `border` to style elements specifically
- Keeping *theme* separately allows for the extraction and re-use of *modules* between projects

**Read:**
* [goo.gl/ThLKb](http://goo.gl/ThLKb)

### Icon Fonts

## State



## CMS



## Modernizr

## Breakpoints

- Each breakpoint has its own separation within `/states`
- **Create breakpoints when content requires**, not for specific devices or screen-sizes
- Four breakpoints are set up by default &mdash; primarily work small-screen upwards using `min-width`
- Each breakpoint should have its own separate stylesheet with **one `@media` query per breakpoint**, rather than multiple `@media` queries per element
- Use a prefix for breakpoint-specific classes (e.g. `.bp1-cols-full`) to serve styles *only* at a given breakpoint upwards

## Internet Explorer

- IE8 and below is served a fixed-width, 960px wide container compiling styles from each breakpoint (up to desktop) in `ie.scss`
- When you add a new breakpoint you wish to include in IE &mdash; include it in `ie.scss`
- Older IE (below IE7) recieves a fixed-width *mobile* version via styles in `oldie.scss`
- Serve additional IE7 &amp; 8 styles **only** in `ie.scss` using relevant classes on the `<html>` element
- Support for Proportioanal Grids is also added via mixin for each breakpoint
- **Never polyfill IE with media query support**

## Javascript

## External Libraries

This framework makes use of the following external libraries or services

- [Normalize.css](http://necolas.github.com/normalize.css/)
- [Proportional Grids](https://github.com/mattberridge/Proportional-Grids/)
- [Modernizr](http://modernizr.com/)
- [Selectivizr](http://selectivizr.com/)
- [Fontello](http://fontello.com/)

## Pattern library

---------------------------------------

# General CSS notes, advice and guidelines

Listen below are some general rules to adhere to when using this framework or when completing any front end work. Extracts are taken from [CSS Guidelines](https://github.com/csswizardry/CSS-Guidelines/blob/master/CSS%20Guidelines.md) written by Harry Roberts.

## Syntax and formatting

Use multi-line CSS to help with version control (diffing single line CSS is a nightmare) and we order CSS declarations by relevance, **not** alphabetically.

Use hyphen delimited, lowercase selectors: `.thisIsBad{}`, `.this_is_also_bad{}` but `.this-is-correct{}`.

Always use a trailing semi-colon on the last declaration in a ruleset to avoid any potential confusion and syntax errors over the life of the document.

Here is the preferred convention and structure for defining CSS rules, comments and nested elements within Sass:

	/* Tertiary Nav
	----------------------------------*/
	.nav-tertiary {
	
		a {
			padding: 0 .75em; }
			
		:first-child a {
			padding-left: 0; }	
	}
	
	/* Blocked Nav Object
	----------------------------------*/
	.nav-blocked a {
		display: block;
		padding: .5em; }

## Comments

Comment as much as you can as often as you can. Where it might be useful, include a commented piece of markup which can help put the current CSS into context.

Be verbose, go wild, CSS will be minified before it hits live servers.

## Building components

When building a new component write markup **before** CSS. This means you can visually see which CSS properties are naturally inherited and thus avoid reapplying redundant styles. Look for existing modules or objects to work with before beginning and always comment a new module with a title.

## OOCSS

When building components try and keep a DRY, OO frame of mind. **Adding classes is not a crime** - use them wisely and efficiently.

Instead of building dozens of unique components, try and spot repeated design patterns abstract them; build these skeletons as base objects and then peg classes onto these to extend their styling for more unique circumstances.

If you have to build a new component split it into structure (modules) and skin (theme); build the structure of the component using very generic classes so that we can reuse that construct and then use more specific classes to skin it up and add design treatments.

**Read:**

* [csswizardry.com/&hellip;/the-nav-abstraction](http://csswizardry.com/2011/09/the-nav-abstraction)
* [stubbornella.org/&hellip;/the-media-object-saves-hundreds-of-lines-of-code](http://stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code)

## Layout

All components should be left totally free of widths; your components should always remain fluid and their widths should be governed by a grid system.

Heights should **never** be be applied to elements. Heights should only be applied to things which had dimensions _before_ they entered the site (i.e. images and sprites). Never ever set heights on `<p>`s, `<ul>`s, `<div>`s, anything. You can normally achieve the desired effect with `line-height` which is far more flexible.

Grid systems should be thought of as shelves. They contain content but are not content in themselves. You put up your shelves then fill them with your stuff.

You should never apply any styles to a grid or layout container, they are for layout purposes only. Nest modules inside layout components.

## Sizing

**Never use pixels** unless unavoidable. Use a combination of `ems`, `rems` and percentages. Only use `rems` if you need to reference a base measure e.g. to make padding equal more easily 

**Read:**

* [csswizardry.com/&hellip;/measuring-and-sizing-uis-2011-style](http://csswizardry.com/2011/12/measuring-and-sizing-uis-2011-style)

## Font sizing

Set a *relevant* default font-size on the `<html>` element to supply global typographic elements. From there, use `ems` to define font sizing &mdash; **do not define any font sizes in pixels**. Define line heights unitlessly everywhere **unless** we are trying to align text to known heights.

Do not use `rems` for font-sizing unless absolutely necessary due to compound nesting. If using `rems` - provide pixel/<`em>` fallback for IE using the Modernizr `.no-remunit` class. 

We want to avoid defining font sizes over and over; to achieve this we have a predefined scale of font sizes tethered to classes. We can recycle these rather than having to declare styles over and over.

Before writing another font-size declaration, see if a class for it already exists.

**Read:**

* [csswizardry.com/&hellip;/pragmatic-practical-font-sizing-in-css](http://csswizardry.com/2012/02/pragmatic-practical-font-sizing-in-css)

## Shorthand

It might be tempting to use declarations like `background: red;` but in doing so what you are actually saying is *I want no image to scroll, aligned top left and repeating X and Y and a background colour of red*. Nine times out of ten this won't cause any issues but that one time it does is annoying enough to warrant not using such shorthand. Instead use `background-color: red;`.

Similarly, declarations like `margin: 0;` are nice and short, but **be explicit**. If you're actually only really wanting to affect the margin on the bottom of an element then it is more appropriate to use `margin-bottom: 0;`.

Be explicit in which properties you set and take care to not inadvertently unset others with shorthand. E.g. if you only want to remove the bottom margin on an element then there is no sense in blitzing all margins with `margin: 0;`.

Shorthand is good, but easily misused.

## Selectors

Keep selectors efficient and portable.

Heavily location-based selectors are bad for a number of reasons. For example, take `.sidebar h3 span {}`. This selector is too location-based and thus we cannot move that `span` outside of a `h3` outside of `.sidebar` and maintain styling.

Selectors which are too long also introduce performance issues; the more checks in a selector (e.g. `.sidebar h3 span` has three checks, `.content ul p a` has four), the more work the browser has to do.

Make sure styles aren't dependent on location where possible, and make sure selectors are nice and short.

**Remember:** classes are neither semantic or insemantic; they are sensible or insensible! Stop stressing about *semantic* class names and pick something sensible and futureproof.

**Read:**

* [speakerdeck.com/&hellip;/breaking-good-habits](http://speakerdeck.com/u/csswizardry/p/breaking-good-habits)
* [csswizardry.com/&hellip;/writing-efficient-css-selectors](http://csswizardry.com/2011/09/writing-efficient-css-selectors)

### Over-qualified selectors

An over-qualified selector is one like `div.promo`. We could probably get the same effect from just using `.promo`. Of course sometimes we will _want_ to qualify a class with an element (e.g. if you have a generic `.error` class that needs to look different when applied to different elements (e.g. `.error { color: red; }` `div.error { padding: 14px; }`), but generally avoid it where possible.

Another example of an over-qualified selector might be `ul.nav li a {}`. As above, we can instantly drop the `ul` and because we know `.nav` is a list, we therefore know that any `a` _must_ be in an `li`, so we can get `ul.nav li a {}` down to just `.nav a{}`.

## Be explicit, don't make assumptions

Instead of using selectors to drill down the DOM to an element, it is often best to put a class on the element you explicitly want to style. Let's take a specific example.

Imagine you have a promotional banner with a class of `.promo` and in there there is some text and call-to-action link. If there is just one `a` in the whole of `.promo` then it may be tempting to style that call-to-action via `.promo a {}`.

The problem here should be obvious in that as soon as you add a simple text link (or any other link for that matter) to the `.promo` container it will inherit the call-to-action styling, whether you want it to or not. In this case you would be best to explicitly add a class (e.g. `.cta`) to the link you want to affect.

Be explicit; target the element you want to affect, not its parent. Never assume that markup won't change.

### Key selectors should (typically) never be a type selector or an object/abstraction class

You should never find yourself writing selectors whose key selector is a type selector (e.g. `.header ul {}`) or a base object (e.g. `.header .nav {}`). This is because you can never guarantee that there will only ever be one `ul` or `.nav` in that `.header`, the key selector is too loose/too broad.

It would be more appropriate to give the element in question an explicit class targeting that one and that one only, so `.header .nav {}` would be replaced with `.site-nav`, for example.

The only time where a type selector may be appropriate is if you have a situation like this:

    a {
        color:red; }
        
    .promo {
        background-color: red; 
        color: white; }
    
    .promo a {
        color: white; }

In this case you _know_ that every `a` in `.promo` needs a blanket rule because it would be unreadable without.

**Write selectors that target what you want, not what happens to be there already.**


## IDs and classes

**Do not use IDs in CSS** at all. They can be used in your markup for JS and fragment-identifiers but use only classes for styling. We don't want to see a single ID in this (or any other) stylesheet.

Classes come with the benefit of being reusable (even if we don't want to, we can) and they have a nice, low specificity.

**Read:**

* [csswizardry.com/&hellip;/when-using-ids-can-be-a-pain-in-the-class](http://csswizardry.com/2011/09/when-using-ids-can-be-a-pain-in-the-class)


## `!important`

It is okay to use `!important` on helper classes only. To add `!important` preemptively is fine, e.g. `.error { color: red !important; }`, as you know you will **always** want this rule to take precedence.

Using `!important` reactively, e.g. to get yourself out of nasty specificity situations, is not advised. Rework your CSS and try to combat these issues by refactoring your selectors. Keeping your selectors short and avoiding IDs will help out here massively.


## Magic numbers and absolutes

A magic number is a number which is used because *it just works*. These are bad because they rarely work for any real reason and are not usually very futureproof or flexible/forgiving. They tend to fix symptoms and not problems.

For example, using `.dropdown-nav li:hover ul { top: 37px; }` to move a dropdown to the bottom of the nav on hover is bad, as 37px is a magic number. 37px only works here because in this particular scenario the `.dropdown-nav` happens to be 37px tall.

Instead we should use `.dropdown-nav li:hover ul{ top: 100%; }` which means no matter how tall the `.dropdown-nav` gets, the dropdown will always sit 100% from the top.

Every time you hard code a number think twice; if you can avoid it by using keywords or aliases (i.e. `top:100%` to mean *all the way from the top*) or &mdash; even better &mdash; no measurements at all then you probably should.

Every hard-coded measurement you set is a commitment you might not necessarily want to keep.

## Debugging

If you run into a CSS problem **take code away before you start adding more** in a bid to fix it. The problem exists in CSS that is already written, more CSS isn't the right answer!

Delete chunks of markup and CSS until your problem goes away, then you can determine which part of the code the problem lies in.

It can be tempting to put an `overflow: hidden;` on something to hide the effects of a layout quirk, but overflow was probably never the problem; **fix the problem, not its symptoms.**