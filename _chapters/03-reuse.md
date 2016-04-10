---
layout: chapter
title: Reuse
section: Background
permalink: /chapters/reuse/
---

**Summary:** *Don't* try and reuse CSS rules. Take a duplicate-first approach instead.

## Why? Because reuse breaks semantics!

If you don't repeat yourself, then you break semantics. Go read that chapter.

## Why? Because reuse causes bloat!

If you don't repeat yourself you'll end up with classes such as: red, clearfix, pull-left, grid which leads to HTML bloat:

	<div class="clearfix pull-left red etc"></div>

Bloat makes it harder to maintain, and degrades performance.

## Why? Because reuse makes debugging more difficult

When debugging an element, there will be several applicable CSS selectors playing a part making it noisey.

## Why? Because granular styles aren't worth bothering with!

If you're going to do `<div class="red">` you may as will do `<div style="color: red"` which is more explicit anyway. But we don't want to do this because we don't want to mix concerns!

## Why? Because styles change based on breakpoints.

We build responsive sites. This means sometimes styles change based on viewport size. Sometimes something floats on big screens and not on small screens. So if you have a class called `clearfix` but you don't clear on small screens, then we now have misleading code.

## Why? Because visual class names don't hold enough meaning.

Take `red`. Does this mean a red background? Does this mean red text? Does this mean a red gradient? What tint of red does this mean?

## Why? Because updating a "utility" class applies to all instances.

This sounds good but it isn't. You end up applying changes where you didn't mean to. Think regression. Alternatively, you end up scared to touch this utility class so you end up with `.red2`. Then you end up with redundant code. Obviously this is not fun to maintain.

## What if really want to reuse a style?

It is extremely rare, but there are times when it really does make sense to reuse a style. In this case use the comma in your selectors:

	.someModule,
	.anotherModule {
		/*common styles*/
	}

And put it in a relevant file, colours.css, fonts.css etc, with a relevant comment. But if one module deviates even a little bit, then take it out of the comma list and duplicate. You have to be very careful with this.

## What about mixins?

CSS preprocessors allow you to create mixins which sound great and seemingly appear to give you the best of both worlds.

However, you have to be very careful to update a mixin because it propagates in all instances just like utility classes. You become scared to touch and then you create new mixins that are slightly different causing redundancy and maintainance problems.

Also, mixins can become very complicated with lots of params, conditionality and large declarations of styles. All of this makes it complicated and complicated is hard to maintain.

To mitigate, you can make mixins really granular. For example you could have a "red text" mixin which is certainly better. But then again, the declaration of that mixin is basically the same as a declaration of red text. Might as well just declare that instead.

If you need to update it in multiple places, then a search and replace will do it. And even if you did use a mixin, when red changes to orange, you will have to do a search and replace anyway.

## Final thoughts on reuse

Reuse and DRY are such important principles in software engineering but when it comes to CSS, it ironically makes maintainance harder. Avoid the reuse, enjoy the maintainability. Go for a duplication-first approach instead.