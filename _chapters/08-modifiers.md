---
layout: chapter
title: Modifiers
section: Core
permalink: /chapters/modifiers/
description: Use modifiers to change appearance based on slight differences.
---

Like state, a modifier can also override styles. This is useful when modules (or components) have small and well understood differences.

Take an e-commerce site whereby each category has a unique background image in the header.

All headers have the same padding, and margin etc. The only difference is the background image. For example, the *boys* category would have a modifier as follows:

	<div class="categoryHeader categoryHeader-boys">

And similarly, the *girls* category whould have a *girls* modifier:

	<div class="categoryHeader categoryHeader-girls">

The CSS would be:

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

Because the differences are small and well understood, this type of reuse is more maintainable.

We can use the same approach to buttons. Most sites have a primary and secondary button style. If all that changes is one or two styles we can have a modifier for primary and secondary buttons as follows:

	.button {
	  padding: 20px;
	  border-radius: 3px;
	  /* etc */
	}

	.button-primary {
	  background-color: green;
	}

	.button-secondary {
	  background-color: #eee;
	}

Again, this only works because the differences are well contained and well understood.

## Final thought

Modifiers are a good way to reuse styles across a well understood element. But, the modifier itself should be a tweak. If it contains a lot of overrides, then modifiers are probably not the way to go.
