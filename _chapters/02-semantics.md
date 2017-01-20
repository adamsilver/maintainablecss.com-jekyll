---
layout: chapter
title: Semantics
section: Background
permalink: /chapters/semantics/
description: Why naming something based on what it is, instead of how it looks or behaves is a cornerstone of writing well architected and maintainable CSS code.
---

Summary: Name something based on what it *is*, not how it *looks* or *behaves*.

## The longer explanation

Semantic HTML isn't just about the elements we use. It's quite obvious that we should use `<a>` for links, `<table>` for tabular data and `<p>` for paragraphs etc.

What's not quite so obvious is the values we use for classes. This is important because they enable us to enhance a web page with style (and behaviour).

> &ldquo;There are only two hard things in Computer Science: cache invalidation and naming things.&rdquo;
<br>&mdash; <cite>Phil Karlton</cite>

If naming something is hard, then it's important to think about it and do it well. We're not so good at understanding abbreviated, non-semantic abstractions.

## Good and bad class names

Here are some examples of semantic and non-semantic class names:

	<!-- non semantic -->
	<div class="red pull-left">
	<div class="grid row">
	<div class="col-xs-4">

	<!-- semantic -->
	<div class="basket">
	<div class="product">
	<div class="searchResults">

Non semantic classes don't tell us *what* the HTML represents. At *most*, they give us an idea of what elements *look* like. Atomic, visual, behavioural and  utility classes are all forms of non semantic classes.

Semantic classes don't tell us what they look like, but that's okay. That's what CSS is for. Semantic class names mean something to HTML, CSS, Javascript and automated functional tests.

There are many reasons why semantic classes are advantageous:

## 1. Because they are easy to understand

This is best explained with a *real* example. Here's a module of HTML using atomic classes.

	<div class="pb3 pb4-ns pt4 pt5-ns mt4 black-70 fl-l w-50-l">
	  <h1 class="f4 fw6 f1-ns lh-title measure mt0">Heading</h1>
	  <p class="f5 f4-ns fw4 b measure dib-m lh-copy">Tagline</p>
	</div>

Not only do we need to mentally map these abbreviations (assuming we know what they mean in the first place), but we need to wade through a load of classes just to work out what's going on. The content itself is somewhat obfuscated.

Also, visual class names are ambiguous. For example, `.red` could mean red text, a red background or perhaps a reddish gradient. It's hard to be sure.

Here's the same thing using semantic classes:

	<div class="hero">
	  <h1 class="hero-heading">Heading</h1>
	  <p class="hero-tagline">Tagline</p>
	</div>

This is easy to read and we can inspect styles easily with browser tools.

## 2. Because it's easier to build responsive sites

Imagine coding a two-column responsive grid whereby:

* each column has `20px` and `50px` padding on small and large screens;
* each column has `2em` and `3em` font-size on small and large screens; and
* the columns stack on small screens. Note that *column* is now a misleading class name.

### Using atomic class names

Taking an atomic approach results in the following HTML:

	<div class="grid clearfix">
	  <div class="col pd20 pd50 fs2 fs3">Column 1</div>
	  <div class="col pd20 pd50 fs2 fs3">Column 2</div>
	</div>

Notes:

- There are 7 classes, some of which override each other.
- To make the columns actually responsive we would need a `fs3large` class etc.
- At certain break points, the classes are misleading and redundant e.g. clearfix.

We've barely evaluated this simple component and yet there is so much pain already. Let's see what a semantic approach looks like.

### Using semantic class names

Taking a semantic approach results in the following HTML:

	<div class="thing">
	  <div class="thing-thingA"></div>
	  <div class="thing-thingB"></div>
	</div>

Notes:

- These classes are encapsulated to the module's design and content.
- Any differences can be handled easily using media queries.
- We can style these elements however we need to.
- These classes are meaningful in small and big screens.
- We can use a media query, to clear elements only when needed.

Semantic class names are meaningful all the time. This is not only powerful, but this is where it makes most sense.

*Also, think about how valuable a responsive grid system is. A visual layout should adapt to the content, not the other way around.*

## 3. Because they are easier to find

Visual classes tend to be used on a multitude of elements. This means a search will yield many results, making it hard to find the element in question.

As semantic class names are unique, a search should yield just one result making it easy to track down the HTML and the styles.

## 4. Because they reduce the risk of regression

Updating a visual class name increases the chance of regression because many elements will use them. It will take a lot of time and effort to check otherwise.

As semantic class names are unique, any changes we make will only apply to the module in question. This is easier.

When we don't feel confident making changes, we either cause problems or we avoid doing the work which creates redundancy.

## 5. Because visual classes aren't worth it

If we're going to do `<div class="red">` we may as well do `<div style="color: red">`. Afterall, it's more explicit.

But this mixes concerns and removes the benefit of being able to cache CSS. Also, isn't `.red` a repeat of the exact same abstraction that CSS gives us for free with `color: red`?

## 6. Because they provide hooks for automated tests too

Automated functional tests work by searching for and interacting with elements. This may include:

1. clicking a link;
2. finding a text box;
3. typing in text;
4. submitting a form; and then
5. verifying some criteria.

Visual class names don't allow us to target specific elements because they apply to many. Adding hooks just for tests is foolhardy.

## 7. Because they provide hooks for Javascript

Semantic class names are useful for Javascript too. We can't use visual class names as a reliable way to retrieve elements.

## 8. Because they don't need maintaining

If we name something based on what it is, we won't have to update the HTML again. A heading is always a heading, no matter what it *looks* like.

The styling might change but this only requires a CSS update. This is known as *loose coupling* which improves maintainability.

## 9. Because they are easier to debug

When inspecting an element, there will be several applicable CSS selectors. We'll have to look through these. With a semantic class name there is just one which is easier to work with.

## 10. Because the standards recommend it

On using the class attribute, HTML5 specs say in 3.2.5.7:

> "[...] authors are encouraged to use values that describe the nature of the content, rather than values that describe the desired presentation of the content."

## 11. Because styling state is easier

Consider the following HTML:

	<a class="padding-left-20 red" href="#"></a>

Changing the padding and colour on hover is a difficult task. It's better to avoid having to fix self-induced problems like this.

## 12. Because they encourage lean HTML

As we've seen above, atomic classes bloat the HTML. Semantic classes result in smaller HTML. And whilst the CSS may increase in size, it's cacheable.

## Final thought

Semantic class names are a corner stone of *MaintainableCSS*. Without them, everything else makes little sense. So name something based on what it is and everything else falls into place.

<!--## Because visual class names might declare the same property!

It's likely that several different utility classes could refer to the same property meaning order matters and performance degrades.

Think of an example of this.
-->

