---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

Summary: Don't use IDs as hooks for styling.

[IDs overpower class names](http://www.w3.org/TR/css3-selectors/#specificity) by orders of magnitude. This is a problem when we need two hooks on a single element&mdash;something we'll cover in upcoming chapters.

To demonstrate the problem in isolation imagine we want to override the colour of an element from *red* to *blue*.

Here's the HTML using an ID:

	<div id="module" class="module-override">

And the CSS:

	#module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}

The element will be red when we intended for it to be blue. To solve this problem we need to swap the ID for a class:

	<div class="module module-override">

And the CSS:

	.module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}

Here the element will be blue as intended.

## But sometimes we must use IDs?

Sometimes we must use an ID. For example, labels are linked to form controls using the ID. For another, internal anchors are bound by ID. Both examples improve the user experience from a behavioural perspective but they have no bearing on styles.

It's not that we can't use IDs. It's just that we should avoid them as hooks for *styling*.