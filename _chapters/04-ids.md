---
layout: chapter
title: IDs
section: Background
permalink: /chapters/ids/
description: Learn why using IDs as hooks for styling are problematic and what you should do instead.
---

Summary: Don't use IDs as hooks for styling.

## Why shouldn't we use IDs for CSS?

[IDs overpower class names](http://www.w3.org/TR/css3-selectors/#specificity) by orders of magnitude. For this reason classes can't override IDs easily.

This is a problem when you need a way to provide additional meaning to the HTML, such as state, something I discuss in a chapter of its own.

	#someModule {
	  color: red;
	}

	.someModule-override {
	  color: blue;
	}

With the example above, the colour will always be red which is not our intention. But if we avoid classes the colour will be blue as follows:

	.someModule {
	  color: red;
	}

	.someModule-override {
	  color: blue;
	}

## But sometimes we need to use IDs?

Sometimes we must use an ID. For example:

- A form control is linked to a label using the ID; and
- Internal anchors are often bound using IDs.

Both of which improve the experience. So in short use IDs, but not as hooks for styling.