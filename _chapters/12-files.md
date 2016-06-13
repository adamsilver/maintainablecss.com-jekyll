---
layout: chapter
title: File layout
section: Extras
permalink: /chapters/file-layout/
description: What does a maintainable CSS file look like?
---

There are only a few things to consider in order to write a maintainable CSS file. But first, please note that these guides pertain to CSS, but if you're using a CSS preprocessor, you can still take away the principles from this chapter, and apply them to the syntax of your chosen preprocessor.

## 1. Media Queries

Generally speaking, the screen should adapt to the content, not the other way around. This means that a module's breakpoints are determined by the module itself, and *not* by a predetermined set of break point such as "small", "medium" and "large". Doing it this way would constrain the design and quite possibly degrade the User Experience unnecessarily.

Therefore, all styles&mdash;even those that are wrapped in Media Queries&mdash;should be located next to other styles which apply to elements. See below for an example:

	.basket {}

	@media(min-width: 500px) {
		.basket {}
	}

	@media(min-width: 1000px) {
		.basket {}
	}

	.basket-heading {}

## States and modifiers

Just like media queries, states and modifiers should be located in close proximity to the element they pertain to:

	.basket {}

	.basket-isHidden {}

	.basket-heading {}

	.basket-heading-someModifier {}

## Comments

If you have multiple modules residing in a single file, then it's useful to split up these modules with an obvious well named comment:
	
	/********************************************
	* Basket
	********************************************/

	.basket {}

	.basket-heading {}

	/********************************************
	* Banana
	********************************************/

	.banana {}

	.banana-details {}