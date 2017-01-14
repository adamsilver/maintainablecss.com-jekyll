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

Don't take this the wrong way. We'll discuss strategies for reuse later on. It's just that, too often, we try so hard to reuse rules inbetween the curly braces. And this is problematic for many reasons:

## 1. Because styles change in response to screen size

Imagine coding a two-column responsive grid whereby:

* Each column has `20px` and `50px` padding on "small" and "large" screens respectively.
* Each column has `2em` and `3em` font-size on "small" and "large" screens respectively.
* On "small" screens, the columns stack. Note that *column* is now a misleading class name.

### 1.1 Using atomic class names

Taking an atomic approach results in the following HTML:

	<div class="grid">
	  <div class="col pd20 pd50 fs2 fs3">Column 1</div>
	  <div class="col pd20 pd50 fs2 fs3">Column 2</div>
	</div>

Here are some notes:

- There are 6 classes.
- They override each other.
- They are misleading at certain screen sizes.
- To make the columns actually responsive we would need a `fs3large` class etc.
- This is hard to read.

We've barely evaluated this simple component and yet there is so much pain already. Let's see what a semantic approach would look like.

### 1.2 Using semantic class names

Taking a semantic approach results in the following HTML:

	<div class="thing">
	  <div class="thing-thingA"></div>
	  <div class="thing-thingB"></div>
	</div>

Here are some notes:

- These classes are isolated to the module.
- Any differences can be handled easily using media queries.
- We can style these elements however we need to.
- It's easy to read.

*Also, think about how valuable a responsive grid system is. A visual layout should adapt to the content, not the other way around.*

## 2. Because styles change due to state

Consider the following HTML:

	<a class="padding-left-20 red" href="#"></a>

Changing the padding and colour on hover is a difficult task. It's better to avoid having to fix self-induced problems like this.

## 3. Because debugging is harder

When inspecting an element, there will be several applicable CSS selectors. We'll have to look through these. With a semantic class name there is just one.

## 4. Because granular styles aren't worth it

If we're going to do `<div class="red">` we may as well do `<div style="color: red">`. Afterall, it's more explicit.

But this isn't advisable because it mixes concerns and removes the benefit of being able to cache CSS.

Also, isn't `.red` a repeat of the exact same abstraction that CSS gives us for free with `color: red`?

## 5. Because visual class names are ambiguous

For example, `.red` could mean red text, a red background or perhaps a reddish gradient. It's hard to be sure.

## 6. Because updating a utility class applies to all instances

This sounds good but it isn't. We'll end up applying changes to elements we didn't even know existed. Or we'll be afraid to update the class altogether. Or we'll create `.red2` resulting in redundancy.

## 7. Because non-semantic class names are hard to find

Visual classes tend to be used on a multitude of elements. This means a search will yield many results, making it hard to find the element in question.

As semantic class names are unique, a search should yield just one result making it easy to track down.

## 8. Because reusing CSS causes HTML bloat

Attempting to reuse rules results in bloated HTML like this:

	<div class="clearfix pull-left red etc">

Bloat makes it harder to maintain and degrades performance albeit in a minor way.

## What if we really want to reuse a style?

On occasion it makes sense to reuse a style. In this case we should use comma-delimitted selectors inside a well-named file.

If we wanted multiple elements to have red text, we could do this:

	/* colours.css */

	/* red text */
	.someSelector,
	.someOtherSelector {
	  color: red;
	}

However, if one selector deviates from an abstraction containing many rules, it should be removed from the list. Otherwise we'll end experience override hell down the line.

We should use this technique for convenience, not for performance.

## What about mixins?

Mixins are helpful because they provide the best of both worlds. At least in theory.

Like utility classes, updating a mixin propagates to all instances. Instead of updating a mixin, we could create a new and slightly different one. But, this causes redundancy.

Also, mixins can easily end up with many rules, multiple parameters, and conditionality. This is complicated. Complicated is hard to maintain.

To mitigate this complexity, we can create granular mixins, such as one for red text. This is better. However, declaring the mixin is the same as declaring `color: red`. We may as well declare that instead.

If we need to update the rule in multiple places, a search and replace might be all that's necessary. If we did use a mixin, when *red* changes to *orange*, its name will need updating anyway.

Mixins are useful in some cases. For example, we might want to apply *clearfix* rules across different elements and breakpoints.

So it's not that mixins are *bad*, it's just we probably shouldn't be so quick to use them.

## What about performance?

We developers are prone to overcomplicating matters when it comes to performance. We get obsessed with the smallest details.

Even if CSS totals more than 100kb, in the grand schemes of things, there's probably very little gain from mindlessly striving for DRYness.

Compressing just one image will give us a better return on our investment. And as we've discussed, resolving other forms of redundancy improves maintainability *and* performance.

## Is this violating DRY principles?

Attempting to reuse, for example `float: left`, is akin to trying to reuse variable names in different Javascript objects. It's simply not in violation of DRY.

## Final thought

Reuse and DRY are important principles in software engineering. But, striving to reuse CSS too much ironically makes maintenance *harder*.
