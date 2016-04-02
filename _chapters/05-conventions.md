---
layout: chapter
title: Conventions
section: Core
---

Whether you choose to utilise lower (or upper) camel case or use (double) dashes or underscores to delimit your CSS it really doesn't matter.

What matters is *consistency*.

*MaintainableCSS* has the following conventions:

	.<moduleName>[-<componentName>][-<state>] {}

If we take a module called searchResults, that is made up of other elements and might also have a loading state (think AJAX), then we might end up with the following semantic class names:

	/* module container */
	.searchResults {}

	/* components of a module */
	.searchResults-heading {}

	.searchResults-item {}

	/* state */
	.searchResults-isLoading {}

More information can be found in upcoming chapters about *modules* and *state*.