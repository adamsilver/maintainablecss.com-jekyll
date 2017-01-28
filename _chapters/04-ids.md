---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

When I first wrote CSS, I used IDs because semantically speaking, we should use an ID when there is one of something, and a class when there are several. For example, a footer would use an ID; a list of products would use a class.

The problem occurs when we need to override styles that are applied with an ID. This is because [IDs overpower class names](http://www.w3.org/TR/css3-selectors/#specificity) by orders of magnitude. To demonstrate the problem, we're going to override the colour of an element from *red* to *blue* using an ID.

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

However, it's not that we shouldn't use IDs. In fact IDs enable specific browser features such as:

- Labels are linked to form fields by ID
- Internal anchors are bound by ID
- Various ARIA attributes are connected by ID

So it's not that we shouldn't use them at all, it's just that we shouldn't use them as hooks for *styling*.