---
layout: chapter
title: Versioning
section: Extras
permalink: /chapters/versioning/
description: Learn how MaintainableCSS makes it really easy to upgrade and AB test modules for rapidly evolving websites.
---

Sometimes versioning modules can be helpful when the features of a website evolve over time. For example you may want to A/B test two versions of a module to see what performs better. Or the website might be going through a brand refresh.

When you have multiple versions of a module in your codebase, it can be tempting to again reuse the same HTML and CSS to do this. *MaintainableCSS* again dictates that you duplicate and provide a unique name to aid maintainability.

	/* existing module */
	.someModule {}

	/* new version of module */
	.someModuleVariant2 {}

All you have to do is create two separate modules with a unique module name and you can edit each one independently and in your own time.