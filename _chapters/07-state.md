---
layout: chapter
title: State
section: Core
permalink: /chapters/state/
description: Learn how to provide different styles to your modules and components based on state, such as showing, hiding and loading.
---

You might need to style elements differently based on state. This is particularly the case with richer User Interfaces. States might include:

- showing/hiding
- active/inactive
- disabled/enabled
- loading/loaded

To style elements differently based on state, we need to use an additional class name. These states should be encapsulated to the module or component at hand.

## Encapsulating state

Let's say a module is called *myModule*. You could apply an `isActive` class as follows:

	<div class="myModule isActive">

But it is likely that `isActive` is going to be used in many different modules, and what it means to be active is different depending on the module, so this breaks the fundamental rules of *MaintainableCSS* i.e. it's not encapsulated to the module in question.

For this reason, state must be prefixed with the module (or component) it pertains to...

## Applying state to a module

So let's say our module is called *myModule*.

	.myModule {}

Here are some states we might need to apply to `myModule`.

	.myModule-isDisabled {}
	.myModule-isActive {}
	.myModule-hasProducts {}
	.myModule-isHidden {}
	.myModule-isLoading {}

And the HTML needs to be as follows:

	<div class="myModule myModule-isDisabled">
	    <p class="myModule-title">

## Applying state to a component

If you wanted to apply state to just the *title* component, then you would apply `myModule-title-isDisabled` to the title component as follows:

	<div class="myModule">
       <p class="myModule-title myModule-title-isDisabled">
