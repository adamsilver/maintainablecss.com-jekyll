---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how MaintainableCSS suggests to organise your CSS files within your codebase.
---

Well-organised CSS files are an important aspect of MaintainableCSS. We want to make our CSS easy to find, update and add to over time as projects evolve and increase in size.

There are generally two approaches when it comes to organising your CSS. Let's discuss each in turn.

## 1. Put CSS in a CSS folder

This approach places all CSS files in to a single folder as follows:

	/path/to/css
		/vendor
		/yourApp
			basket.css

With this method, it's obvious where CSS lives. Often this folder might be copied elsewhere and prep'd for deploying to production. Having it all in one place simplifies this process.

Whilst MaintainableCSS does a great job in making CSS modular, it is likely there will always be rules that are global, so having the easy decision to shove it all in one place leaves little room for error.

This has been the approach that I have taken and been exposed to most often.

## 2. Put CSS in a module folder

This approach means that the CSS folder resides within the module it pertains to as follows:

	/basket
		/controllers
			BasketController.js
		/templates
			Basket.html
		/css
			basket.css
	/header
		...

This approach is great because it groups related functionality under a single module folder. Whether it's CSS, Javascript, HTML, Controllers, Views, Partials or whatever else, having it all grouped in one place improves portability, and often you're working on multiple bits relating to the same feature so this makes sense.

This to me makes more sense than the first approach, and when I have used it, it works well.

As with the first approach, there is always *some* global CSS to write, so this will have to reside somewhere that doesn't have a natural home like modules do. You end up needing a "GlobalStuff" folder anyway.

	/global
		global.css
		etc.css
	/header
		...
	/basket
		...

## The 32 CSS file limit problem

Whatever approach you decide to take you may well need to be aware of the 32 CSS file limit problem.

In short, you can't include more than 31 CSS files in an HTML document in some browsers up to Internet Explorer 9. What happens is any CSS that resides in an additional file will be ignored.

Meaning you can't create more than 31 files unless you jump through certain hoops to avoid this problem. For example, if you don't use a CSS preprocessor, then when you're in debug mode for local development, you're limited.

You could of course bundle these files into one, on save, but this can be problematic for development and debugging.

If you do use a CSS preprocessor, you're likely already doing this and won't experience this problem. If so, move along now.

If you want to debug the original CSS files, then you will have to get creative in using the 31 CSS files to their max.

For example, recently on a shop the following was used to organise:

	base.css
	basket.css
	brand.css
	category.css
	checkout.css
	dashboard.css
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
