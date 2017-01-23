---
layout: chapter
title: Reuse
section: Background
permalink: /chapters/reuse/
description: Learn why avoding reuse and embracing repetition makes CSS maintenance easier.
---

Summary: Don't try too hard to reuse style rules across selectors. Adopt a duplication-first approach.

As Harry Roberts says, *DRY is often misinterpreted as the necessity to never repeat the exact same thing twice. This is impractical and usually counterproductive, and can lead to forced abstractions, over-thought and over-engineered code.*

This forced abstraction, over-thought and over-engineered code manifests itself in visual and atomic classes. We know how painful they can be because we discussed them thoroughly in the previous chapter about [semantics](/chapters/semantics/). But let's talk more about reuse.

## But what if we did want to reuse a style?

If we do want to reuse a style we can use comma-delimitted selectors inside a well-named file. For example, if  multiple elements need red text, we could do this:

	/* colours.css */

	/* red text */
	.someSelector,
	.someOtherSelector {
	  color: red;
	}

If one module deviates from the styles in the abstraction, it should be removed. Otherwise we'll experience override hell later on. Use this technique for convenience, not for performance.

There are times when overrides makes sense, which we'll discuss in [State](/chapters/state/) and [Modifiers](/chapters/modifiers/).

## What about mixins?

Mixins provide the best of both worlds. At least in theory.

Like utility classes, updating a mixin propagates to all instances. If we don't have a handle of what's using the mixin, we increase the risk of regression. Instead of updating a mixin, we can create another, but this causes redundancy.

Also, mixins can easily end up with many rules, multiple parameters, and conditionality. This is complicated. Complicated is hard to maintain.

To mitigate this complexity, we can create granular mixins, such as one for red text. At first this seems better. But, declaring the red mixin is the same as declaring `color: red`. We may as well declare that instead.

If we need to update the rule in multiple places, a search and replace might be all that's necessary. Also, when the red *mixin* changes to *orange*, its name will need updating anyway.

With all that said, mixins are useful in some cases. We might, for example, want to apply a *clearfix* across different elements and only within certain breakpoints. This well understood *group* of rules, can be used many times over.

So it's not that mixins are *bad*, it's just we probably shouldn't be so quick to use them.

## What about performance?

We developers are prone to overcomplicating matters when it comes to performance. We get obsessed with the smallest details.

Even if CSS totals more than 100kb, in the grand schemes of things, there's probably very little gain from mindlessly striving for DRYness. And as we've discussed making CSS small makes HTML big.

Compressing just one image will give us a better return on our investment. And as we've discussed, resolving other forms of redundancy improves maintainability *and* performance.

## Is this violating DRY principles?

Attempting to reuse, for example `float: left`, is akin to trying to reuse variable names in different Javascript objects. It's simply not in violation of DRY.

## Final thought

Reuse and DRY are important principles in software engineering. But, striving to reuse CSS too much ironically makes maintenance *harder*.
