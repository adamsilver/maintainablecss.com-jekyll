---
layout: chapter
title: Frequently Asked Questions
section: Extras
permalink: /chapters/faqs/
description: Your questions about MaintainableCSS are answered here.
---

## When should I use this?

When you're working on a long-lived, bespokely designed website MaintainableCSS is probably an essential methodology to follow. But feel free not to use it, or take bits and pieces that you do like from the book.

## What if I don't want to use it?

Then you don't have to. You might find that it's not a good fit for your situation. That's fine :).

## Why must I prefix components with the module name?

Good question. I actually used to do it like this too but ran into problems...

The HTML I used to write

	<div class="basket"> <!-- module -->
		<div class="heading"> <!-- component -->

And CSS like this:

	/* module */
	.basket {}

	/* heading component of basket module */
	.basket .heading {}

The first problem is that within the HTML you can't differentiate between a module and a component which makes maintainence a bit harder.

The second problem is that a `.basket .heading` *component* will incorrectly inherit the styles from the `.heading` *module* which is something we don't want.

The third problem is down to portability.

## What about common styles that you use across different modules e.g. buttons?

In the chapter about [Modules](/chapters/modules/) there is a component defined as `.basket-removeButton` but what if the styling for that is used in many places?

There are two approaches. Firstly, you can create a `buttons.css` file and have the following section:

	/***********************************
	* Button style for primary actions
	***********************************/

	.basket-removeButton,
	.another-loginButton,
	.and-anotherDeleteButton {
		/*common styles*/
	}

Or you can just have a button as a module:

	.primaryButton {
		/* common styles */
	}

There is nothing wrong with having a module within a module. You just have to be careful with the latter approach, because once you edit a style it propagates everywhere, and this can be problematic due to unexpected regression.

## This seems similar to BEM, why use it?

It is similar to BEM. The conventions are a little different, the terminology is a little different and the rationale is different. But all in all, if you're happy with BEM (or any other methodology), stick with it unless it starts to cause you pain.

## Got another question?

Just hit me up on [Github](https://github.com/adamsilver/maintainablecss.com/issues/new) and I will get back to you, or add the answer to the book.