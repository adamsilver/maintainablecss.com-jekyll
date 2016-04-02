---
layout: chapter
title: Conventions
section: Core
---

Whether you choose to utilise lower (or upper) camel case or use (double) dashes or underscores to delimit your CSS it really doesn't matter.

What matters is *consistency*.

*MaintainableCSS* has the following conventions:

	.<moduleName>[-<componentName>][-<state>] {}

Some examples:

	/* module container/root */
	.searchResults {}

	/* components of a module */
	.searchResults-heading {}

	.searchResults-item {}

	/* state */
	.searchResults-isLoading {}

I will go into lot's more detail in later chapters.