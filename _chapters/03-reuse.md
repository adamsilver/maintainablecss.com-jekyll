---
layout: chapter
title: Reuse
section: Background
permalink: /chapters/reuse/
description: Learn why avoding reuse and embracing repetition makes CSS maintenance easier.
---

**Summary:** Embrace repetition. Don't try and reuse styles.

## Why? Because reuse breaks semantics.

If you don't repeat yourself, then you break semantics. Go read that chapter.

## Why? Because reuse causes bloat.

If you attempt to reuse every single *rule* you'll end up with classes such as: `red`, `clearfix`, `pull-left`, `grid` which leads to HTML bloat:

	<div class="clearfix pull-left red etc"></div>

Bloat makes it harder to maintain and degrades performance.

## Why? Because reuse makes debugging more difficult.

When debugging an element, there will be several applicable CSS selectors playing a part making it noisey.

## Why? Because granular styles aren't worth bothering with.

If you're going to do `<div class="red">` you may as will do `<div style="color: red"` which is more explicit anyway. But we don't want to do this because we don't want to mix concerns!

## Why? Because styles change based on breakpoints.

Building responsive sites mean that we style elements differently based on viewport size. Imagine trying to build a 2 column grid that:

- has 50px and 20px padding on large and small screens respectively.
- has 3em and 2em font-size on large and small screens respectively.
- on small screens each column is stacked below each other. Note: "column" is now misleading.

With this in mind how can you utilise these atomic class names: `.grid`, `.col`, `.pd50`, `.pd20`, `.fs2` and `fs3` and achieve these specs?

	<div class="grid">
	  <div class="col pd50 pd20 fs3 fs2">Column 1</div>
	  <div class="col pd50 pd20 fs3 fs2">Column 2</div>
	</div>

You can see this just isn't going to work. You now need some crazy class names such as `fs3large`. This is just the tip of iceberg when it comes to maintainance issues.

Alternative take the following semantic mark-up that doesn't attempt to reuse styles:

	<div class="someModule">
	  <div class="someModule-someComponent"></div>
	  <div class="someModule-someOtherComponent"></div>
	</div>

Ensuring this is styled as above is now a simple task with 6 CSS declarations needed in total, 3 of which reside within media queries.

## Why? Because visual class names don't hold enough meaning.

Take `red`. Does this mean a red background? Does this mean red text? Does this mean a red gradient? What tint of red does this mean?

## Why? Because updating a "utility" class applies to all instances.

This sounds good but it isn't. You end up applying changes where you didn't mean to. Think regression. Alternatively, you end up scared to touch this utility class so you end up with `.red2`. Then you end up with redundant code. Obviously this is not fun to maintain.

## Why? Because non-semantic class names are hard to find.

If an element has classes based on how it looks such as `.red`, `.col-lg-4` and `.large`, then these classes will be scattered all over the codebase so searching for "red" will yield many results across the HTML templates.

If you use semantic class names, a search should yield just one result. And if it yields more than one result, then this should indicate a problem that needs dealing with.

## What if I really want to reuse a style?

It is extremely rare, but there are times when it really does make sense to reuse a style. In this case use the comma in your selectors and place it in a well named file.

For example let's say you wanted a bunch of different modules or components to have red text you might do this:

	/* colours.css */

	/* red text */
	.someSelector,
	.someOtherSelector {
		colour: red;
	}

Remember though that if any selector deviates, even a little bit, then remove it from the common list and duplicate. You must be very careful with something like this. Do it for convenience, not for performance. Your mileage may vary.

## What about mixins?

CSS preprocessors allow you to create mixins which sound great and seemingly appear to give you the best of both worlds.

However, you have to be very careful to update a mixin because it propagates in all instances just like utility classes. You become scared to touch and then you create new mixins that are slightly different causing redundancy and maintainance problems.

Also, mixins can become very complicated with lots of params, conditionality and large declarations of styles. All of this makes it complicated and complicated is hard to maintain.

To mitigate, you can make mixins really granular. For example you could have a "red text" mixin which is certainly better. But then again, the declaration of that mixin is basically the same as a declaration of red text. Might as well just declare that instead.

If you need to update it in multiple places, then a search and replace will do it. And even if you did use a mixin, when red changes to orange, you will have to do a search and replace anyway.

## What about performance?

I don't have stats to hand, but I can very confidently say that it's not wise to practice premature optimisation. Let's say you have a very large CSS codebase (100kb).

Firstly, I *guess* you *might* save yourself a few KB. Secondly, there are alternative paths to improving performance and thirdly, you probably have redundant code due to a lack of maintainability.

Also consider that one or two images are likely to be far larger than the entire CSS so exerting energy here is probably of little value.

## Final thoughts on reuse

Reuse and DRY are such important principles in software engineering but when it comes to CSS, it ironically makes maintainance harder. Avoid trying to reuse style rules and gain the benefits of easy to maintain CSS.