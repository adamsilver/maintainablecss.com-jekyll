---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how to organise your CSS files.
---

*Discoverability* is an important part of writing maintainable stylesheets and this becomes more important as a project grows in size over time. There are two approaches to consider. Let's discuss each in turn.

## 1. CSS in a single folder

This approach places all CSS inside a single folder within your project:

	/path/to/css
	    /vendor
            someLib.css
            someOther3rdParty.css
	    /yourApp
	        resetPerhaps.css
	        global.css
	        basket.css

Third-party CSS files live under `/vendor` while the CSS you write should live under `yourApp` where you change the name of this to match the name of your project.

This approach normally simplifies the deployment process because typically, the act of bundling, compressing and other such tasks, are applied to a single target directory.

This is the approach I have used most often, but that does not mean it's necessarily the best approach.

## 2. CSS in separate module folders

This approach places module-specific CSS within module folder encapsulating all the related functionality under one roof:

	/basket
      /controllers
        ...
      /templates
        basket.html
        emptyBasket.html
      /partials
        basketHeader.html
        basketSummary.html
      /js
        ...
      /css
        basket.css
	/header
	  ...

If you, like me have used the first approach for a long time, this way of doing things can seem strange at first, but it's really nice to work with.

### But what about global CSS?

You'll need a folder for global CSS or global stuff in general:

	/global
	  /css
        resetPerhaps.css
        global.css
        etc.css
	/basket
	  ...as above...
	/header
       ...

## The 31 CSS file limit problem

Whatever approach you decide, make sure you're aware of the 31 CSS file limit problem.

Some browsers, such as IE9, will ignore styles that are included in the 32nd file (or above). For production this is fine, because you should be bundling your CSS to reduce the amount HTTP requests, but for local development you normally want to work on the source files for easy debugging.

If you **have a compilation step** for local development&mdash;as would be the case if you're using a CSS preprocessor&mdash;you don't need to worry, because your files will be bundled up into one during development.

If you **don't have a compilation** step for local development&mdash;because debugging source files is easier this way&mdash;then you may have to address this. Your options are as follows:

The *first* option would be to introduce a compilation step i.e. mimick what you're doing for production, so you can&mdash;where necessary&mdash;debug in offending browsers.

The *second* option would be to make sure you don't go over 31 files. Choosing this option probably means you can't take the second, modular approach (described above) because most websites will require more than 31 modules.

If you decide to limit the amount of CSS files you will need to work out how best to group modules into a single CSS folder. As an example, I recently grouped `.deliveryAddress`, `.paymentDetails` and `.orderConfirmation` modules within a `checkout.css` file.