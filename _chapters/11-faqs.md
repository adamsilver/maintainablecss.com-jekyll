---
layout: chapter
title: FAQs
section: Extras
permalink: /chapters/faqs/
description: Your questions about MaintainableCSS are answered here.
---

Can't find your answer here? Raise an issue on [Github](https://github.com/adamsilver/maintainablecss.com/issues/new) and I will get back to you as soon as I can. Thanks!

## When should I use this?

MaintainableCSS is an approach that works well when building long-lived, bespokely designed responsive websites that you want to scale. It's also useful for websites that evolve over time.

## What if I don't want to use it?

If you don't like it, feel free not to use it, or take the bits and pieces that you do like&mdash;please tell me though what didn't work and why, as i'd love to know more so that we can learn together.

## Isn't this the same as [insert methodology here]?

These guides are the result of building many different types of websites and have been influenced by many experiences and the many people I have worked with.

With that said, I think it bares most resemblance to BEM and ECSS, so if you're using those or any other methodology that works for you, stick with it. These guides will be here if and when required.

## Can I translate your book?

It's already been translated to [Japanese](http://coliss.com/articles/build-websites/operation/css/maintainable-css-by-adam.html) and German and Spanish are both on the way. So yes, please get in touch to find out how to do this.

## Why must I prefix components with the module name?

Good question. I actually used to write components without the prefix too but ran into problems...

The HTML I used to write looked something like this:

	<div class="basket">
	    <div class="heading">

And the CSS looked something like this:

	/* module */
	.basket {}

	/* heading component of basket module */
	.basket .heading {}

The first problem is that when viewing the HTML, you can't easily differentiate between a module and a component, which makes maintainence a bit harder.

The second problem is that the `.basket .heading` *component* will incorrectly inherit the styles from the `.heading` *module* which is something we don't want, we want our styles encapsulated and bound to the module.

<!-- perf and portability -->

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
