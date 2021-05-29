---
title: HTML Questions
layout: layouts/page.njk
permalink: /questions/html-questions/index.html
---

* What does a `doctype` do?
  The HTML document type declaration, also known as DOCTYPE , is the first line of code required in every HTML or XHTML document. The DOCTYPE declaration is an instruction to the web browser about what version of HTML the page is written in. This ensures that the web page is parsed the same way by different web browsers.
* How do you serve a page with content in multiple languages?
  1. Explicitly by setting header of HTTP request Accept-Language
  2. Set charset and lang in meta tag for proper language display
  3. Set lang attr in links for SEO dedupe
* What kind of things must you be wary of when designing or developing for multilingual sites?
  1. Don't use text in images
  2. Restrictive word/sentence length 
  3. Don't hardcode text, use dynamic templating
* What are `data-` attributes good for? 
  1. Holding data for custom functionality and custom components.
  2. Data in the HTML accessible to JS and CSS
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
  1. Tags - define the start and end of elements and what it wraps
  2. Attributes - describe traits of the element
  3. Elements - what part of the document feature, like paragraph or header etc.
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
  1. script - download synchronously (after HTML parsed)
  2. script async - download asynchronously HTML parsing and exec immediately
  3. script defer - async loading of js but defers execution for after HTML parsed
  https://ourcodeworld.com/articles/read/1379/what-is-the-difference-between-the-async-and-defer-attributes-in-javascript

  With defer on a script in the head, the JavaScript file will download in the background while the rest of the DOM is parsed and rendered. When you get to the bottom of the page, the JS file is already downloaded and ready to run.
  https://gomakethings.com/when-should-you-add-the-defer-attribute-to-the-script-element/
  
* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
  Don't want the CSS to appear after the DOM loads, it'll look janky. 
  Also, JS typically needs to select elements, attributes, classes, etc. to apply so it's better to have the HTML load before the JS starts initializing or selecting.
* What is progressive rendering?
  Prioritizing data load on client side in chunks of data to get faster load times. Some ways to achieve this is to load chunks and wait for certain load events to load the less necessary data afterwards. Also lazy loading.
* Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
* Have you used different HTML templating languages before?
  I've played with pug and jade. I've never used the professionally.
* What is the difference between `canvas` and `svg`?
  SVG: scalable vector graphics. Good for sharp logos and icons and simple animations.
  Canvas: used to draw 2D shapes and render images. Holds state and easily accessible with JS. Good for games.
* What are empty elements in HTML ?
  Cannot have any child nodes.
<area>
<base>
<br>
<col>
<embed>
<hr>
<img>
<input>
<keygen>(HTML 5.2 Draft removed)
<link>
<meta>
<param>
<source>
<track>
<wbr>
