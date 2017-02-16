---
layout: chapter
title: Reuse
section: Background
permalink: /chapters/reuse/
description: Learn why avoding reuse and embracing repetition makes CSS maintenance easier.
---

As Harry Roberts says, *DRY is often misinterpreted as the necessity to never repeat the exact same thing twice. This is impractical and usually counterproductive, and can lead to forced abstractions, over-thought and over-engineered code.*


This forced abstraction, over-thought and over-engineered code often results in visual and atomic classes. We know how painful they are because we discussed them thoroughly in [semantics](/chapters/semantics/). Mixins may also be a problem as we'll discuss shortly.

Whilst we often try to abstract CSS too much too soon, there are obviously going to be times when reuse makes sense. The question must be answered, *how can we reuse a style?*

## How can we reuse a style?

If we want to reuse a style, one option would be to comma-delimit selectors inside a well-named file. For example, if multiple elements need red text, we could do this:

	.someThing,
	.anotherThing {
	  color: red;
	}

This approach should be used for convenience, not for performance. (If the abstraction only has one rule, we're simply exchanging one line of code for another.)

If a selector deviates from the rules inside the abstraction, it should be removed from the list. Otherwise we could regress the other selectors and potentially experience override issues.

It's important to note that this is one of several techniques at our disposal. When a *thing* is well understood we can make use of other techniques, which we'll discuss in [Modules](/chapters/modules/), [State](/chapters/state/) and [Modifiers](/chapters/modifiers/).

## What about mixins?

Mixins provide the best of both worlds. At least in theory.

Like utility classes, updating a mixin propagates to all instances. If we don't have a handle of what's using the mixin, we increase the risk of regression. Instead of updating a mixin, we can create another, but this causes redundancy.

Also, mixins easily end up with many rules, multiple parameters, and conditionality. This is complicated. Complicated is hard to maintain.

To mitigate this complexity, we can create granular mixins, such as one for red text. At first this seems better. But isn't the declaration of a red mixin, the same as the rule itself i.e. `color: red`?

If we need to update the rule in multiple places, a search and replace might be all that's necessary. Also, when the red *mixin* changes to *orange*, its name will need updating anyway.

With all that said, mixins can be very useful. We might, for example, want to apply *clearfix* rules across different elements and only within certain breakpoints. This is something that vanilla CSS can't do.

As such, mixins are not *bad*, we should use them, but use them judiciously.

## What about performance?

We overcomplicate matters when it comes to performance. We get obsessed with the smallest details.

Even if CSS totals more than 100kb, in the grand schemes of things, there's probably very little gain from mindlessly striving for DRYness. And as we've discussed making CSS small makes HTML big.

The compression of a single image gives us a better return on our investment. And as we've discussed, resolving other forms of redundancy improves maintainability *and* performance.

## Is this violating DRY principles?

Attempting to reuse, for example `float: left`, is akin to trying to reuse variable names in different Javascript objects. It's simply not in violation of DRY.

## Final thought

Striving for DRY leads to over-thought and over-engineered code. In doing so we make maintenance harder, not easier. Instead of obsessing over styles, we should focus on reusing tangible modules. Something we'll discuss in upcoming chapters.