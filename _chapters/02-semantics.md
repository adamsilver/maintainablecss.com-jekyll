---
layout: chapter
title: Semantics
section: Background
permalink: /chapters/semantics/
---

In short: Name something based on what it is, not how it *looks* or *behaves*.

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

## Also

Naming is both important and difficult. It is not a coincidence that the topic of semantics is discussed so early on, in the *MaintainableCSS* guidelines.

> &ldquo;There are only two hard things in Computer Science: cache invalidation and naming things.&rdquo;
<br>&mdash; <cite>Phil Karlton</cite>

It's imperative that this chapter is understood and followed because if it isn't, CSS (and Javascript) become far more painful to write.

## It's about the classes

Yes, it's important that you use the right element for the job! It goes without saying that you should use a `<table>` for tabular data, an `<a>` for a link and a `<p>` for a paragraph&mdash;however *MaintainableCSS* doesn't concern itself with this particular aspect of semantics.

What *MaintainableCSS* *does* care about is the class names (and IDs) we place in our HTML, in order to provide *additional* meaning. Ultimately these are hooks for CSS (and Javascript) to enhance as appropriate.

## How I used to write HTML

I have pretty much always written semantic HTML but I haven't always followed the *MaintainableCSS* guidelines, and therefore have encountered some of the problems it solves.

This is how I used to write a module &mdash; here is a basket module:

	<div class="basket">
		<div class="heading">
			<h1>Your basket</h1>
		</div>
		<div class="whatever"></div>
	</div>

It's modularised based on the module container. And the CSS for this might look like this

	.basket {}

	.basket .heading {}

	.basket .whatever {}

As you can see each selector begins with the container class name. This is how it is modular. There are 2 problems with this 1 minor and 1 is a major problem. Both of which are solved by *MaintainableCSS*.

The first, is that these selectors are nested which aren't as performant as they might be. Not that I am a fan of premature optimisation, and have rarely encountered CSS performance problems. Regardless, flat selectors are the most performant.

The second, is that due to the cascade, the heading *component* inside the basket *module* could easily receive styles pertaining to a pre-existing heading *module* like so:

	/* heading module
	.heading { ... }

This is obviously not what we want. We want them to be styled completely differently and for each section not to affect each other as per the goals of *MaintainableCSS*.

## Non semantic HTML examples

Let's take a look at a few non semantic HTML modules.

	<div class="red pull-left"></div>
	<div class="grid row"></div>
	<div class="col-xs-4"></div>

The clue above is that firstly, all the class names describe the *look* of the content, not what the content *is*. Secondly, because of the choice to architect code like this, there are no many class names per element, causing HTML bloat.

If you're going to write non semantic HTML like this, you may as well use the style attribute instead:

	<div style="color: red; float: left; width: 25%;"></div>

## Semantic HTML examples

Let's take a look at a few semantic HTML modules.

	<div class="header"></div>
	<div class="basket"></div>
	<div class="product"></div>
	<div class="searchResults"></div>

The clue is that each of these class names describe what each module *is*. I don't have a clue what it looks like or how it behaves. Nor should I &mdash; that's the job of CSS and Javascript. Also, notice how there is just one class name per module&mdash;we don't need anymore.

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
