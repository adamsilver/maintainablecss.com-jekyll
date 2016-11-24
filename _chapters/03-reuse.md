---
layout: chapter
title: Reuse
section: Background
permalink: /chapters/reuse/
description: Learn why avoding reuse and embracing repetition makes CSS maintenance easier.
---

**Summary:** Don't try and reuse styles. Adopt a duplication-first approach.

> &ldquo;DRY is often misinterpreted as the necessity to never repeat the exact same thing twice [...]. This is impractical and usually counterproductive, and can lead to forced abstractions, over-thought and [over]-engineered code.&ldquo;
<br>&mdash; <cite>Harry Roberts, CSS Wizardy</cite>

Don't take this advice the wrong way. MaintainableCSS has various strategies for reuse which I will talk about later. The problem is that trying to reuse the bits *in-between* the curly braces is problematic. Here's why:

## 1. Because styles change based on breakpoints

Responsive Design  means styling elements differently based on viewport size. Imagine coding a two-column grid to the following spec:

1. Each column has 20px and 50px padding on "small" and "large" screens respectively.
2. Each column has 2em and 3em font-size on "small" and "large" screens respectively.
3. On small screens, the columns are stacked. Note: "column" is now a misleading class name.

Using atomic class names such as: `.grid`, `.col`, `.pd50`, `.pd20`, `.fs2` and `fs3` makes this difficult at best.

	<div class="grid">
	  <div class="col pd20 pd50 fs2 fs3">Column 1</div>
	  <div class="col pd20 pd50 fs2 fs3">Column 2</div>
	</div>

The latter class names override the former. There is no responsive behaviour here. To achieve this you need a crazy class name such as `.fs3large`.

This is merely scratching the surface of the problems you will face with this approach to CSS development.

Alternatively, take the following semantic mark-up:

	<div class="someModule">
	  <div class="someModule-someComponent"></div>
	  <div class="someModule-someOtherComponent"></div>
	</div>

The styles are isolated to the module. And you can apply the rules flexibly within CSS. Just 6 CSS declarations are needed with 3 of those inside Media Queries.

As an aside, consider how valuable a responsive grid system is. A visual layout should adapt to the *content*, not the other way around. The content should not adapt to a predefined responsive grid. That's poor design.

## 2. Because styles change based on states

Consider the following HTML:

	<a class="padding-left-20 red" href="#"></a>

Giving the element different styles on hover (e.g. padding or colour) becomes painful at best. It's better to avoid having to fix self-induced problems.

## 3. Because reuse makes debugging more difficult

When inspecting an element, there are several applicable CSS selectors. You will have to look through these. With a semantic class name there is just one.

## 4. Because granular styles aren't worth bothering with

If you're going to do `<div class="red">` you may as well do `<div style="color: red">`. The latter is more explicit anyway. But this isn't advisable because it mixes concerns and removes the benefit of being able to cache CSS.

## 5. Because visual class names don't hold much meaning

Take `.red` for example. This could mean a red background, text or a reddish gradient. Who knows.

## 6. Because updating a "utility" class applies to all instances

This sounds good but it isn't. You end up applying changes where you didn't mean to. Think regression. Alternatively, you end up scared to touch this utility class so you end up with `.red2`. Then you end up with redundant code. Obviously this is not fun to maintain.

## 7. Because non-semantic class names are hard to find

If an element has classes based on how it looks such as `.red`, `.col-lg-4` and `.large`, then these classes will be scattered all over the codebase so searching for "red" will yield many results across the HTML templates, making it hard to find the element in question.

If you use semantic class names, a search should yield just one result. And if it yields more than one result, then this should indicate a problem that needs dealing with.

Note: if you have a repeated *component* within a module, then searching might yield several results within 1 file. That is, a module would typically live in a single template.

## 8. Because reuse causes bloat

If you attempt to reuse every single *rule* you'll end up with classes such as: `red`, `clearfix`, `pull-left`, `grid` which leads to HTML bloat:

	<div class="clearfix pull-left red etc">

Bloat makes it harder to maintain and degrades performance (albeit in a minor way).

## 9. Because reuse breaks semantics

If you strive to reuse the bits inbetween the curly braces to create "atomic" class names, then you encounter all the problems stated in the chapter about [Semantics](/chapters/semantics/). Read that chapter now, if you haven't already.

## 10. What if I really want to reuse a style?

It is extremely rare, but there are times when it really does make sense to reuse a style. In this case use the comma in your selectors and place it in a well named file.

For example let's say you wanted a bunch of different modules or components to have red text you might do this:

	/* colours.css */

	/* red text */
	.someSelector,
	.someOtherSelector {
		color: red;
	}

Remember though that if any selector deviates, even a little bit, then remove it from the common list and duplicate. You must be very careful with something like this. Do it for convenience, not for performance. Your mileage may vary.

## What about mixins?

CSS preprocessors allow you to create mixins which can be really helpful because they provide the best of both worlds but they should be designed with caution.

You have to be very careful to update a mixin because it propagates in all instances just like utility classes. It can be problematic to edit and instead you create new mixins that are slightly different causing redundancy and maintenance problems.

Also, mixins can become very complicated with lots of params, conditionality and large declarations of styles. All of this makes it complicated and complicated is hard to maintain.

To mitigate, you can make mixins really granular. For example you could have a "red text" mixin which is certainly better. But then again, the declaration of that mixin is basically the same as a declaration of red text&mdash;might as well just declare that instead.

If you need to update it in multiple places, then a search and replace might just do it, depending on your context. And even if you did use a mixin, when red changes to orange, you will have to do a search and replace anyway, because the mixin name will otherwise be misleading.

This does not mean mixins are "bad"&mdash;in fact they can be very helpful. For example, being able to apply *clearfix* rules across different elements at different breakpoints is probably a very helpful thing to do for maintainability. Just make sure to use them with care.

## What about performance?

I don't have stats to hand, but I can very confidently say that it's not wise to practice premature optimisation. Let's say you have a very large CSS codebase (100KB or more).

Firstly, I *guess* you *might* save yourself a few KB. Secondly, there are alternative paths to improving performance and thirdly, you probably have redundant code due to a lack of maintainability.

Also consider that one or two images are likely to be far larger than the entire CSS so exerting energy here is probably of little value.

## Is this violating DRY principles?

Attempting to reuse `float: left` as an example, is akin to trying to reuse variable names in different Javascript objects. It's simply not in violation of DRY.

## Final thoughts on reuse

Reuse and DRY are such important principles in software engineering but when it comes to CSS, striving to reuse too much ironically makes maintenance *harder*. However, there are times when reuse and abstraction makes sense which is discussed in later chapters.
