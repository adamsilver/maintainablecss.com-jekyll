---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Learn the simple conventions that MaintainableCSS employs to write modules, components and state.
---

Conventions can be a bone of contention amongst engineers, but what matters most is readability and consistency. With that said, *MaintainableCSS* has the following convention:

	/* Square brackets denote optional parts */
	.<moduleName>[-<componentName>][-<state>] {}

Here are some real examples pertaining to a "search results" module:

	/* module container/root */
	.searchResults {}

	/* components of a module */
	.searchResults-heading {}

	.searchResults-item {}

	/* state: such as AJAX loading */
	.searchResults-isLoading {}

Each of these class names are semantic. Module, component and state are all delimitted by dashes. Each bit is written in lowerCamelCase.

We will see this convention used in all upcoming chapters.