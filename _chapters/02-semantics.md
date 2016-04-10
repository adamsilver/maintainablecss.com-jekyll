---
layout: chapter
title: Semantics
section: Background
permalink: /chapters/semantics/
---

**Summary:** Name something based on what it *is*, not how it *looks* or *behaves*.

## The longer explanation

Semantic HTML isn't just about the elements we use&mdash;it's pretty obvious that you should use a `<a>` for a link, a `<table>` for tabular data and a `<p>` for a pargraph etc.

But, more importantly, it's about the class names (and IDs) we add to the elements that provide *additional* hooks for the CSS (and Javascript) to enhance as appropriate.

It's easy to add class names without thought as to their naming but naming is very important.

> &ldquo;There are only two hard things in Computer Science: cache invalidation and naming things.&rdquo;
<br>&mdash; <cite>Phil Karlton</cite>

This is because humans are good at understanding human communication and bad at understanding the abbreviated non-semantic abstractions.

## Good and bad examples of class names

Try and spot the difference between non-semantic and semantic class names...

	<!-- bad -->
	<div class="red pull-left"></div>
	<div class="grid row"></div>
	<div class="col-xs-4"></div>

It's not clear at all *what* this HTML represents. You *might* have an idea of what these things look *like* but that is all.

	<!-- good -->
	<div class="header"></div>
	<div class="basket"></div>
	<div class="product"></div>
	<div class="searchResults"></div>

Here I know exactly what I am looking at. I know the intention of what this HTML represents. And I have no idea how it looks like. That's what the CSS is for.

So **why** else should we use semantic class names?

## Why? Because it breaks the reuse rule!

If you don't use semantics class names, then you will likely be repeating yourself. Go read that chapter.

## Why? Because it's easier to understand!

Whether you're looking at the HTML or the CSS, you know what you're affecting. With visual class names you end up having to sprinkle several class names on to each element, ending up with a vauge understanding of the intention of these visual class names. This is hard to maintain.

## Why? Because we are building responsive websites!

Styles often need changing based on viewport size. For example, you might float elements on big screens and not on small screens. So if you have a class called `clearfix` but you don't clear on small screens, then you now have misleading code.

If you use semantic class names, then you can style them differently based on media queries making it easier to maintain.

## Why? Because you get a performance improvement!

This is a very small reason but when you have one class name per element, you end up with lighter HTML. With visual classes you end up with multiple class names per element and that can add up.

## Why? Because semantic class names are easier to find!

If an element has classes based on how it looks such as .red or .clearfix or .pull-left etc, then these classes will be all over the codebase. So if you’re trying to hunt for a particular piece of HTML, the class name is not going to help you.

On the other hand, if your class names are semantic, a search is likely going to hunt down the HTML in question. Same goes for the CSS. This makes it easier to maintain.

## Why? Because you don't want unexpected regression!

If you have utility non-semantic classes that describe the look then when you edit one of these classes, they will propogate to every single element with that class. Which normally means a developer, is too scared to touch an existing utility class because it is likely it will cause a regression.

When you use semantic class names, they are unique, so when editing one, it will only apply to the module in question.

## Why? Because you don't want to be afraid to update code!

As with the unexpected regressions above, if you use a bunch of utility class names and they are applied all over a large codebase, it's likely you're scared to touch them or delete them. You will end up with redundant code or a pain for testing.

## Why? Because it helps automated functional testing

Automated functional tests work by searching for particular elements, interacting with them (typing in text, clicking buttons and links) and verifying based on that.

If you have visual class names all over the HTML, then there is no reliable way to target particular elements.

## Why? Because general maintainance

If you name something based on what it is, you won't have to touch the HTML again in a dramatic way. I.e. a heading is always a heading, but the styles and behaviour might change.

## Why? Because reuse makes debugging more difficult

When debugging an element, there will be several applicable CSS selectors playing a part making it noisey.

## Final thoughts about semantics

Semantic class names are a corner stone of the approach that *MaintainableCSS* advocates. Without this, everything else makes little sense so, name something what it is and everything else follows.