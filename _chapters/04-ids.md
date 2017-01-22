---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

Summary: Don't use IDs as hooks for styling.

Sometimes we have to use IDs. For example, labels are linked to form fields via ID; and internal anchors are bound by ID, both of which improve the user experience. But they have no bearing on *style*.

If we were to use IDs as hooks for style, we would run into [specificity problems](http://www.w3.org/TR/css3-selectors/#specificity). To demonstrate, imagine we want to override the colour of an element from *red* to *blue*.

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

Now, the element is blue. Problem solved.

## Final thought

Use IDs to enable browser functionality. But never use them as hooks for styling.