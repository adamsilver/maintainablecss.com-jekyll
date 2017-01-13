---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Learn the simple conventions that MaintainableCSS employs to write modules, components and state.
---

Conventions can be a bone of contention amongst developers. Whilst we may not always agree, it doesn't matter too much. We can always tweak the convention, if necessary.

What's most important is consistency. And, with that in-mind *MaintainableCSS* has the following convention:

	/* Square brackets are optional */
	.<module>[-<component>][-<state>] {}

Here are some examples of a *search results* module:

	/* module container */
	.searchResults {}

	/* component of a module */
	.searchResults-heading {}

	/* state e.g. AJAX loading */
	.searchResults-isLoading {}

Notes:

- Component and state are both delimitted by a dash
- Each segment is written with lowerCamelCase
- Every class is always prefixed with the module name