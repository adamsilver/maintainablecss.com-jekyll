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

Important notes:

- Component and state are both delimitted by a dash;
- Names are written with lowerCamelCase; and
- Selectors are prefixed with the module name.