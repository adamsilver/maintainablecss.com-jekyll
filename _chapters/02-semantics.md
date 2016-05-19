---
layout: chapter
title: Semantics
section: Background
permalink: /chapters/semantics/
description: Why naming something based on what it is, instead of how it looks or behaves is a cornerstone of writing well architected and maintainable CSS code.
---

**Summary:** Name something based on what it *is*, not how it *looks* or *behaves*.

## The longer explanation

Semantic HTML isn't just about the elements we use&mdash;it's pretty obvious that you should use a `<a>` for a link, a `<table>` for tabular data and a `<p>` for a paragraph etc.

More importantly, it's about the class names (and IDs) we add, that provide *additional* hooks for CSS (and Javascript) to enhance as appropriate.

It's easy to add class names without thought as to their naming but naming is very important.

> &ldquo;There are only two hard things in Computer Science: cache invalidation and naming things.&rdquo;
<br>&mdash; <cite>Phil Karlton</cite>

This is because humans are good at understanding human communication and bad at understanding abbreviated, non-semantic abstractions.

## Good and bad examples of class names

Try and spot the difference between non-semantic and semantic class names...

	<!-- bad -->
	<div class="red pull-left">
	<div class="grid row">
	<div class="col-xs-4">

It's not clear at all *what* this HTML represents. You *might* have an *idea* of what these things *look like* (on small or large screens) but that is all.

	<!-- good -->
	<div class="header">
	<div class="basket">
	<div class="product">
	<div class="searchResults">

Here I know exactly what I am looking at. I know the intention of what this HTML represents. And I have no idea how it looks&mdash;that's what CSS is responsible for. Semantic class names mean something to both HTML *and* CSS (and JS).

So **why** else should we use semantic class names?

## Because it's easier to understand.

Whether you're looking at the HTML or the CSS, you know what you're affecting. With visual class names you end up having to sprinkle several class names on to each element, ending up with a vague understanding of the intention of these visual class names. This is hard to maintain.

## Because we are building responsive websites.

Styles often need changing based on viewport size. For example, you might float elements on big screens and not on small screens. So if you have a class called `clearfix` but you don't clear on small screens, then you now have misleading code.

If you use semantic class names, then you can style them differently based on media queries making it easier to maintain.

## Because semantic class names are easier to find.

If an element has classes based on how it looks such as `.red`, `clearfix` and `.pull-left`, then these classes will be scattered all over the codebase&mdash;so if you’re trying to hunt for a particular piece of HTML, the class name is not going to help you.

On the other hand, if your class names are semantic, a search will find the HTML in question. Or more typically, if you're beginning your search via the HTML (think: inspecting an element) then finding unique CSS selectors based on the class name will be far easier.

## Because you don't want unexpected regression.

If you have utility non-semantic classes that describe the look then when you edit one of these classes, they will propagate to every single element with that class. Knowing CSS as you do, do you feel comfortable that the propagation didn't cause unexpected problems elsewhere?

Semantic class names are unique, so when editing one, you *can* feel comfortable that your change only applies to the module in question as you intended, making maintainance easier.

## Because you don't want to be afraid to update code.

Directly linked with the previous point about regression, when you don't feel comfortable touching code, you end up causing problems or being afraid to touch it at all. Therefore you end up with redundant code, increasing maintainance issues.

## Because it helps automated functional testing.

Automated functional tests work by searching for particular elements, interacting with them (typing in text, clicking buttons and links etc) and verifying based on that.

If you have visual class names all over the HTML, then there is no reliable way to target particular elements and act upon them.

## Because it provides meaningful hooks for Javascript to enhance.

Just like these hooks help automated testing, they are also useful to enhance behaviour with Javascript. Visual class names can't be used as a reliable way to target modules or components.

## Because of general maintainance concerns.

If you name something based on what it is, you won't have to touch the HTML again i.e. a heading is always a heading, no matter what it *looks* like.

The styling might change but you only have to update the CSS. This is otherwise known as Loose Coupling and this improves maintainability.

## Because utility classes increase noise when debugging.

When debugging an element, there will be several applicable CSS selectors making it noisey to debug.

## Because the standards recommend it.

On using the class attribute, HTML5 specs say in 3.2.5.7:

> "[...] authors are encouraged to use values that describe the nature of the content, rather than values that describe the desired presentation of the content."

## Because you get a performance bump.

This is a *very* small benefit but when you have one class name per element, you end up with smaller HTML. With visual classes you end up with multiple class names per element and that can add up.

## Because it adheres to the reuse rule.

If you don't use semantic class names, then you will likely be breaking the rules of reuse. Read the next chapter to find out more.

<!--## Why? Because visual class names might declare the same property!

It's likely that several different utility classes could refer to the same property meaning order matters and performance degrades.

Think of an example of this.
-->

## Final thoughts about semantics

Semantic class names are a corner stone of *MaintainableCSS*. Without this, everything else makes little sense. So name something based on what it is and everything else follows.
