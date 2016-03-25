---
layout: chapter
title: 6. State
id: chapter5
chapterNumber: 5
permalink: /chapters/6/
previousPage:
  href: /chapters/5/
nextPage:
  href: /chapters/7/
---

**What do I mean by state?** Is the module *showing* or *hiding*. Is it *active* or *inactive*, is it in a *loading* state or not? Each of these potentially mean that the UI *looks* different.

We want to communicate this via a css class.

So let's say our module is called *header*.

	.m-header {}

If we need this to have a disabled state we need to do add this

	.m-header-disabled {
		/* something that makes it look disabled */
	}

And the HTML needs to have *both* classes

	<div class="m-header m-header-disabled"></div>
