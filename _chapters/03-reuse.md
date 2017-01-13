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

Don't take this the wrong way. We'll discuss strategies for reuse later on. It's just that we try so hard to reuse the rules inbetween the curly braces across selectors. And this is problematic for many reasons:

## 1. Because styles change in response to screen size

Imagine coding a two-column responsive grid whereby:

* Each column has `20px` and `50px` padding on "small" and "large" screens respectively.
* Each column has `2em` and `3em` font-size on "small" and "large" screens respectively.
* On "small" screens, the columns stack. Note that *column* is now a misleading class name.

Using atomic class names such as: `.grid`, `.col`, `.pd50`, `.pd20`, `.fs2` and `.fs3` makes this hard.

	<div class="grid">
	  <div class="col pd20 pd50 fs2 fs3">Column 1</div>
	  <div class="col pd20 pd50 fs2 fs3">Column 2</div>
	</div>

The latter class names override the former. To make the columns responsive we would need another class such as `.fs3large`. We start to see how painful this could get.

Alternatively, take the following *semantic* mark-up:

	<div class="someModule">
	  <div class="someModule-someComponent"></div>
	  <div class="someModule-someOtherComponent"></div>
	</div>

These classes are isolated to the module. They enable us to style these components how ever we need to, and using media queries where necessary.

*Think about how valuable a responsive grid system is. A visual layout should adapt to the content, not the other way around.*

## 2. Because styles change due to state

Consider the following HTML:

	<a class="padding-left-20 red" href="#"></a>

Changing the padding and colour on hover is a difficult task. Better to avoid having to fix self-induced problems like this.

## 3. Because debugging is harder

When inspecting an element, there will be several applicable CSS selectors. We'll have to look through these. With a semantic class name there is just one.

## 4. Because granular styles aren't worth it

If we're going to do `<div class="red">` we may as well do `<div style="color: red">`. It's more explicit.

But this isn't advisable because it mixes concerns and removes the benefit of being able to cache CSS.

## 5. Because visual class names are ambiguous

For example, `.red` could mean red text, background or perhaps a reddish gradient. We can't be sure.

## 6. Because updating a utility class applies to all instances

This sounds good but it isn't. We'll end up applying changes to elements we didn't even know existed. Or we'll be afraid to update the class altogether. Instead we'll create a `.red2` resulting in redundant code. Either way, this is not maintainable.

## 7. Because non-semantic class names are hard to find

If an element has classes based on how it looks such as `.red` or `.col-lg-4`, then these classes will be scattered all over the codebase.

In which case, searching for *red* will yield many results across the HTML templates, making it hard to find the element in question.

If we use semantic class names, a search should yield just one result. And if it yields more than one result, then this indicates a problem that requires our attention.

## 8. Because reusing CSS causes HTML bloat

If we attempt to reuse *rules* we'll end up with classes such as: `red`, `clearfix` and `pull-left` which leads to HTML like this:

	<div class="clearfix pull-left red etc">

Bloat makes it harder to maintain and degrades performance (albeit in a minor way).

## What if we really want to reuse a style?

On occasion it can make sense to reuse a style. In this case we should use comma-delimitted selectors residing in a well named file.

For example, let's say we wanted a bunch of different elements to have red text we might do this:

	/* colours.css */

	/* red text */
	.someSelector,
	.someOtherSelector {
	  color: red;
	}

If an abstraction has more than one rule, if one selector needs something different, that selector should be removed from the list. Otherwise we'll end experience override hell down the line.

We should use this technique for convenience, not for performance.

## What about mixins?

If we're using a CSS preprocessor, we can use mixins. They are helpful because they provide the best of both worlds. But, we should use them with caution.

Just like utility classes, updating a mixin propagates to all instances. Instead of updating a mixin, we could create a new, slightly different mixin. But, this causes redundancy.

Also, mixins can end up containing multiple parameters, conditionality and lots of rules. This is complicated. Complicated is hard to maintain.

To mitigate this complexity, we can create granular mixins For example, a "red text" mixin. This is better. However, the declaration of that mixin is basically the same as a declaring `color: red`. We may as well declare that instead.

If we need to update the rule in multiple places, a search and replace might be all that's necessary. Even if we did use a mixin, if *red* changes to *orange*, for example, the mixin's name will need updating.

Sometimes mixins are useful in some cases. For example, we might want to apply *clearfix* rules across different elements and breakpoints.

So it's not that mixins are *bad*, it's just we probably shouldn't be so quick to use them.

## What about performance?

We developers are prone to overcomplicating matters when it comes to performance. We get obsessed with the smallest of details.

Even if the CSS totals more than 100kb, in the grand schemes of things, there's probably very little gain from mindlessly striving for DRYness.

Compressing just one image will give us a better return on our investment. And as we've already discussed, there are other forms of CSS redundancy. If we resolve that we improve maintainability *and* performance.

## Is this violating DRY principles?

Attempting to reuse, for example `float: left`, is akin to trying to reuse variable names in different Javascript objects. It's simply not in violation of DRY.

## Final thoughts on reuse

Reuse and DRY are important principles in software engineering. But, striving to reuse CSS too much ironically makes maintenance *harder*.
