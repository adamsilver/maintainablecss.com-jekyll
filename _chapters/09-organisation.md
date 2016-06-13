---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how MaintainableCSS suggests to organise your CSS files within your codebase.
---

*Discoverability* is an important part of writing maintainable CSS. And, the ease of tracking down CSS, becomes more and more important as a project grows in size.

There are generally two approaches to consider. Let's discuss each in turn.

## 1. CSS in one folder

This approach places all CSS inside a single folder within your project. Something like this:

	/path/to/css
	  /vendor
      someLib.css
      someOther3rdParty.css
	  /yourApp
	    resetPerhaps.css
	    global.css
	    basket.css

If you're using any third party CSS files, they should live in `/vendor`. Everything else should live in `/yourApp` (change the name to match your project). All CSS lives under this one folder whether it's a global style applied to the `body`, or if it's a module style applied to `.basket`.

This is useful for deployment purposes such as combining, minifying, compressing and revving because having all CSS in one place simplifies this task.

This is the approach I have used the most, but it's not necessarily the best.

## 2. CSS in separate folders

This approach places CSS within the module it pertains to:

	/basket
      /controllers
        ...
      /templates
        basket.html
        emptyBasket.html
      /partials
        basketHeader.html
        basketSummary.html
      /whatever
        ...
      /css
        basket.css
	/header
	  ...

All related functionality lives under a single folder relating to the module. Lovely!

**But what about global CSS?** You'll need a folder for global CSS (or perhaps global stuff in general). Something like:

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

Whatever approach you decide to take you may need to be aware of the 31 CSS file limit problem.

In short, some browsers (such as IE9) will ignore styles that are included in the 32nd file or above. For production this is fine, because you should be bundling and compressing your CSS for performance etc.

If you **have a compilation step** for local development&mdash;as would be the case if you're using a CSS preprocessor&mdash;you don't need to worry about this problem, because all your files will be bundled up into one during development.

If you **don't have a compilation** step for local development&mdash;because debugging source files is easier this way&mdash;then you may have to solve this problem. Your options are as follows:

The *first* option would be to introduce a compilation step i.e. mimick what you're doing for production, so you can&mdash;where necessary&mdash;debug in offending browsers such as IE9.

The *second* option would be to make sure you don't go over 31 files. Choosing this option will likely mean you can't go down the modular route, as you're now limited to no more than 31 modules in an entire website.

When I have taken the second option, I have grouped modules by the pages or sections of a site that they relate to. For example, in a recent project I have had *checkoutHeader*, *deliveryAddress*, *paymentDetails* and *orderConfirmation* modules within a `checkout.css` file.