---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

Summary: Don't use IDs as hooks for styling.

IDs enable specific browser features. For example:

- Labels are linked to form fields by ID
- Internal anchors are bound by ID
- Various ARIA attributes are connected by ID

All of these features improve the user experience. We don't have to use IDs for styling. If we did, we would run into [specificity problems](http://www.w3.org/TR/css3-selectors/#specificity). To demonstrate the problem, we're going to override the colour of an element from *red* to *blue* using an ID.

Here's the HTML:

	<div id="module" class="module-override">

And the CSS:

	#module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}

The element will be red even though the override class declares blue. This is because IDs overpower classes. Let's swap the ID for a class:

	<div class="module module-override">

And the CSS:

	.module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}

Now, the element is blue&mdash;problem solved.

## Final thought

Don't be afraid to use IDs to enable browser features, but avoid them for styling purposes.