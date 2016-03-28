---
layout: chapter
title: Semantics
permalink: /chapters/2/
---

Naming stuff is both important and difficult. It is not a coincidence that the topic of semantics is discussed this early in the *Maintainable CSS* guidelines.

> &ldquo;There are only two hard things in Computer Science: cache invalidation and naming things.&rdquo;
<br>&mdash; <cite>Phil Karlton</cite>

It's imperative that this chapter is understood and followed because if it isn't, CSS (and Javascript) become far more painful to write.

HTML and CSS are tied together so if you make your HTML meaningful then CSS becomes equally meaningful in the process.

## It's not *just* about the right element

Whilst it's important that you use the right element for the job, it's obvious that you should use a `<table>` for tabular data, `<a>` for a link and a `<p>` for a paragraph, so Maintainable CSS doesn't concern itself with this.

## It's about the *additional* hooks

What *Maintainable CSS* *does* care about is the additional class names (and IDs) we place on in our HTML in order to provide additional meaning. Ultimately these are hooks for CSS and Javascript to enhance as appropriate.

## The one rule you must not break

When it comes to naming, **an element must be named based on with it *is*&mdash;not what it *looks* like or how it *behaves*.**

Basically, just ask yourself *what am I looking at?*.

## Non semantic HTML

Let's take a look at a few non semantic HTML modules.

	<div class="red pull-left"></div>
	<div class="grid row"></div>
	<div class="col-xs-4"></div>

The clue above is that firstly, all the class names describe the *look* of the content, not what the content *is*. Secondly, because there are many aspects to *look* there are many class names per element.

## Semantic HTML

Let's take a look at a few semantic HTML modules.

	<div class="header"></div>
	<div class="basket"></div>
	<div class="product"></div>
	<div class="searchResults"></div>

The clue is that each of these class names describe what each module *is*. I don't have a clue what it looks like or how it behaves. Nor should I &mdash; that's the job of CSS and Javascript. Also, notice how there is just one class name per module, there is no need for two.

## Why shouldn't you name something based on what it looks like?

There are many reasons why. If you change the CSS so that it looks different, then you need to change the class name in CSS and HTML.

If you name something based on what it is, then it will never have to change.

For example a shopping basket is always a shopping basket. Styles might change, behaviour might change, but it will always be the shopping basket.

**Why else?**

Okay say you have a class name that means the element floats left with a particular width in a system. That class name is only likely to be meaningful at a particular breakpoint.

	.column1 {
		float: left;
	}

	@media(whatever) {
		.column1 {
			float: none;
		}
	}

Suddenly, column1 is named based on how it looks, but it now doesn't look like that at certain breakpoints. It's now misleading. However, the shopping basket is still a shopping basket when it's big and when it's small, it just looks (and perhaps behaves differently).

For further information you can read [Why Semantic HTML Is So Important](http://adamsilver.io/articles/why-semantic-html-is-so-important/).
