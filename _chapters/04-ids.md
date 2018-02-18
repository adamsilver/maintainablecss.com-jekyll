---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

Semantically speaking, we should use an ID when there's only one instance of a thing. And we should use a class when there are several.

However, [IDs overpower class names](http://www.w3.org/TR/css3-selectors/#specificity) by orders of magnitude, which is a problem when we want to override a style.


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

The element will be red even though the override class declares blue. Let's fix this by swapping the ID for a class:

	<div class="module module-override">

And the CSS:

	.module {
	  color: red;
	}

	.module-override {
	  color: blue;
	}

Now, the element is blue&mdash;problem solved.

Whilst using IDs for styling is problematic, we can still use them for other things. For example, we'll most certainly need to use them to connect:

- labels to form fields
- in-page anchors to a hash fragment in the URL
- ARIA attributes to help screen reader users

## Final thought

Use IDs whenever you need to enable particular behaviours for browsers and assistive technology. But avoid using them as hooks for styles.
