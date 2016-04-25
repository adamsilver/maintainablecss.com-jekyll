---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how MaintainableCSS suggests to organise your CSS files within your codebase.
---

## Strategy 1

	/basket
		/templates
		/whatever
		/css
			basket.css

## Strategy 2

	/path
		/to
			/css
				/vendor
				/yourApp
					basket.css

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

## 32 file limit

Test IE9