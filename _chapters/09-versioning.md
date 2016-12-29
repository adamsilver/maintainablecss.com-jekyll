---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/versioning/
description: Learn how MaintainableCSS makes it really easy to upgrade and AB test modules for rapidly evolving websites.
---

You might want to have multiple versions of a module at the same time. For example you might want to test two different Basket modules to see which performs better in an AB test.

To do this, duplicate the module and give each one a unique name. Our two Basket modules might be named as follows:

	/* existing module (variant A) */
	.basket {}

	/* new version (variant B) */
	.basketVariant2 {}

This way you can easily maintain the two versions during testing until you've settled on one.