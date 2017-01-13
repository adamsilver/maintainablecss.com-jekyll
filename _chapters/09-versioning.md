---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/versioning/
description: Learn how MaintainableCSS makes it really easy to upgrade and AB test modules for rapidly evolving websites.
---

We may need multiple versions of the same module at any given time. For example, we may want to AB test two different versions of a basket to see which converts better.

To do this, we just need to duplicate the module and give it a unique name as follows:

	/* existing module (variant A) */
	.basket {}

	.basket-componentEtc {}

	/* new version (variant B) */
	.basketVariant2 {}

	.basketVariant2-componentEtc {}

This way we can maintain two versions during testing until we settle on the best one.