---
layout: chapter
title: Files
section: Extras
permalink: /chapters/files/
description: What does a maintainable CSS file look like?
---

Writing a maintainable CSS file is easy. There are just a few small things to consider:

## 1. Media Queries

Generally speaking, the screen should adapt to the content, not the other way around. With this in mind it could be that some modules don't require any breakpoints when others require five for example. 

Attempting to crow bar all screens in to say 3 predefined breakpoints is something that is unecessarily constraining to a design, ultimately degrading the User Experience.

In a site I worked on recently, the header had just one breakpoint based on the navigation being able to fit on one line or not. That breakpoint happened to be `500px`. Then below the header, there was a module that had a breakpoint of `650px` which is where the content needed a breakpoint to take into account the extra space available to it.

For these reasons, styles residing in breakpoints should be located in very close proximity to a style not wrapped by a breakpoint. See below for an example:

	.basket {}

	@media(min-width: 500px) {
		.basket {}
	}

	@media(min-width: 1000px) {
		.basket {}
	}

## States and modifiers

Just like media queries they should reside next to the element they affect.

	.whatever {}

	.whatever-isWhatever {}

	/* then the rest */

## Comments

Place a nice obvious comment between major parts of a CSS file. If you're using the first approach to file organisation, you will have multiple modules inside one file. Split them up as follows:
	
	/********************************************
	* Module name
	********************************************/

	.blah {}

	.blah-a {}

	/********************************************
	* Module name
	********************************************/

	etc {}