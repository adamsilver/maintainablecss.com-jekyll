---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/versioning/
description: Learn how MaintainableCSS makes it really easy to upgrade and AB test modules for rapidly evolving websites.
---

We may need to have multiple versions of the same module in the codebase at the same time. For example we may want to AB test two different versions of a Basket to see which converts better.

This is easy. Just duplicate the module and give each a unique name:

	/* existing module (variant A) */
	.basket {}

	/* new version (variant B) */
	.basketVariant2 {}

This way we can maintain two versions during testing until we settle on the best one.