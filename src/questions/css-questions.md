---
title: CSS Questions
layout: layouts/page.njk
permalink: /questions/css-questions/index.html
---
answers: https://codeburst.io/clearing-your-front-end-job-interview-css-95bdd82871f2

* What is CSS selector specificity and how does it work?
  Depending on how specific a rule is, it can overwrite the properties of a rule with less specificity. 
* What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
  Normalization creates consistency between browsers. Resetting strips all browser-assigned CSS but that doens't make the same page amongst browsers look the same.
* Describe Floats and how they work.
  Float aligns items left/right while still being a part of the web flow. Clear left/right prevents the next content from taking up space next to the floated element. The clear CSS property sets whether an element must be moved below (cleared) floating elements that precede it.
* Describe z-index and how stacking context is formed.
  The stacking context is a three-dimensional conceptualization of HTML elements along an imaginary z-axis relative to the user. Can be applied to positioned element, flex, opacity, etc. Applied z-index of child won't be higher than the applied z-index of parent. So if a cousin element has a lesser z-index than parent of higher z-index, cousin element will be on top.
* Describe BFC (Block Formatting Context) and how it works.
  The outermost element in a document that uses block layout rules establishes the first, or initial block formatting context. This means that every element inside the <html> element's block is laid out according to normal flow following the rules for block and inline layout. Elements participating in a BFC use the rules outlined by the CSS Box Model, which defines how an element's margins, borders, and padding interact with other blocks in the same context.
  Flexbox: flex containers establish flex formatting contexts.
  Grid Layout: grid containers establish grid formatting contexts.
* How would you approach fixing browser-specific styling issues?
  Use browser prefixes or an autoprefixer
* How do you serve your pages for feature-constrained browsers?
  caniuse.com
  polyfill libraries
  browser prefix
* What are the different ways to visually hide content (and make it available only for screen readers)?
  make visibility hidden
  make height/width 0
  position off the screen with absolute
* Can you give an example of an `@media` property other than `screen`?
  print 
* What are some of the "gotchas" for writing efficient CSS?
  Know that CSS page rule traversal is right form left so one needs to be specific when writing them
  Use BEM so everything has 1 class and efficient traversal
* What are the advantages/disadvantages of using CSS preprocessors?
  * Describe what you like and dislike about the CSS preprocessors you have used.
* How would you implement a web design comp that uses non-standard fonts?
* Explain how a browser determines what elements match a CSS selector.
  Browsers filter out elements in the DOM according to the key selector, and traverse up its parent elements to determine matches. The shorter the length of the selector chain, the faster the browser can determine if that element matches the selector. That's why one should try to be as specific as possible to lessen CSS traversal and page load time.
* Describe pseudo-elements and discuss what they are used for.
* Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
  How much space a block-level element takes up.
  Whether or not borders and/or margins overlap, or collapse.
  A box’s dimensions.
  display: flex
  display: grid
* What does ```* { box-sizing: border-box; }``` do? What are its advantages?
content-box: default, 
border-box: border and padding counted as part of height and width, easier to control space taken up
* What is the CSS `display` property and can you give a few examples of its use?
  Defines formatting context of element or parent and its children
  Can be used to change formatting context like flex/grid
* What's the difference between block, inline and inline-block?
  block: stacked
  inline-block: side-by-side, can set height, width, margin, padding
  inline: no height or width styles applied, only LR margin/padding
* What's the difference between the "nth-of-type()" and "nth-child()" selectors?
  nth-child can find a child position
  nth-of-type can pass odd/even or functional notation
* What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
  I like the syntax, templating, scoping, and ease of use of vue
  but i like the control of react
* Have you used CSS Grid?
* How is clearfix css property useful?
  Fixes calculated floated height and alignment of cleared items. 
* Can you explain the difference between px, em and rem as they relate to font sizing?
* Can you give an example of a pseudo class? Can you provide an example use case for a pseudo class?
Has a colon
Often a state selector
:hover, :focus, :playing, :pause
