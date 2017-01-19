---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how to organise your CSS files.
---

Good code is easy to find. Easy to find code is well organised. We want our CSS to be well organised. There are two approaches we can take:

1. **Organise by type**. All CSS under a single folder; or
2. **Organise by module**. The CSS lives in module-specific folder.

## 1. CSS in a single folder

This approach puts all CSS inside a single folder within the project:

	/path/to/css
	  /vendor
        some3rdParty.css
        someOther3rdParty.css
	  /yourApp
	    some.css
	    global.css
	    basket.css

### Notes

* Third-party CSS files live under `/vendor`.
* The application's CSS lives under `/yourApp` where *yourApp* is the name of your project.
* This approach simplifies deployment because a build script can easily target a single directory in order to bundle and compress etc.
* This is the most common approach I've seen but that doesn't mean it's the best.

## 2. CSS in a module folder

This approach puts module-specific CSS within a folder of its own:

	/global
	  /css
	    resetPerhaps.css
	    global.css
        etc.css
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

### Notes

* We normally orientate ourselves by feature, not by technology when tackling a piece of work. This makes this approach a compelling one.
* Global CSS needs a folder of its own because global styles by their very nature don't belong to a module.
* This approach is more likely to suffer from the *31 CSS file limit problem*, which is explained next.

## The 31 CSS file limit problem

Whichever approach you take, be aware of the 31 CSS file limit found in versions of Internet Explorer. Internet Explorer 9, for example, ignores styles stored in the 32nd (or 33rd etc) file.

For production this is fine, because we should bundle our CSS to reduce HTTP requests. But for local development it's better to work with source files to make debugging easier. And it's in legacy browsers where bugs normally arise.

**If you have a compilation step** for local development&mdash;as would be the case when using a CSS preprocessor&mdash;you don't need to worry. The preprocessor will bundle the files.

**If you don't have a compilation step** for local development&mdash;because debugging source files is easier this way&mdash;then you may want to remedy this with one of two approaches:

### 1. Add an option to concatenate CSS locally

By doing this you'll be able to mimick production and debug CSS in offending legacy browsers.

### 2. Use less than 32 CSS files

As you'll probably have more than 31 modules, you can't organise your CSS by module. Instead you'll have to put several modules within the same CSS file.