---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/versioning/
description: Learn how MaintainableCSS makes it really easy to upgrade and AB test modules for rapidly evolving websites.
---

We may, for example, want to AB test two different versions of a module to see which works better.

To do this, we just need to duplicate the module and give it a unique name. For example, if we want to test two different baskets, the CSS would be as follows:

	/* existing module (variant A) */
	.basket {}

	.basket-componentEtc {}

	/* new version (variant B) */
	.basketVariant2 {}

	.basketVariant2-componentEtc {}

This way we can maintain two versions during testing until we settle on the best one.

And, once we do, it's easy to discard the redundant module as they are not intertwined. Good code is easy to delete.