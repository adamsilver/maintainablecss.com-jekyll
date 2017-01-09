---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Learn the simple conventions that MaintainableCSS employs to write modules, components and state.
---

Conventions can cause dispute amongst engineers. But, if you agree with the rationale up to now then the convention itself doesn't matter too much. You can always tweak it to your liking if you don't find this one readable.

What's most important is consistency. And with that in-mind *MaintainableCSS* has the following convention:

	/* Square brackets denote optional parts */
	.<moduleName>[-<componentName>][-<state>] {}

Here are some examples of a *search results* module:

	/* module container */
	.searchResults {}

	/* components of a module */
	.searchResults-heading {}

	.searchResults-item {}

	/* state: such as AJAX loading */
	.searchResults-isLoading {}

Each of these class names are semantic. Components and state are delimitted by dashes with each word written in lowerCamelCase. We'll use this convention going forwards.