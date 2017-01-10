---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Learn the simple conventions that MaintainableCSS employs to write modules, components and state.
---

Sometimes conventions cause dispute. But, if you agree with the rationale up to this point, the convention itself doesn't matter too much. You can always tweak to your liking if necessary.

What's most important is consistency. With that in-mind *MaintainableCSS* has the following convention:

	/* Square brackets are optional */
	.<module>[-<component>][-<state>] {}

Here are some examples of a *search results* module:

	/* module container */
	.searchResults {}

	/* component of a module */
	.searchResults-heading {}

	/* state e.g. AJAX loading */
	.searchResults-isLoading {}

The key points are as follows:

- Component and state are delimitted by a dash
- Each segment is written with lowerCamelCase
- Every class is always prefixed with the module name