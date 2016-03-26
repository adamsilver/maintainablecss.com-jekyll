---
layout: chapter
title: State
permalink: /chapters/7/
---

**What do I mean by state?** Is the module *showing* or *hiding*. Is it *active* or *inactive*, is it in a *loading* state or not? Each of these potentially mean that the UI *looks* different.

We want to communicate this via a css class.

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

That's state sorted.
