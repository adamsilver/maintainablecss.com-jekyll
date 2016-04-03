---
layout: chapter
title: State
section: Core
permalink: /chapters/state/
---

**What do I mean by state?** Is the module *showing* or *hiding*. Is it *active* or *inactive*, is it in a *loading* state or not? Each of these potentially mean that the UI *looks* different.

We want to communicate this via a css class.

## Ensuring state is encapsulated to the module

Let's say the module is called *myModule*.

You could apply an `isActive` state to the module as follows:

	<div class="myModule isActive"></div>

But it is likely a state such as `isActive` is going to be used on many different modules, and what it means to be active might very well be different across modules.

Therefor this breaks the main rule of *MaintainableCSS* by inheriting overzealous styles that weren't intended that way.

So I suggest that state is prefixed with the module name...

## How to do it?

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
		<p class="myModule-title">The title</p>
		<p class="myModule-somethingElse">Something else</p>
	</div>

Note: the module container has both classes.

If you wanted to apply state to to just the title then you would apply `myModule-title-isDisabled` to the title component as follows:

	<div class="myModule">
		<p class="myModule-title myModule-isDisabled">The title</p>
		<p class="myModule-somethingElse">Something else</p>
	</div>