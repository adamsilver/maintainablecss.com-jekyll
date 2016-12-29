---
layout: chapter
title: State
section: Core
permalink: /chapters/state/
description: Learn how to provide different styles to your modules and components based on state, such as showing, hiding and loading.
---

You might need to style elements differently based on state. Here some examples of state that could affect the styling of an element:

- showing or hiding
- active or inactive
- disabled or enabled
- loading or loaded
- hasProducts or hasNoProducts
- isEmpty or isFull

To style elements differently based on their state, we need to use an additional class name. These states should be applied to the module or component.

Imagine we have a module called *thing*. We might give this element a class of `isDisabled` as follows:

	<div class="thing isDisabled">

But we shouldn't do this because different elements will look different when disabled. For example:

* a disabled link may have a dark background colour; and
* a disabled basket may have a greyed-out overlay.

Instead, we should prefix the module (or component) to the state class.

## Applying state to a module

In this case the HTML will be:

	<div class="thing thing-isDisabled">

## Applying state to a component

If your components need state then you would prefix the component:

	<p class="thing-blah thing-blah-isDisabled">
