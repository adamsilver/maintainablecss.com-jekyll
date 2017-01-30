---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

Semantically speaking, we should use an ID when there is only one instance of a thing. And we should use a class when there are several. [IDs overpower class names](http://www.w3.org/TR/css3-selectors/#specificity) by orders of magnitude, which is problem when we want to override a style.


To demonstrate the problem, let's override the colour of an element from *red* to *blue* using an ID.

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

Sometimes we need to use IDs to enable certain behaviours. For example:

- Labels are linked to form fields by ID;
- Internal anchors are bound by ID; and
- Various ARIA attributes are connected by ID.

All of which improve the experience for users. So it's not that we shouldn't use IDs, it's just that we shouldn't use them for *styling*.