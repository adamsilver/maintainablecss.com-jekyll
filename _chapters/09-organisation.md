---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how MaintainableCSS suggests to organise your CSS files within your codebase.
---

*"Where do I find CSS?"* and *"Where do I put CSS?"* are questions we need to be able to answer if we are to write maintainable CSS. Shoving everything into one file isn't fun, but yet we can't just create a separate file per module as will be discussed in a sec.

There are generally two ways in which we can organise these things.

## Method 1: Put CSS in a CSS folder

	/css
		/vendor
		/yourApp
			basket.css

## Method 2: Put CSS within a module folder

	/basket
		/templates
		/whatever
		/css
			basket.css

Global stuff? Where to put global stuff when putting stuff in modules?

	/global
		global.css

	/module1
		module1.css
		module1.html
		etc

## 32 file limit

Both organisation options suffer from the 32 file limit which occurs up until IE9, fixed in IE10. So if you have more than 32 modules which is pretty likely you're in trouble depending on your bundling approach.

If you're using a preprocessor, you're probably fine, but then debugging is harder.

## Splitting out sections with a chunky comment

	/****************************************
	* Basket
	****************************************/

	.basket {
		/* etc */
	}

	.basket-title {
		/* etc */
	}
