---
layout: chapter
title: State
section: Core
permalink: /chapters/state/
---

Often, particularly with richer user interfaces, we need to style modules or components to look different based on state. States such as *showing*, *hiding*, *active*, *inactive*, *disabled*, *loading*, *loaded* etc. To do this we must communicate this with an additional class name.

## Encapsulating state

Let's say a module is called *myModule*. You could apply an `isActive` class as follows:

	<div class="myModule isActive"></div>

But it is likely a state such as `isActive` is going to be used on many different modules, and what it means to be active likely manifests itself different depending on the module.

For this reason this class actually breaks a fundamental rule of *MaintainableCSS* because we likely will inherit styles that weren't intended that way. So it's imperative that state is prefixed with the module name, just like components are...

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
		<p class="myModule-title">The title</p>
	</div>

## Applying state to a component

If you wanted to apply state to to just the *title* component, then you would apply `myModule-title-isDisabled` to the title component as follows:

	<div class="myModule">
		<p class="myModule-title myModule-isDisabled">The title</p>
	</div>