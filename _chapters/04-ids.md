---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

Summary: Don't use IDs as hooks for styling.

Sometimes we *must* use an ID to enable certain behaviour. Two examples of this include the fact that:

1. labels are linked to form fields via ID; and
2. internal anchors are bound by ID;

Both of which improve the user experience.

The *problem* with using IDs for styles is that they [overpower class names](http://www.w3.org/TR/css3-selectors/#specificity) which is a problem when we need to override styles.

To demonstrate the problem, imagine we want to override the colour of an element from *red* to *blue*.

Here's the HTML using an ID:

	<div id="module" class="module-override">

And the CSS:

	#module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}

The element will be red which is not what we wanted. However, exchanging the ID for a class results in the following HTML:

	<div class="module module-override">

And the CSS:

	.module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}

In this case, the element will be blue as we intended. So it's not that we can't use IDs, it's just that we should avoid them as hooks *styling*.