---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how MaintainableCSS suggests to organise your CSS files within your codebase.
---

Organising your CSS files is important. When you organise your CSS well, it makes finding CSS and adding new CSS much easier, improving general maintainability.

There are generally two options when it comes to file organisation:

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

If you're not using a preprocessor, then you will likely need to think about what deserves it's own file and what needs to be grouped and how those things are grouped.

For example, recently on a shop the following was used to organise:

	base.css
	basket.css
	brand.css
	buttons.css
	category.css
	checkout.css
	dashboard.css
	department.css
	editorial.css
	forms.css
	globalModules.css
	header.css
	homepage.css
	productDetails.css
	roadtTest.css
	security.css
	simpleBrand.css
	staticPages.css
	subCategory.css

It's interesting because I don't think this is perfect or great but it's okay considering we decided not to use a preprocessor to make debugging and developing easier in some respects.

But the thing is, buttons.css could have been shoved in global. Same goes for forms.css.

Then you have header.css which is a global module but got so big that it warranted a file of it's own.

And actually these are organised more by page, than module, because those modules are often only surfaced on a single page.

All food for thought for deciding how to organise stuff.

Also, bundling everything v.s. separate bundles per section or page.

Could do account.css and shop.css etc. It's not perfect, but prefer easy debuggin and a pretty easy to navigate file system.

Failing that, it's easy to search for a module in question as per the guidelines because the css will only reside in one place. So search to the rescue on that one.

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
