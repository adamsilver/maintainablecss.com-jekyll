---
layout: chapter
title: Reuse
section: Background
permalink: /chapters/reuse/
description: Learn why avoding reuse and embracing repetition makes CSS maintenance easier.
---

Summary: Don't try too hard to reuse style rules across selectors. Adopt a duplication-first approach.

> &ldquo;DRY is often misinterpreted as the necessity to never repeat the exact same thing twice [...]. This is impractical and usually counterproductive, and can lead to forced abstractions, over-thought and [over]-engineered code.&ldquo;
<br>&mdash; <cite>Harry Roberts, CSS Wizardy</cite>

Don't take this the wrong way as I'll discuss ways to reuse CSS shortly. The problem is that we try too hard to reuse the rules inbetween the curly braces across selectors. This is problematic for many reasons:

## 1. Because styles change based on breakpoints

If you're building a responsive website, element styles will change based on screen size. Imagine coding a two-column grid to the following spec:

1. Each column has 20px and 50px padding on "small" and "large" screens respectively.
2. Each column has 2em and 3em font-size on "small" and "large" screens respectively.
3. On small screens, the columns are stacked. Note that "column" is now a misleading class name.

Using atomic class names such as: `.grid`, `.col`, `.pd50`, `.pd20`, `.fs2` and `.fs3` makes this hard.

	<div class="grid">
	  <div class="col pd20 pd50 fs2 fs3">Column 1</div>
	  <div class="col pd20 pd50 fs2 fs3">Column 2</div>
	</div>

The latter class names override the former. To make the coloumns responsive you would need another class such as `.fs3large`. You can start to get a feel for how difficult this is.

Alternatively, take the following *semantic* mark-up:

	<div class="someModule">
	  <div class="someModule-someComponent"></div>
	  <div class="someModule-someOtherComponent"></div>
	</div>

These classes are isolated to the module. They enable you to style these components with how ever many media queries you need.

Note: think about how valuable a responsive grid system is. A visual layout should adapt to the *content*, not the other way around. The content should not adapt to a predefined responsive grid. That's poor design.

## 2. Because styles change based on states

Consider the following HTML:

	<a class="padding-left-20 red" href="#"></a>

Changing the padding and colour on hover is a difficult task. It's better to avoid having to fix self-induced problems like this.

## 3. Because reuse makes debugging more difficult

When inspecting an element, there will be several applicable CSS selectors. You will have to look through these. With a semantic class name there is just one.

## 4. Because granular styles aren't worth bothering with

If you're going to do `<div class="red">` you may as well do `<div style="color: red">`. It's more explicit. But this isn't advisable because it mixes concerns and removes the benefit of being able to cache CSS.

## 5. Because visual class names are ambiguous

For example, `.red` could mean a red background, text or perhaps a reddish gradient. I don't know.

## 6. Because updating a utility class applies to all instances

This sounds good but it isn't. You'll end up applying changes to elements in the site you didn't even know existed. Or you'll be too scared to update the utility class. Instead you'll create a `.red2` resulting in redundant code. Either way, this is not maintainable.

## 7. Because non-semantic class names are hard to find

If an element has classes based on how it looks such as `.red`, `.col-lg-4` and `.large`, then these classes will be scattered all over the codebase so searching for "red" will yield many results across the HTML templates, making it hard to find the element in question.

If you use semantic class names, a search should yield just one result. And if it yields more than one result, then this indicates a problem that requires your attention.

Note: if you have a repeated *component* within a module, then searching will yield several results within 1 file. That's to be expected.

## 8. Because reusing CSS causes HTML bloat

If you attempt to reuse *rules* you'll end up with classes such as: `red`, `clearfix` and `pull-left` which leads to HTML like this:

	<div class="clearfix pull-left red etc">

Bloat makes it harder to maintain and degrades performance (albeit in a minor way).

## 9. Because reuse breaks semantics

If you strive to reuse the bits inbetween the curly braces to create atomic class names, you'll encounter all the problems stated in the chapter about [Semantics](/chapters/semantics/). Read that chapter now, if you haven't already.

## 10. What if I really want to reuse a style?

It is rare, but there are times when it does make sense to reuse a style. In this case use the comma in your selectors and place it in a well named file.

For example let's say you wanted a bunch of different modules or components to have red text you might do this:

	/* colours.css */

	/* red text */
	.someSelector,
	.someOtherSelector {
		color: red;
	}

If you have an abstraction that deals with more than one rule, when one selector deviates from the rule, you'll need to remove it from the list and duplicate. Otherwise you'll get into override hell.

Take this comma-delimitted approach for convenience, not performance.

## What about mixins?

If you're using a CSS preprocessor, you can use mixins. They are helpful because they can provide the best of both worlds.

But, you should use them with caution. Just like utility classes, updating a mixin propagates to all instances.

Instead of updating a mixin, a developer could create a new, slightly different mixin. This causes redundancy.

Moreover, mixins can end up containing multiple parameters, conditionality and lots of rules. This makes CSS more complicated. Complicated is hard to maintain.

To mitigate, you can create granular mixins. For example, you could have a "red text" mixin. This is better. However, the declaration of that mixin is basically the same as a declaring `color: red`. You may as well declare that instead.

If you need to update the rule in multiple places, a search and replace might be all you need. Even if you did use a mixin, if *red* changes to *orange*, for example, the name of the mixin will need to be changed anyway.

I am not saying Mixins are bad. They can be helpful in some cases. For example, you might want to apply *clearfix* rules across different breakpoints. Use them with care.

## What about performance?

I don't have stats to hand, but I know it's not wise to practice premature optimisation.

Even if you have a CSS codebase of 100kb or more, I doubt you can save that much anyway. Compressing just one image will probably be more valuable than shaving CSS.

Moreover, there are other ways to improve performance. And lastly, you probably have some redundancy in your CSS because of the problems discussed in this guide.

## Is this violating DRY principles?

Attempting to reuse, for example `float: left`, is akin to trying to reuse variable names in different Javascript objects. It's simply not in violation of DRY.

## Final thoughts on reuse

Reuse and DRY are important principles in software engineering. But, striving to reuse CSS too much ironically makes maintenance *harder*. Lastly, there are times when reuse through abstraction makes sense which I discuss in later chapters.
