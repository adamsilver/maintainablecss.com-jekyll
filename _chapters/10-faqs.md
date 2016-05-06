---
layout: chapter
title: FAQs
section: Extras
permalink: /chapters/faqs/
description: Your questions about MaintainableCSS are answered here.
---

Can't find your answer here? Raise an issue on [Github](https://github.com/adamsilver/maintainablecss.com/issues/new) and I will get back to you as soon as I can. Thanks!

## When should I use this?

MaintainableCSS is an approach that works well when building long-lived, bespokely designed responsive websites.

## What if I don't want to use it?

If you don't like it, feel free not to use it, or take the bits and pieces that you do like&mdash;please tell me though what didn't work and why, as i'd love to know more so that we can learn together.

## Isn't this the same as [insert methodology here]?

MaintainableCSS has evolved over many years, and has been influenced by different people. I have been meaning to document these ideas for public consumption for a few years now and that's what I have done.

With that said, I have noticed similarities with BEM and ECSS and no doubt there are others too. If you're happy using something else stick with it&mdash;MaintainableCSS will be right here as and when you need it :)

## Why must I prefix components with the module name?

Good question. I actually used to do write components without the prefix too but ran into problems...

The HTML I used to write looked something like this:

	<div class="basket">
	    <div class="heading">

And the CSS looked something like this:

	.basket {}
	.basket .heading {}

The first and most important problem is that the `.basket .heading` *component* will incorrectly inherit the styles from the `.heading` *module* which is something we don't want, we want our styles encapsulated and bound to the module.

The second problem is that when inspecting the HTML, you can't differentiate between a module and a component, which makes maintainence a harder.

The third problem is that you have to nest selectors which isn't as performant.

The fourth problem is that it's not as portable. For example, let's say you move a component into a different position in the Document Tree, you will then have to update your selectors in the CSS.

<!--## What about common styles that you use across different modules e.g. buttons?

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

There is nothing wrong with having a module within a module. You just have to be careful with the latter approach, because once you edit a style it propagates everywhere, and this can be problematic due to unexpected regression.-->