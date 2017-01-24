---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/versioning/
description: Learn how MaintainableCSS makes it really easy to upgrade and AB test modules for rapidly evolving websites.
---

We may, for example, want to A/B test two different versions of a module to see which works best. To do this, we need to duplicate the module and give it a unique name. For example, if we want to test two different baskets, the CSS might be as follows:

	/* existing module (variant A) */
	.basket {}

	.basket-title {}

	/* new version (variant B) */
	.basket2 {}

	.basket2-title {}

This way we can maintain two versions during testing until we settle on the best one. And, once we do, it's easy to discard the redundant module as they are not intertwined. Good code is easy to delete.