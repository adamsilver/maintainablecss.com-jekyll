---
layout: chapter
title: Conventions
section: Core
permalink: /chapters/conventions/
description: Learn the simple conventions that MaintainableCSS employs to write modules, components and state.
---

*MaintainableCSS* has the following convention:

	.<module>[-<component>][-<state>] {}

Square brackets are optional depending on the module in question. Here are some examples:

	/* Module container */
	.searchResults {}

	/* Component */
	.searchResults-heading {}

	/* State */
	.searchResults-isLoading {}

Notes:

- component and state are both delimited by a dash
- names are written with lowerCamelCase
- selectors are prefixed with the module name
