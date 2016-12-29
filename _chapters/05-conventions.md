---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Learn the simple conventions that MaintainableCSS employs to write modules, components and state.
---

Conventions often cause dispute amongst engineers. If you agree with the rationale behind this approach, then tweaking the convention is hardly a big deal. What's most important is readability and consistency.

With that said, *MaintainableCSS* has the following convention:

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

Each of these class names are semantic. Module, component and state are all delimited by dashes. Each bit is written in lowerCamelCase.

You will see this convention in upcoming chapters.