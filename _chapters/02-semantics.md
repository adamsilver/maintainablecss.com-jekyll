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

Here's the same thing using semantic classes:

	<div class="hero">
	  <h1 class="hero-heading">Heading</h1>
	  <p class="hero-tagline">Tagline</p>
	</div>

This is far cleaner. If we want to understand how this is styled, it's easy to do so using the inspector.

## 2. Because it's easier to build responsive sites

Let's look at a typical responsive module. There are two elements which stack on small screens but sit beside each other when there is enough room.

	<div class="clearfix">
	  <div></div>
      <div></div>
	</div>

When the elements are stacked, `clearfix` is not only redundant but it's misleading.

Semantic class names are meaningful all the time. If we need to clear, then we can apply those styles within a media query inside the CSS. This is not only powerful, but this is where it makes most sense.

## 3. Because they are easier to find

Many elements will use `.red` and `.pull-left` classes. Therefore, a search will yield many results. This makes it hard to track down the HTML in question.

A semantic class, such as `.basket`, should yield one result making it easy to find. And inspecting an element, makes it easy to track down its styles.

## 4. Because they reduce the risk of regression

Updating a visual class name increases the chance of regression because many elements will use them. It will take a lot of time and effort to check otherwise.

As semantic class names are unique, any changes we make will only apply to the module in question. This is much easier.

## 5. Because we want to make changes with confidence

When we don't feel confident making changes, we either cause problems or we  avoid doing the work which creates redundancy.

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

It's harder to inspect an element with a multitude of visual class names. With a semantic class there will be just one.

## 10. Because the standards recommend it

On using the class attribute, HTML5 specs say in 3.2.5.7:

> "[...] authors are encouraged to use values that describe the nature of the content, rather than values that describe the desired presentation of the content."

## 11. Because they encourage lean HTML

The use of semantic classes results in smaller HTML. The CSS may increase in size, but it's cacheable.

<!--## Because visual class names might declare the same property!

It's likely that several different utility classes could refer to the same property meaning order matters and performance degrades.

Think of an example of this.
-->

## Final thought

Semantic class names are a corner stone of *MaintainableCSS*. Without them, everything else makes little sense. So name something based on what it is and everything else falls into place.
