---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how to organise your CSS files.
---

Discoverability is an important part of writing maintainable stylesheets. Discovery becomes harder as the project grows over time. There are two approaches you can take.

## 1. CSS in a single folder

This approach places all CSS inside a single folder within your project:

	/path/to/css
	  /vendor
        some3rdParty.css
        someOther3rdParty.css
	  /yourApp
	    some.css
	    global.css
	    basket.css

Third-party CSS files live under `/vendor` while the CSS you write should live under `/yourApp` where *yourApp* is the name of your project.

This approach can simplify deployment because bundling and compressing can be targetted via single directory.

This is the approach I have used most, but that doesn't mean it's the best.

## 2. CSS in separate module folders

This approach puts module-specific CSS within a module folder. It's good because it encapsulates all related code under one roof, so to speak.

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

### What about global CSS?

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

Whatever approach you take, bere aware of the 31 CSS file limit.

IE9 for example, will ignore styles that are included in the 32nd (or 33rd etc) file. For production this is fine, because you're probably bundling your CSS to reduce HTTP requests. But for local development you probably want to work with source files to make debugging easier.

If you have a compilation step for local development&mdash;as would be the case if you're using a CSS preprocessor&mdash;you don't need to worry. Your files will be bundled during development.

If you don't have a compilation step for local development&mdash;because debugging source files is easier this way&mdash;then you may have to address this. Your options are as follows:

1. You can introduce a compilation step. Basically, you need to mimick what you're doing for production, so you can&mdash;where necessary&mdash;debug in offending browsers; or

2. Make sure you don't use more than 31 files. Choosing this option probably means you can't use the modular approach (as described above) because most websites contain more than 31 modules.

If you do take this approach, you'll need to work out how best to group modules into files. For example, I recently folded delivery address, payment details and order confirmation modules into `checkout.css`.