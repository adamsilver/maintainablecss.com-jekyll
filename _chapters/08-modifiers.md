---
layout: chapter
title: Modifiers
section: Core
permalink: /chapters/modifiers/
description: Use modifiers to change appearance based on slight differences.
---

Modifiers are similiar to states. Like states they can override certain rules. This is useful when modules (or components) are almost identical but have slight differences.

In this case, reusing and abstracting common CSS rules is useful for maintainability, which I'll explain with an example.

Recently, I was working on an e-commerce website. Each category had a header at the top with a background image. The background image was unique per category. The difference was just one style rule.

The HTML for Boys was:

	<div class="categoryHeader categoryHeader-boys">

The HTML for Girls was:

	<div class="categoryHeader categoryHeader-girls">

And the CSS was:

	.categoryHeader {
	    padding-top: 50px;
	    padding-bottom: 50px;
	}

	.categoryHeader-boys {
	    background-image: url(/path/to/boys.jpg);
	}

	.categoryHeader-girls {
	    background-image: url(/path/to/girls.jpg);
	}