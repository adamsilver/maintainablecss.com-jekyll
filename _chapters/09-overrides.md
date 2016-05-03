---
layout: chapter
title: Modifiers
section: Core
permalink: /chapters/modifiers/
description: Use modifiers to change appearance based on slight differences.
---

There are times when reusing the parts between curly braces makes total sense, in particular when a module (or component) is almost identical. This is best explained by example...

## E

One example of this I have experienced recently is on an e-commerce site where each category has a header at the top and the background image changes based on category name as follows:

	<div class="categoryHeader categoryHeader-boys"></div>
	<div class="categoryHeader categoryHeader-girls"></div>

The CSS is identical, except for the `background-image` declaration based on the category.

Another example