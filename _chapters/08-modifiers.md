---
layout: chapter
title: Modifiers
section: Core
permalink: /chapters/modifiers/
description: Use modifiers to change appearance based on slight differences.
---

Like state, a modifier can also override styles. This is useful when modules (or components) are almost identical but have slight differences.

In this case, reusing and abstracting common CSS rules is useful for maintainability, which is best explained with an example.

Imagine an e-commerce site whereby each category has a unique background image in the header.

All headers have the same padding etc. The only difference is the background image. To achieve this we added a unique modifier.

The *boys* category had the following HTML:

	<div class="categoryHeader categoryHeader-boys">

And the *girls* category had the following HTML:

	<div class="categoryHeader categoryHeader-girls">

And the CSS was as follows:

	.categoryHeader {
	  padding-top: 50px;
	  padding-bottom: 50px;
	  /* etc */
	}

	.categoryHeader-boys {
	  background-image: url(/path/to/boys.jpg);
	}

	.categoryHeader-girls {
	  background-image: url(/path/to/girls.jpg);
	}

This is a good example of reuse because the differences are small and they are well understood.