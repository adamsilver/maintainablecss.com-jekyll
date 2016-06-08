---
layout: chapter
title: Organisation
section: Extras
permalink: /chapters/organisation/
description: Learn how MaintainableCSS suggests to organise your CSS files within your codebase.
---

Well-organised CSS files are an important aspect of MaintainableCSS. Finding CSS and knowing how to add to it, is important at all times, but moreso as a project evolves and gets bigger.

There are generally two approaches to consider. Let's discuss each in turn.

## 1. CSS in one folder

As per the name, all CSS resides in a single folder within your project. Something like this:

	/path/to/css
		/vendor
		/yourApp
			basket.css

If you're using any third party CSS files, they should live in `/vendor`. Everything else should live in `/yourApp` (change the name to match your project).

This is the approach I have taken and been exposed to the most.

It's obvious where CSS lives whether it is a global rule such as `body {}` or if it's a module such as `.basket {}`. Additionally, these assets are often modified for deployment, and having them all in one place simplifies this task.

## 2. CSS in separate folders

This option means that CSS resides within the module it pertains to:

	/basket
		/controllers
			...
		/templates
			...
		/partials
			...
		/whatever
			...
		/css
			basket.css
	/header
		...

The nice thing with this is that all related functionality lives under a single folder relating to the module.

But what about global CSS?

You'll need a folder for global CSS (or global stuff in general) for rules applied globally. Something like:

	/global
		/css
			resetPerhaps.css
			global.css
			etc.css
	/basket
		...as above...
	/header
		...

## The 32 CSS file limit problem

Whatever approach you decide to take you may need to be aware of the 31 CSS file limit.

In short, you can't include more than 31 CSS files in an HTML document in some browsers including Internet Explorer 9. What happens is any CSS that resides in an additional file will be ignored.

If you have a compilation step for local development&mdash;as would be the case if you're using a CSS preprocessor&mdash;you don't need to worry about this problem because all your files will be bundled up into one.

If you don't have a compilation step for local development&mdash;because debugging source files is easier this way&mdash;then like me, you may have to consider this 31 file limit.

Your options:

1. Introduce a compilation step i.e. mimick what you're doing for production so that you can test in offending browsers such as IE9 when necessary.
2. Make sure you don't go over 31 files.

If you choose the latter, then you can't really go down the modular route, as several different modules will need to reside in the same file, depending on the size of your website etc.