---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

**Summary:** *Don't* use IDs as hooks for styling.

**Why** shouldn't we use IDs for CSS?

## Because of specificity issues.

[IDs overpower class names](http://www.w3.org/TR/css3-selectors/#specificity) by orders of magnitude. For this reason you can't override an ID selector's style with a class name selector easily.

This becomes a problem when you need a way to provide additional meaning to the HTML, such as state, something we discuss in a chapter of its own.

	#someModule {
	    color: red;
	}

	.someModule-override {
	    color: blue;
	}

If you apply the ID and the class name to the element, the colour will always be red.

	.someModule {
	    color: red;
	}

	.someModule-override {
	    color: blue;
	}

Now the colour will be blue as intended.

## But, sometimes an ID is required?

Sometimes using IDs is necessary. For example a form control is linked to a label by ID. And internal anchors are often bound using IDs too. Both of these improve the User Experience. Use as appropriate for additional behaviour, not for styling.

## Final thoughts on IDs

Avoid IDs as hooks for styling but if you need them for other things use them. As and when you do use IDs, stick to the naming conventions you would use for classes as explained in other chapters.