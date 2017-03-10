---
layout: chapter
title: FAQs
section: Extras
permalink: /chapters/faqs/
description: Your questions about MaintainableCSS are answered here.
---

If you can't find an answer, please [raise an issue on Github](https://github.com/adamsilver/maintainablecss.com/issues/new). Thanks!

## Can I translate your book?

Yes. To do this:

1. [Fork the repo](https://github.com/adamsilver/maintainablecss.com/).
2. Point your (country code) domain to it.
3. Cite the original and let me know :).

## When should I use this?

If you like to keep things truly simple, use this approach. It works well if you're building long-lived, bespokely designed, responsive sites that scale and evolve over time.

## What if I don't want to use it?

If you don't like it, feel free not to use it. Or use the bits you do like. If something doesn't work well, let me know and we can work out.

## Isn't this the same as [methodology]?

These guides are the result of building many different types of websites. I've been influenced by many different experiences, requirements and people that I've worked with.

No doubt, there is a resemblance to BEM and ECSS. If you're using those happily, stick with them. These guides are here if and when you need them.

## Must I give a class name to every element?

No. You can write `.module p {}` if you want to. And sometimes you may have to, if for example you're using markdown. But beware that if you nest a module which contains a `p` it will inherit the styles and need overriding.

## Why must I prefix the module name?

Good question. Here's the HTML without a prefix:

	<div class="basket">
	  <div class="heading">

And the CSS:

	/* module */
	.basket {}

	/* heading component of basket module */
	.basket .heading {}

There are two problems:

1. when viewing HTML, it's hard to differentiate between a module and a component; and
2. the `.basket .heading` component will inherit styles from the `.heading` module which has unintended side effects.

## Could we chain classes for state?

We could use a chained selector for state e.g. `.module.isDisabled`. The problem is that this approach has less browser support. We should avoid patterns that unnecessarily exclude users, unless there is a compelling reason to do so.

## What about inheritance for headings etc?

Ideally our semantic HTML matches the integrity of the visual design. Meaning that we would hope that `h1`s are identical. In this case we can declare the following CSS:

	h1 {
      /* etc */
	}

However, this is rarely the case, in commercial, large-scale websites. In this case we should encapsulate styles to the module in question:

	.module-heading {
	  font-size: ...;
	  color: ...;
	}

## Where do I put media queries?

The screen should adapt to the content, not the other way around.

This means a module's breakpoints shouldn't be predetermined by *small*, *medium* and *large*. Doing this constrains the design and degrades the user experience.

Therefore, all styles&mdash;even those that are wrapped in media queries&mdash;should be located next to regular styles:

	.basket {}

	@media(min-width: 500px) {
      .basket {}
	}

	@media(min-width: 1000px) {
	  .basket {}
	}

	.basket-heading {}

## Where do I put modifiers and states?

States and modifiers, similarly to media queries, should be located in close proximity to the element they pertain to:

	.basket {}

	.basket-isHidden {}

	.basket-heading {}

	.basket-heading--someModifier {}

## Should I add comments?

If you take an approach whereby multiple modules reside within a single CSS file, it's a good idea to segregate those with a chunky comment:

	/********************************************
	* Basket
	********************************************/

	.basket {}

	.basket-heading {}

	/********************************************
	* Thinger
	********************************************/

	.thinger {}

	.thinger-details {}

## Can't find an answer here?

Raise an issue on [Github](https://github.com/adamsilver/maintainablecss.com/issues/new) and I will get back to you as soon as I can. Thanks!
